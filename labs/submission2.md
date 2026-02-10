# Lab 2 submission

## Task 1

1. **Objects inspections:**
![2.1](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.1.png?raw=true)

- Commit inspection:

![2.2](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.2.png?raw=true)

- Tree inspection:

![2.4](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.4.png?raw=true)

- Blob inspection:

![2.3](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.3.png?raw=true)

Commit is a snapshot of the project's state at a specific point in time which contains a link to the tree, a link to the parent commit, author and message.

Tree is like a file system that contains a list of files (blobs) and subdirectories (other trees) in a format: *object type* *object's hash* *object's real name (file or directory)*.

Blob is an object that represents raw data of the file.

2. **How does Git store repository data?**

In Git files are stored based on their hashes, not real filenames. Blobs store content of files, trees store references to other trees and blobs, commits point to trees and contain metadata. 

## Task 2

1. `git reset --soft HEAD~1`: cancels last commit but saves its changes to staging area (test.txt: "Third commit"). Can be useful when we want to change commit message or add/remove something in last commit.

![2.5](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.5.png?raw=true)

2. `git reset --hard HEAD~1`: delete last commit and all its changes (test.txt: "First commit"). Can be dangerous because all changes are deleted permanently.

![2.6](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.6.png?raw=true)

3. `git reflog`: shows history of HEAD movements.

![2.7](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.7.png?raw=true)

4. `git reset --hard <reflog_hash>`: restores state to specified entry from reflog (test.txt: "Second commit"). Can be useful when we did `git reset --hard` and now want to recover lost commits. 

![2.8](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.8.png?raw=true)

## Task 3

![2.9](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.9.png?raw=true)

![2.10](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.10.png?raw=true)

The graph shows branch relationships and merge points making it easier to understand project history and what have been done.

## Task 4

![2.11](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.11.png?raw=true)

Git tags matter because they provide stable versioning (reference points for releases), generate accurate release documentation and trigger automated CI/CD workflows.

## Task 5

![2.12](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.12.png?raw=true)

- Use `git switch` only for branch operations (creating, moving between, deleting), it prevents accidental file modifications.

- Use `git checkout` only for restoring files or specific commits because it can overwrite uncommitted changes when switching branches.

![2.13](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.13.png?raw=true)

![2.14](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab2/labs/assets/screenshots/lab2.14.png?raw=true)

- Use `git restore` only for discarding or reverting file changes.

## Task 6

**GitHub Community:**

Starring repositories matters in open source because it signals appreciation to maintainers and helps them to gain public recognition in GitHub ans recommendations.

Following developers helps in networking (you see what other developers are working on and you can discover their projects) and collaboration (easier to find team members for future projects among familiar developers).