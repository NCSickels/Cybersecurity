See how [a minor change](#examples) to your commit message style can make a difference. 

> [!TIP]
> Have a look at **[git-conventional-commits](https://github.com/qoomon/git-conventional-commits)** , a CLI util to ensure these conventions, determine version and generate changelogs

## Commit Message Formats

### Default

```markdown
<type>(<optional scope>): <description>
empty separator line
<optional body>
empty separator line
<optional footer>
```

### Merge Commit
```
Merge branch '<branch name>'
```
Follows default git merge message

### Revert Commit

```
Revert "<reverted commit subject line>"
```

<sup>Follows default git revert message</sup>

### Initial Commit

```
chore: init
```

### Types

- API relevant changes
- `feat` Commits, that adds or remove a new feature
- `fix` Commits, that fixes a bug
- `refactor` Commits, that rewrite/restructure your code, however does not change any API behaviour
- `perf` Commits are special `refactor` commits, that improve performance
- `style` Commits, that do not affect the meaning (white-space, formatting, missing semi-colons, etc)
- `test` Commits, that add missing tests or correcting existing tests
- `docs` Commits, that affect documentation only
- `build` Commits, that affect build components like build tool, ci pipeline, dependencies, project version, ...
- `ops` Commits, that affect operational components like infrastructure, deployment, backup, recovery, ...
- `chore` Miscellaneous commits e.g. modifying `.gitignore`

### Scopes

The `scope` provides additional contextual information.

- Is an **optional** part of the format
- Allowed Scopes depends on the specific project
- Don't use issue identifiers as scopes

### Breaking Changes Indicator

Breaking changes should be indicated by an `!` before the `:` in the subject line e.g. `feat(api)!: remove status endpoint`

- Is an **optional** part of the format

### Description

The `description` contains a concise description of the change.

- Is a **mandatory** part of the format
- Use the imperative, present tense: "change" not "changed" nor "changes"
- Think of `This commit will...` or `This commit should...`
- Don't capitalize the first letter
- No dot (`.`) at the end

### Body

The `body` should include the motivation for the change and contrast this with previous behavior.

- Is an **optional** part of the format
- Use the imperative, present tense: "change" not "changed" nor "changes"
- This is the place to mention issue identifiers and their relations

### Footer

The `footer` should contain any information about **Breaking Changes** and is also the place to **reference Issues** that this commit refers to.

- Is an **optional** part of the format
- **optionally** reference an issue by its id.
- **Breaking Changes** should start with the word `BREAKING CHANGES:` followed by space or two newlines. The rest of the commit message is then used for this.

### Examples
`feat: add email notifications on new direct messages`

 `feat(shopping cart): add the amazing button`

 ```
 feat: remove ticket list endpoint
 refers to JIRA-1337
 BREAKING CHANGES: ticket endpoints no longer supports list all entities.
```

`fix(shopping-cart): prevent order an empty shopping cart`

`fix(api): fix wrong calculation of request body checksum`

```
fix: add missing parameter to service call
The error occurred because of <reason>.
```

`perf: decrease memory footprint for determine unique visitors by using HyperLogLog`

`build: update dependencies`

`build(release: bump version to 1.0.0`

`refactor: implement fibonacci number calculation as recursion`

`style: remove empty line`

