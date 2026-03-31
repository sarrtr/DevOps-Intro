# Lab 9 submission

## Task 1

1. **Number of Medium risk vulnerabilities found:** 2
2. **Description of the 2 most interesting vulnerabilities:**
    - *Content Security Policy (CSP) Header Not Set:* Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files.
    - *Cross-Domain Misconfiguration:* Web browser data loading may be possible, due to a Cross Origin Resource Sharing (CORS) misconfiguration on the web server.
3. **Security headers status (which are present/missing and why they matter):**
    - missing: Cross-Origin-Opener-Policy (Helps prevent cross-origin attacks like Spectre by isolating the browsing context)
    - set: Deprecated Feature Policy (Deprecated header that restricts browser features (camera, geolocation). Its presence shows some security awareness, but it should be updated to Permissions-Policy)
4. **Screenshot of ZAP HTML report overview:**
![9.1](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab9/labs/assets/screenshots/lab9.1.png?raw=true)
5. **Analysis: What type of vulnerabilities are most common in web applications?**
- Injection flaws (SQL, NoSQL, OS command) – still the most prevalent.
- Cross-Site Scripting (XSS) – frequently found, especially in apps that don’t properly sanitize user input.
- Security misconfiguration – missing security headers, default credentials, exposed debug endpoints.
- Broken Access Control – users accessing resources they shouldn’t (e.g., admin endpoints).
- Outdated components – using vulnerable libraries or frameworks.

## Task 2

1. **Total count of CRITICAL and HIGH vulnerabilities:**
    - high: 50
    - critical: 10
2. **List of 2 vulnerable packages with their CVE IDs:**
    - base64url (package.json) - NSWG-ECO-428 
    - braces (package.json) - CVE-2024-4068
3. **Most common vulnerability type found:** node-tar: tar: node-tar: Arbitrary file overwriten/creation/read/write
4. **Screenshot of Trivy terminal output showing critical findings**:
![9.2](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab9/labs/assets/screenshots/lab9.2.png?raw=true)
![9.3](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab9/labs/assets/screenshots/lab9.3.png?raw=true)
![9.4](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab9/labs/assets/screenshots/lab9.4.png?raw=true)
![9.5](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab9/labs/assets/screenshots/lab9.5.png?raw=true)
![9.6](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab9/labs/assets/screenshots/lab9.6.png?raw=true)
![9.7](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab9/labs/assets/screenshots/lab9.7.png?raw=true)
5. **Analysis: Why is container image scanning important before deploying to production?**
- Identifies known vulnerabilities in OS packages and application dependencies before they reach production.
- Prevents supply chain attacks – many images contain outdated libraries with known exploits.
- Reduces attack surface – scanning helps you choose minimal base images and remove unnecessary components.
- Ensures compliance with security policies and regulations (e.g., PCI-DSS, SOC2).
- Enables “shift left” security – finding issues early in the development lifecycle is cheaper and safer than fixing them after deployment.
6. **Reflection: How would you integrate these scans into a CI/CD pipeline?**
- Run Trivy as part of the build stage – after building the Docker image, automatically scan it.
- Set severity thresholds – fail the pipeline if CRITICAL or HIGH vulnerabilities are found (unless explicitly overridden).
- Generate and store reports – save the scan results as artifacts for auditing.
- Use the results to prioritize fixes – feed them into a vulnerability management system.
- Integrate with pull requests – add a GitHub Action (or GitLab CI job) that comments on PRs with a summary of new vulnerabilities.
- Schedule regular scans – even after deployment, re‑scan images in the registry to catch newly disclosed CVEs.