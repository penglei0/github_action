# github_action
learn how to use github action

# Git raw operation

## 1.Get the last commit hash

```bash
git rev-parse HEAD^{tree}
df0a78c05b4ac0a11ddd63437248a11499e465e7
```

## 2.Create a blob

one way to create a blob:
```bash
# create a file
touch me.log
# get file hash
git hash-object -w me.log
# add the file to staging area
git update-index --add me.log
```

## 3.Write blob(or the content of staging area) to a tree object

```bash
git write-tree
c530ff232192d837b7450d627bdc6e40a69518ec
```

## 4. Create a commit object

```bash
# which is the tree object, which is the parent commit
git commit-tree c530ff232192d837b7450d627bdc6e40a69518ec -m "feat: test commit" -p df0a78c05b4ac0a11ddd63437248a11499e465e7
8e9a6016075ad3431251a529f02579e99fec6396
```

## 5. Update the reference of the branch to point to the new commit SHA

```bash
git update-ref refs/heads/main 8e9a6016075ad3431251a529f02579e99fec6396
```

# Get remote pull-request

```bash
# the id of pull-request is 1
git -c protocol.version=2 fetch --prune --no-recurse-submodules origin pull/1/merge:my_local_pr_name

remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), 871 bytes | 871.00 KiB/s, done.
From github.com:penglei0/example
 * [new ref]         refs/pull/1/merge -> my_local_pr_name

# checkout to `my_local_pr_name`
git checkout my_local_pr_name

# get all impacted files in current PR
git diff --name-only -r HEAD^1 HEAD

```
