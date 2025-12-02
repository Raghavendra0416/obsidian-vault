### Important Points:
- All Git related commands start with the `git` keyword.
- All the folders are called as repositories in the GIT.
- [History of GIT](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git)
- [Branches in GIT](https://www.atlassian.com/git/tutorials/using-branches)
- A branch represents an independent line of development. Branches serve as an abstraction for the edit/stage/commit process. You can think of them as a way to request a brand new working directory, staging area, and project history.
-  It's important to understand that branches are just pointers to commits. When you create a branch, all Git needs to do is create a new pointer, it doesn’t change the repository in any other way.

**Un-staged, Staged, Committed, Untracked:**
- **Un-staged:** (Working Directory): You are still gathering items and putting them in the box. Git sees that the file has changed, but it hasn't been "marked" to be saved yet. **Command to move to next step:** `git add <filename>`
- **Staged:** (Staging Area / Index): You have sealed the box and put a label on it. It is ready to go, but hasn't left your house yet. The file is sitting in the "waiting room," ready to be committed. **Command to move to next step:** `git commit -m "message"`.
- **Committed:** (Local Repository): You have handed the box to the mail carrier. It is now officially "shipped" and recorded in history. The file is safely stored. Your "Unstaged" and "Staged" areas are now clean (empty) until you make new changes.
- **Untracked:** There is a 4th state you will see often: **Untracked**. This happens when you create a **brand new file**. Git sees the file exists, but it isn't tracking it yet. You have to `git add` it once to tell Git, "Hey, please watch this file from now on."

Image of GIT:
![[Pasted image 20251121081858.png]]

![[Pasted image 20251121145932.png]]

---
### How to initialize GIT? Add to staged? commit? create branch? name the branch? and push the file?
git init
git add .
git commit -m "Initial commit - my new project"
git branch -M main
git remote add origin https://github.com/Raghavendra0416/my-new-project.git
git remote -v
git push -u origin main

Answer:

> “After commit, we rename the branch to `main`, then we add a remote called `origin`, then we push the branch to GitHub.”

You said:
```bash
git branch -M main
git remote add origin https://github.com/Raghavendra0416/my-new-project.git
git push -u origin main
```

Each step really means:
##### 1️⃣ `git branch -M main`

- This **renames** your current branch to `main`.
- Usually, when you do `git init`, Git creates a branch called `master` by default (unless configured otherwise).
- `-M` means:
    > “Move/rename this branch to `main`, even if `main` already exists.”

So after this:
- You’re on branch: `main`.
You are **not** creating a new branch from scratch here; you are renaming the existing one.

##### 2️⃣ `git remote add origin https://github.com/.../my-new-project.git`

- This tells Git:
    > “There is a remote repository called `origin`, and its URL is this GitHub repo.”
- `origin` is just a **nickname** for that URL.

After this command:
- You now have a link:  
    **local repo ⇄ `origin` (GitHub repo)**
You do this once per project (unless you change the remote later).

##### git remote -v:
Tells  current working origin.
##### 3️⃣ `git push -u origin main`

- This pushes your **local `main` branch** → to the remote `origin`, branch `main`.
- `-u` (or `--set-upstream`) means:
    > “Remember that my local `main` is connected to `origin/main`.”

After this:
- Future pushes are simpler: you can just run:
```bash
    git push
    ```
    and Git knows you mean `origin main`.

##### Full flow in order (for a new project)
For a fresh project, it’s typically:
```bash
# 1. Go to project folder, or create it
cd D:\Projects\my-new-project

# 2. Initialize repo
git init

# 3. Stage & commit files
git add .
git commit -m "Initial commit - my new project"

# 4. Rename branch to main
git branch -M main

# 5. Connect to GitHub repo
git remote add origin https://github.com/Raghavendra0416/my-new-project.git

# 6. Push to GitHub
git push -u origin main
```


---
### Keywords:

##### The "Core" Concepts (Your List)

|**Keyword**|**What it means**|**Simple Analogy**|
|---|---|---|
|**Unstaged**|Modified files that Git sees but hasn't been told to save yet.|You’ve written a letter but haven't put it in the envelope.|
|**Staged**|Files you have selected ("added") to be included in the next save point.|You put the letter in the envelope and sealed it.|
|**Commit**|A permanent snapshot of your staged changes. It saves your work to history.|You dropped the envelope in the mailbox. It's sent!|
|**Branch**|A parallel version of your code. It lets you work on a new feature without breaking the main code.|Like a multiverse timeline. You can go to "Timeline B" to mess things up, while "Timeline A" stays safe.|
|**Merging**|Taking changes from one branch and combining them into another.|Timeline B was a success! You merge it back so "Timeline A" now has those cool changes too.|
|**Merge Conflict**|When Git doesn't know how to combine changes (e.g., two people changed the same line of code differently).|Two people trying to write on the same line of the same page at the same time. Git pauses and asks you, "Which one do you want to keep?"|

### The "Connection" Keywords (Working with others)

Once you start working with GitHub or GitLab, you will need these:
- **Repository (Repo):** The project folder. It contains all your files and the secret `.git` folder that tracks history.
- **Remote:** The version of your repository that lives on the internet (like on GitHub). It is usually called `origin` by default.
- **Clone:** Downloading a repository from the internet to your computer for the first time.
- **Push:** Sending your local commits _up_ to the remote repository. (Uploading).
- **Pull:** Bringing changes _down_ from the remote repository to your computer. (Downloading + Merging).

##### The "Navigation" Keywords (Moving around)

- **Checkout:** The command used to switch between branches or go back to an old commit. Think of it as "teleporting" to a different state of your project.
- **HEAD:** A special pointer that says, _"You are here."_ It usually points to the latest commit on the branch you are currently looking at.
- **Status:** The command `git status`. It is your best friend. It tells you exactly what state your files are in (staged, unstaged, or untracked).



---
### Set up GIT and Push Data to GIT Hub

After Installing git we need to set up the git in laptop for it we need to provide:
- **User name**
- **Email**
- **Default branch**
- Git LFS is installed (optional)
- Credential manager is active (for saving your GitHub/Azure login)

We have to use the below commands in order:

| Steps | Command                                                       | Description                       |
| ----- | ------------------------------------------------------------- | --------------------------------- |
| 1.    | git config --global user.name "Raghavendra0416"               | Set User Name                     |
| 2.    | git config --global user.email "raghavendra.workin@gmail.com" | Set Mail                          |
| 3.    | git config --global init.defaultBranch main                   | Set default branch as "main name" |
| 4.    | git config --list                                             | To check if every thing is set    |
Now We are ready to use GIT.
Now the Main Branch is created. 

Steps:
1. Now you need to create folder/directories in the local. and Open that specific directory where you want to add git
2. Initialize a new Git repository in your project/ Clone the code if already in the git.

| Steps | Command                               | Description                                                        |
| ----- | ------------------------------------- | ------------------------------------------------------------------ |
| 1.    | mkdir name                            | We can create directory using this command.                        |
| 2.    | cd directory path                     | Change the path of the directory, that needs git.                  |
|       | git clone < repo-url>                 | Clone an existing repository - if already present                  |
|       | **Working with Changes**              |                                                                    |
| 3.    | git init                              | Initialize a new Git repository in your project.                   |
| 4.    | git add . or file name or folder name | Stage a specific file for commit.<br>. -> means current directory. |
| 5.    | git commit -m "Commit message"        | Commit changes with a message                                      |
| 6.    | git status                            | To check the status of the commit                                  |
| 7.    | git push                              | To push the committed changes to the git hub.                      |
| 8.    | git log                               | To view commit history                                             |
