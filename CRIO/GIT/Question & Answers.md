Basic Questions:
1. What is the difference between files, commit, branches, staged in GIT? 


---

### 1. What is the difference between files, commit, branches, staged in GIT? 
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

