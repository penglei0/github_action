# github_action
learn how to use github action

# Git

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
