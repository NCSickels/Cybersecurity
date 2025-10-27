# Git 

## Git Repository Config

```bash
http.sslVerify=false
user.email=<EMAIL>
user.password=<PASSWORD_TOKEN>
user.name=<USERNAME>
credential.helper=store
```
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

## Mirror GitHub Repository to GitLab

1.  Clone the GitHub Repository Locally

```bash
git clone --mirror https://github.com/username/repository.git
```
- `--mirror` clones all refs (branches, tags) and the full history including commits, branches, and remotes.

2. Create a new repository on GitLab
3. Push to GitLab

```bash
cd repository.git
git push --mirror https://gitlab.com/username/repository.git
```

## Github Workflow
### Branching
When working on an issue, create a branch specific to that feature/bug. If two people are working on the same feature, they should each have a branch off of the feature branch. There should be a naming convention in place. The name of the branch should contain sufficient detail as to the purpose of that branch. For example, you may want to include the identity of the creator of the branch name so that colleagues know who the branch belongs to. You may want to have a segment that identifies the task being accomplished or the date started. An example of a naming convention would look like `feature_{TASK_ID}` or `{YOUR_INITIALS}_{TASK_NAME}`.

### Commit
The title of the commit can be anything you want. Including an integration in the title is only necessary if the pull request's title will not suffice. If you believe a series of commits can/should be combined into a single commit, you can use `rebase`, `merge --squash`, or `reset` methods. This is commonly referred to as [squashing](http://makandracards.com/makandra/527-squash-several-git-commits-into-a-single-commit).

### Pull Request
A pull request should sit on top of a merge so that any parties of interest can voice concerns or opinions relating to the syntax. This is not a format for discussion regarding the task being accomplished, but rather the methods used. Any integrated hooks should be placed in the title of the pull request. By doing so, a single permalink can be used to represent all of the commits required to accomplish a certain task.

### Code Review
Code review can be useful for a few reasons. 
- It allows someone with more experience to critique your approach and give feedback. 
- It allows someone with less experience to learn the code base. 
- It increases exposure to common elements and enhances your familiarity with the material.

### Merge
Merging can be accomplished using the command line or the Github interface. If using the latter, be aware that there will be an extra commit to represent the merging of the pull request.

## Best Practices
- A staging branch should be set as a repository's default branch. This way, when setting up a pull request, the staging branch is selected as the destination branch automatically, preventing accidental merges into the master branch.
- Merging into master should only occur when performing a release. For this reason, the process can be streamlined by automating deployments when the master branch is changed. This is enabled by a feature called webhooks. A few examples can be seen [here](https://www.nodejitsu.com/documentation/features/webhooks/), where changes to a branch trigger a sequence of deployment steps.