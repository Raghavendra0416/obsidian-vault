Use Chrome Developer Tools to
1. Understand network requests made when a webpage is loaded
2. Inspect and modify HTML content
3. View and edit CSS styles applied to a webpage easily
4. Debug some layout issues efficiently


### What is Stashing?
**Stashing** is like a **"Pause Button"** for your work.

Imagine you are in the middle of working on a messy, half-finished file. Suddenly, your boss asks you to fix a critical bug _right now_ on a different branch.

- You can't **commit** because your code is broken and unfinished.1
- You can't **switch branches** because Git won't let you leave without cleaning up your mess first.

The Solution: You Stash your changes.

Git takes all your uncommitted work, saves it in a temporary storage area (a "stash"), and cleans your working directory so it looks like you never touched it.3 Later, you can "pop" the stash to bring your work back exactly how you left it.4

### The Analogy: The "Draft" Drawer
Let's go back to our **Package** analogy:

- **Unstaged:** You are writing a letter.
- **Committed:** You mailed the letter. It's gone and recorded in history.
- **Stashed:** You are halfway through writing the letter, but the doorbell rings. You don't want to mail it yet (it's not done), but you need your desk clean. So, you **shove the letter in a desk drawer**.
    - Your desk is now clean.
    - You can deal with the doorbell.
    - Later, you open the drawer and put the letter back on the desk to finish it.

### Stash vs. Commit: The Differences

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



