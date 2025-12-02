### Basic Questions:

1. How to setup git? and how to add data to staged? how to commit? how to push the data? how to ignore few files/folders while committing? 
2. What is the difference between files, commit, branches, staged in GIT? 
---
### 1. How to setup git? and how to add data to staged? how to commit? how to push the data? how to ignore few files/folders while committing?  

##### 1️⃣ One-time Git setup (global)

|Command|Description|
|---|---|
|`git config --global user.name "Raghavendra0416"`|Sets your **global Git username** (used as the author name in all your repos on this machine).|
|`git config --global user.email "raghavendra.workin@gmail.com"`|Sets your **global Git email** (used in commits and for GitHub identity).|
|`git config --global init.defaultBranch main`|Makes new repos use `main` as the default branch name instead of `master`.|
|`git config --list`|Shows all Git configuration values (global + local).|
|`git config core.autocrlf false` (optional)|Turns off automatic LF/CRLF line-ending conversion for the current repo (you didn’t run this, but we discussed it as an option to remove those LF/CRLF warnings).|

##### 2️⃣ Repo setup for your Obsidian vault (final clean version)

These are the commands that resulted in the final, correct setup (notes tracked, `.obsidian` ignored, pushed to GitHub).

|Command|Description|
|---|---|
|`cd "D:\Notes\Obsidian\Obisidein notes"`|Moves into your Obsidian vault folder (your Git repo root).|
|`notepad .gitignore`|Opens/creates `.gitignore` in Notepad so you can add patterns to ignore (you added `.obsidian/`).|
|_(edit in Notepad)_ `.obsidian/`|Tells Git to **ignore the entire `.obsidian` folder** (plugins, config, etc.).|
|`rmdir /S /Q .git`|Deletes the existing `.git` folder → **removes old Git history**, but keeps all your files. Used so the secret inside `.obsidian` is completely removed from history.|
|`git init`|Initializes a **new empty Git repo** in the current folder.|
|`git add .`|Stages **all files** (except those ignored by `.gitignore`, like `.obsidian/`) for commit.|
|`git commit -m "Initial commit - notes without Obsidian config"`|Creates your **first commit** with all the staged files and that message.|
|`git ls-files \| findstr ".obsidian"`|Lists tracked files and filters for `.obsidian`; seeing **no output** confirmed `.obsidian` is not tracked.|
|`git remote add origin https://github.com/Raghavendra0416/obsidian-vault.git`|Connects your local repo to the **remote GitHub repo** named `origin`.|
|`git push -u origin main --force`|Pushes your local `main` branch to GitHub, **overwriting** the existing `main` there. Also sets `origin/main` as the upstream so future `git push` works without extra args.|

##### 3️⃣ Commands you used earlier / general useful ones

These were used at different points while learning what’s happening:

|Command|Description|
|---|---|
|`git status`|Shows current repo state: branch, staged files, unstaged changes, untracked files.|
|`git add .`|(Repeated many times) Stages all current changes for the next commit.|
|`git commit`|Starts a commit using the default editor (Vim) to type the message. If you exit with an empty message → **“Aborting commit due to empty commit message.”**|
|`git commit -m "Some message"`|Creates a commit **without opening an editor**. Very handy.|
|`git push -u origin main`|Pushes `main` to `origin` and sets upstream (was rejected first because remote already had commits).|
|`git push -u origin main --force`|Force-pushes your `main` branch, replacing the remote history with your local one. Useful when you know your local branch is the source of truth.|
|`git ls-files`|Lists all files currently tracked by Git.|
|`git log`|Shows commit history for the current branch.|
|`notepad ".obsidian\plugins\tasknotes\main.js"`|Opened the plugin file to inspect where GitHub found secrets.|

##### 4️⃣ Daily workflow cheat sheet for you now ✅

For **future changes** in your notes, your normal flow is just:

|Command|Description|
|---|---|
|`cd "D:\Notes\Obsidian\Obisidein notes"`|Go to your repo.|
|`git status`|See what changed since last commit.|
|`git add .`|Stage all modified/created files.|
|`git commit -m "Update notes for <date/topic>"`|Save a snapshot with a meaningful message.|
|`git push`|Upload the new commits to GitHub (`origin/main`).|


---
### 2. What is the difference between files, commit, branches, staged in GIT? 
Answer:

Think of Git as a photography process for your code. Here is the short breakdown of the differences:
1. Files (Working Directory):
    This is your current workspace. These are the actual files on your computer that you are currently editing or creating. Git doesn't "own" these yet until you tell it to.
    - _Status:_ Untracked or Modified.

2. Staged (The Index):
    This is the preparation zone. You "stage" specific files (using git add) to tell Git, "I want to include these specific changes in my next save." It is like picking which items to put in a box before taping it shut.
    - _Status:_ Ready to be committed.

3. Commit:
    This is the permanent snapshot. When you commit (using git commit), you are taking a picture of everything currently in the "Staged" area and saving it to the history with a message. It is a save point you can always go back to.
    - _Status:_ Saved/Recorded.

4. Branches:
    These are parallel timelines. A branch is just a movable pointer to a specific commit. It allows you to work on a new feature (Feature Branch) without messing up the main code (Main Branch).
    - _Status:_ Independent line of development.

##### The Workflow in 3 Steps:
1. You **Edit** **Files** (Working Directory).8
2. You **Stage** the files you want to keep (`git add`).9
3. You **Commit** the staged files to save them to the current **Branch** (`git commit`).10

##### Quick Analogy: Shopping
- **Files:** The items on the store shelves (everything available).
- **Staged:** The items you put in your **shopping cart** (what you intend to buy).
- **Commit:** The **receipt** after you pay (permanent proof of purchase).
- **Branch:** A separate **shopping trip** for a different dinner party.


---
---
### Another Set of Questions:

1. When would you need multiple remotes?
2. Is there any difference between using the `https` link and the `SSH` link to clone a repository?
3. What if you need to use a different name for the download folder rather than the name of the repository with `git clone`?
4. Where does the `git remote` command get the mapping of remote name & the corresponding links?

---
### 1. When would you need multiple remotes?
Answer:
You typically need more than one remote (usually in addition to `origin`) in two main scenarios:

- **The Forking Workflow (Open Source):**
    - **`origin`**: Points to **your** copy (fork) of the project where you have permission to push code.
    - **`upstream`**: Points to the **original author's** repository. You use this to pull their latest updates so your local code doesn't get outdated.
- **Deployment:**
    - You might have a remote named **`heroku`** or **`production`**. When you are ready to release your app, you run `git push production master` to send your code directly to the live server.

---
### 2. Is there a difference between HTTPS and SSH links?
Answer:
Yes, the difference lies in **how you prove who you are (authentication)**.

|**Feature**|**HTTPS Link**|**SSH Link**|
|---|---|---|
|**Authentication**|Username & Password (or Personal Access Token).|SSH Keys (a file on your computer matches a file on the server).|
|**Convenience**|Easy to start, but may ask for a password often (unless you use a credential helper).|Harder to set up initially, but you never have to type a password again.|
|**Firewalls**|Works on almost all networks.|sometimes blocked by strict corporate firewalls.|

> **Recommendation:** If you are a beginner, start with **HTTPS**. If you push code daily, switch to **SSH** to save time.

---
### 3. How do you rename the download folder when cloning?

By default, `git clone` creates a folder with the same name as the repository. To choose your own name, simply add it to the end of the command:

```Bash
git clone <repository-url> <my-custom-folder-name>
```

Example:
git clone https://github.com/jquery/jquery.git my-website-scripts
(This downloads the code into a folder named my-website-scripts instead of jquery)

---
### 4. Where does `git remote` get the mapping of names & links?
Answer:
Git stores this information in a plain text configuration file hidden inside your project folder.

- **File Location:** `.git/config`
- **How to see it:** You can open this file in any text editor (like Notepad or VS Code) to see the raw mapping.

It looks like this:
```Ini, TOML
[remote "origin"]
    url = https://github.com/user/repo.git
    fetch = +refs/heads/*:refs/remotes/origin/*
```

---
---

### Another Set of Questions:
1. What is Stashing Changes? how is it different from commit?


---
### 1. What is Stashing Changes? how is it different from commit?
Answer:
##### What is Stashing?

**Stashing** is like a **"Pause Button"** for your work.
Imagine you are in the middle of working on a messy, half-finished file. Suddenly, your boss asks you to fix a critical bug _right now_ on a different branch.

- You can't **commit** because your code is broken and unfinished.
- You can't **switch branches** because Git won't let you leave without cleaning up your mess first.

The Solution: You Stash your changes.
Git takes all your uncommitted work, saves it in a temporary storage area (a "stash"), and cleans your working directory so it looks like you never touched it.3 Later, you can "pop" the stash to bring your work back exactly how you left it.4

##### The Analogy: The "Draft" Drawer

Let's go back to our **Package** analogy:

- **Unstaged:** You are writing a letter.
- **Committed:** You mailed the letter. It's gone and recorded in history.
- **Stashed:** You are halfway through writing the letter, but the doorbell rings. You don't want to mail it yet (it's not done), but you need your desk clean. So, you **shove the letter in a desk drawer**.
    - Your desk is now clean.
    - You can deal with the doorbell.
    - Later, you open the drawer and put the letter back on the desk to finish it.

##### Stash vs. Commit: The Differences

|**Feature**|**Commit**|**Stash**|
|---|---|---|
|**Purpose**|To permanently save a completed unit of work.|To temporarily set aside unfinished work.|
|**Visibility**|Visible in the project history (log).|Invisible in the history (only stored locally).|
|**Sharing**|Can be pushed to GitHub for others to see.|Stays on your computer only.|
|**Analogy**|Mailing the package.|Putting the package on a shelf for later.|

### How to use it (The 2 Commands you need)

1. **To save your work away:**
 ```Bash
    git stash
    ```
    _(Your folder will now look clean, and you can safely switch branches.)_
    
2. **To bring your work back:**
  ```Bash
    git stash pop
    ```
    _(Git takes the changes out of the stash and puts them back into your files.)_

---
