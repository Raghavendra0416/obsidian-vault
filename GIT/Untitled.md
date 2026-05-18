Situation:
When unnecessary folder & files are created in local, and git has our correct version, we can use the following commands to remove all the unnecessary files in local and have the same data github

```GIT
git fetch origin
git reset --hard origin/main
git clean -fd
```

