# Basics

Add a new project.

```
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git remote add origin https://github.com/steffenpedersen/test.git
$ git push -u origin master
```

Add an existing project.

```
$ git remote add origin https://github.com/steffenpedersen/test.git
$ git push -u origin mastersh -u origin master
```

Remove all data from Git.

```
$ sudo rm -rf .git
```

Check the status of a Git project.

```
$ git status
```

Add files

```
$ git add -A
$ git add README.md
$ git add .
```

Commit the files \(Add a tag\)

```
$ git commit -m "Added the README file"
```

Ship the files

```
$ git push
```

Get all the new data

```
$ git pull
```

Clone a repository

```
$ git clone https://github.com/steffenpedersen/test.git (foldername)
```

Create branch

```
$ git checkout -b [name_of_your_new_branch]
```

Push the branch on github

```
$ git push origin [name_of_your_new_branch]
```

See all branches

```
$ git branch
```

Merge a git branch into master

```
$ git checkout master
$ git pull origin master
$ git merge test
$ git push origin master
```
