# Lab 1 submission
1. **Benefits of signing commits:**
Commit signing adds a cryptographic signature to my Git commits which confirms that the commit was made by me and it prevents others from committing under my name. It also confirms that commit hasn't been altered: change to the commit after signing breaks the signature. Besides, commit signing mitigates MITM attacks.

2. **"Why is commit signing important in DevOps workflows?"**
- commit signing provides verifiable history for compliance reviews.
- team members can verify each other's work.
- reviewers know commits are authentic and by whom exactly they were made.

3. **Successful SSH key setup and signed commit:**
```
PS C:\Users\kuzzm\OneDrive\Рабочий стол\devops_labs\devops-intro> git cat-file -p HEAD
tree 5a5eb835147f84075bcaad098de64e4e530d150a
parent 33ab6569eadf61f71096a6bb00baf21259c562cc
author sarrtr <kuzzminykh.polina@gmail.com> 1770224793 +0300
committer sarrtr <kuzzminykh.polina@gmail.com> 1770224793 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgRVkHzgYBoD/mzPMfSg5u1fqbAJ
 8tSOo9OJ2Mf7E/AsoAAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
 AAAAQBgkm/SmnxUCeFxSQ48NU3Szsdt7Bg/ZWuAlAqkurBGZSPeXqy+7oPcdl0gbsPdE3h
 nkr3uB5R+xlLMNs49R6QY=
 -----END SSH SIGNATURE-----

docs: add commit signing summary
```