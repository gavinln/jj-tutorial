# JJ Tutorial

[Jujutsu][100] or JJ is a git compatible version control system.

[100]: https://github.com/jj-vcs/jj

## Setup environment

1. Create the lock file

```
nix flake lock
```

2. Start a shell with the environment

```
nix develop
```

## Basic commands

1. jj version

```
jj -V
```

2. Create a new project

```
jj git init
```

3. Status of repository

```
jj st
```

4. List config

```
jj config list
```

5. Add description to working copy commit

```
jj describe -m "hello world"
```

6. Start new changes

```
jj new
```

7. View log

```
jj log
```

## Squash Workflow

1. Add a change with description

```
jj describe -m "print goodbye as well as hello"
```

2. Create a new empty change

```
jj new
```

3. Make changes to the code and save it

4. Squash changes into previous change with description

```
jj squash
```

5. Use `jj log` in between each of the previous commands

6. Use `jj squash -i` to interactively select changes

7. Use "space" key to toggle select, "f" to toggle folding, "c" to confirm

8. Use the following command to abandon changes

```
jj abandon
```

## Edit Workflow

1. Add a change with a description

```
jj describe -m "only print hello world"
```

2. Make change to the code and save it

3. Start working with a commit below the current

```
jj new -B @ -m "add more comments"
```

4. Make change to the code and save it

5. Start working on the next commit

```
jj next --edit
```

6. Save changes and start new commit

```
jj new
```

## Git repository

1. Initialize a jj repo compatible with git

```
jj git init
```

2. List the git remote, both local and remote

```
git branch -a
```

3. Track the remote git repository

```
jj bookmark track master@origin
```

4. Display git remote

```
jj git remote list
```

5. List jj bookmarks and git branches

```
jj bookmark list -a
```

6. Make changes in the code and use jj to track changes

7. Set the git branch and jj bookmark to the latest commit

```
jj bookmark set master
```

8. Push changes to the remote repository

```
jj git push
```

## JJ workspaces

[Demystifying Jujutsu Workspaces][200]

[200]: https://www.joshualyman.com/2026/02/demystifying-jujutsu-jj-workspaces/

1. Create a workspace directory
mkdir ../workspace-b

2. Add a workspace to jj
jj workspace add ../workspace-b

3. Create file in `default@` workspace
echo "add line in workspace default@" >> a.txt

4. Switch to `workspace-b`
cd ../workspace-b

5. Create the same file in `workspace-b` workspace
echo "add line in workspace workspace-b@" >> a.txt

6. Update workspace
jj workspace update-stale

7. Remove `workspace-b`
rm -rf ../workspace-b

8. Remove workspace from jj
jj workspace forget workspace-b


## Links

[JJ Tutorial][1000]

[1000]: https://steveklabnik.github.io/jujutsu-tutorial/introduction/introduction.html
