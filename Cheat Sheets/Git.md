# Git

## Git HEAD Detached

```bash
git fetch --all
git checkout -b temp dev
git reset --hard origin/dev
git checkout dev
git rebase master
git push origin dev --force
git status
git branch
```

To avoid this issue recurring in the future, consider implementing these best practices:

### 1. Use Git Pull Instead of Fetch + Merge

Always use `git pull` instead of manually fetching and merging:

```bash
git pull origin dev
```

This helps maintain a consistent state between your local and remote branches.

### 2. Avoid Detached Heads

Be careful when checking out specific commits:

```bash
git checkout dev
```

Instead of:

```bash
git checkout 563db05
```

### 3. Regular Synchronization

Set up automatic synchronization:

```bash
git config --global pull.rebase false
git config --global pull.rebase true
```

This will make `git pull` automatically rebase your local changes on top of the remote changes.

### 4. Use Upstream Branches

If possible, set upstream branches for your local branches:

```bash
git branch --set-upstream-to=origin/dev dev
```

This helps Git keep track of the remote branch more accurately.

### 5. Commit Frequently

Make small, frequent commits rather than large, infrequent ones. This makes it easier to manage and revert changes if needed.

### 6. Use Feature Branches

Work on features in separate branches and merge them back to `dev` regularly:

```bash
git checkout -b feature/new-feature
# Work on feature
git checkout dev
git merge feature/new-feature
git branch -d feature/new-feature
```

### 7. Keep Master Updated

Regularly update your `master` branch:

```bash
git checkout master
git pull origin master
git checkout dev
```

### 8. Use Git GUI Tools

Consider using Git GUI tools like GitKraken or SourceTree, which often handle these issues automatically.

### 9. Educate Team Members

Ensure all team members understand these best practices to maintain consistency across the project.

By implementing these practices, you can significantly reduce the likelihood of encountering detached heads and synchronization issues in the future. Remember, consistency is key in maintaining a healthy Git workflow.

## Git Reset

Git reset is a command that is used to undo changes in your working directory, staging area, and commit history. It allows you to reset your repository to a previous state, removing or reverting changes that you no longer need.

With each reset command, you can specify the commit you want to reset to using the `HEAD~n` syntax, where `n` is the number of commits you want to go back.

### Soft Reset

The `--soft` option resets the commit history to a previous state but keeps your changes in the staging area. This means you can recommit the changes if needed.

```bash
git reset --soft HEAD~1
```

### Mixed Reset

The `--mixed` option resets the commit history to a previous state and moves your changes to the working directory. This means you need to add the changes to the staging area again before committing.

```bash
git reset --mixed HEAD~1
```

### Hard Reset

The `--hard` option resets the commit history to a previous state and discards all changes in your working directory and staging area. This is useful when you want to completely remove the changes.

```bash
git reset --hard HEAD~1
```
