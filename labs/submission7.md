# Lab 7 submission

## Task 1

Initial `desired-state.txt`:

```
version: 1.0
app: myapp
replicas: 3
```

`current-state.txt`:

```
version: 1.0
app: myapp
replicas: 3
```

![7.1](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab7/labs/assets/screenshots/lab7.1.png?raw=true)
![7.2](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab7/labs/assets/screenshots/lab7.2.png?raw=true)


**GitOps reconciliation loop. How does this prevent configuration drift?**

The reconciliation loop continuously compares the desired state (stored in Git, here simulated by desired-state.txt) with the actual cluster state (current-state.txt). If a difference (drift) is detected, the system automatically applies the desired configuration to restore the intended state. This prevents configuration drift by ensuring that any manual or accidental changes are quickly overwritten by the source of truth.

**What advantages does declarative configuration have over imperative commands in production?**

Applying the same declarative config multiple times yields the same result; imperative commands may cause side effects if run repeatedly. Git history provides a clear record of all changes, and also the same declarative config can be used for dev, staging, and production, reducing environment‑specific surprises.

## Task 2

` healthcheck.sh`:

```
DESIRED_MD5=$(md5sum desired-state.txt | awk '{print $1}')
CURRENT_MD5=$(md5sum current-state.txt | awk '{print $1}')

if [ "$DESIRED_MD5" != "$CURRENT_MD5" ]; then
    echo "$(date) - ❌ CRITICAL: State mismatch detected!" | tee -a health.log
    echo "  Desired MD5: $DESIRED_MD5" | tee -a health.log
    echo "  Current MD5: $CURRENT_MD5" | tee -a health.log
else
    echo "$(date) - ✅ OK: States synchronized" | tee -a health.log
fi
```

`health.log`:

```
Wed Mar 18 14:58:06 RTZ 2026 - ✅ OK: States synchronized
Wed Mar 18 14:58:25 RTZ 2026 - ❌ CRITICAL: State mismatch detected!
  Desired MD5: a15a1a4f965ecd8f9e23a33a6b543155
  Current MD5: 48168ff3ab5ffc0214e81c7e2ee356f5
Wed Mar 18 14:58:42 RTZ 2026 - ✅ OK: States synchronized
Wed Mar 18 14:59:15 RTZ 2026 - ✅ OK: States synchronized
Wed Mar 18 14:59:18 RTZ 2026 - ✅ OK: States synchronized
Wed Mar 18 14:59:22 RTZ 2026 - ✅ OK: States synchronized
Wed Mar 18 14:59:25 RTZ 2026 - ✅ OK: States synchronized
```

![7.3](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab7/labs/assets/screenshots/lab7.3.png?raw=true)
![7.4](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab7/labs/assets/screenshots/lab7.4.png?raw=true)

**How do checksums (MD5) help detect configuration changes?**

MD5 produces a unique hash for a file’s content. By comparing the hash of desired-state.txt with that of current-state.txt, we can instantly detect if the files differ, even if the difference is subtle. This is more reliable and efficient than a full text comparison, especially for large configurations.

**How does this relate to GitOps tools like ArgoCD's "Sync Status"?**

ArgoCD continuously compares the live Kubernetes state with the Git manifests. It reports “Synced” if they match, “OutOfSync” if they differ. `healthcheck.sh` mimics this: “✅ OK” = Synced, “❌ CRITICAL” = OutOfSync. ArgoCD also provides detailed diffs and automated sync policies.
