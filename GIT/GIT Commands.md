All Git related commands start with the `git` keyword.

| Commands                                                            | Description                                                                                                                                                                                                                                                                                               |
| ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| git config --global user.name "Raghavendra0416"                     | To Set name                                                                                                                                                                                                                                                                                               |
| git add File/Folder name                                            | Will add file name to staged                                                                                                                                                                                                                                                                              |
| git commit -m "Message-changes made"                                | This will commit file or folder to the local. <br>-m: means message we need to add - that what changes we made.                                                                                                                                                                                           |
| git status                                                          | Will gets you the current _status_ of the Git repository.                                                                                                                                                                                                                                                 |
| git clone                                                           | Will clone all the repositories from the link                                                                                                                                                                                                                                                             |
| git remote -v                                                       | It tells current working origin<br>It lists the names (aliases) and full URLs of all remote repositories connected to your current project.<br>- remote: Tells Git we are talking about connections to outside servers.<br>- -v: Short for **Verbose**. Says "Show me the full URLs, not just the names." |
| git branch crazy-experiment {git link where it needs to be created} | Creates branch crazy-experiment                                                                                                                                                                                                                                                                           |
| git restore --staged < filename >                                   | Will restore the staged file. <br>if . is used instead of filename, all the staged files will be restored.                                                                                                                                                                                                |

---

All Commands need for branching:

| Commands                       | Description                                                                                            |
| ------------------------------ | ------------------------------------------------------------------------------------------------------ |
| git branch                     | checks which branch you are currently standing on.<br>See all branches                                 |
| git branch branch_name         | Creates a new branch                                                                                   |
| git checkout branch_name       | Switch the branch                                                                                      |
| git checkout -b branch_name    | Creates a new branch and Switch the branch<br>-instead of the above 2 commands we can use this command |
| git push -u origin branch_name | Push new branch to the remote                                                                          |
| git merge Branch_name          | To merge different branches                                                                            |
| git branch -D Branch_name      | Will delete branch from local                                                                          |
| git push origin -d Branch_name | Will delete branch from github                                                                         |

---
#### While Merge Conflict:

| **Scenario**                         | **Action**                                                            |
| ------------------------------------ | --------------------------------------------------------------------- |
| **Their code fixes a bug**           | **Accept Incoming.** (Abandon your old logic if theirs is better).    |
| **You are adding a new feature**     | **Accept Current.** (But check if their changes affect your feature). |
| **You both added items to a list**   | **Accept Both.** (Then fix the formatting manually).                  |
| **You touched the exact same logic** | **STOP.** Do not guess. Proceed to Step 3.                            |
The "Golden Rule": Communication
If you see a change from a teammate and you don't understand _why_ they made it (e.g., they deleted a function you were using), **do not simply overwrite it.**
- **The wrong way:** "I'll just accept my changes because my code works." (This breaks the build).
- **The right way:** Send a quick message: _"Hey, I see we have a conflict in `utils.js`. You deleted the login function, but I was optimizing it. Should we keep the deletion or my optimization?"_

---

#### Unix Commands used in GIT:

| Commands | Description                        |
| -------- | ---------------------------------- |
| cd       | Change Directory                   |
| mkdir    | Make directory                     |
| ls -a    | Shows hidden files                 |
| Cat      | to show what is the file           |
| touch    | to create a file                   |
| nano     | to edit or update the file content |

---
#### Viewing Detailed Changes:

Use `q` to quit from the Pager. The Pager will be opened when git log is used.

|**Command**|**What it shows**|
|---|---|
|`git log -p`|Shows the full "patch" (diff) of every commit in the history.|
|`git log --stat`|Shows which files were changed and how many lines were added/deleted.|
|`git log -n 3`|Limits the output to only the last 3 commits (replace `3` with any number).|
|`git show <hash>`|Shows the full details and code changes for one specific commit.|

---
#### Other Commands:

| Commands                                         | Description/Where to use                                                                                                                                                                                                            |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| git pull origin main --allow-unrelated-histories | Git refuses to merge two repositories that do not share a **common ancestor**(History or files). By using this command we tell -><br>I know these two repositories don't have a shared past, but I want you to combine them anyway. |

