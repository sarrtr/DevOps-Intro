# Lab 1 submission

## Task 1

1. **Benefits of signing commits:**
Commit signing adds a cryptographic signature to my Git commits which confirms that the commit was made by me and it prevents others from committing under my name. It also confirms that commit hasn't been altered: change to the commit after signing breaks the signature. Besides, commit signing mitigates MITM attacks.

2. **"Why is commit signing important in DevOps workflows?"**
- commit signing provides verifiable history for compliance reviews.
- team members can verify each other's work.
- reviewers know commits are authentic and by whom exactly they were made.

3. **Successful SSH key setup and signed commit:**

![ssh key creation](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab1/labs/assets/screenshots/lab1.2.png?raw=true)

![ssh key setup](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab1/labs/assets/screenshots/lab1.1.png?raw=true)

4. **"Verified" badge on GitHub commit:**

![verified commit](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab1/labs/assets/screenshots/lab1.3.png?raw=true)

## Task 2

1. **PR template on main branch and description auto-filling**:

![.github/pull_request_template.md exists]()

![auto-filling]()

2. **How do PR templates improve collaboration?**

PR templates improve collaboration by standardizing communication and saving time for routine pull request description filling. They ensure pull requests include key information like context, testing steps, and screenshots, making reviews faster and more consistent.

3. **Challenges encountered during setup:**

Initially I already was working on feature/lab1 branch and I was confused about the location of the template file, so my first pull request was without description auto-filling by template.