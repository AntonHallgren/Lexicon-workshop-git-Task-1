
# notes for workshop w39 git

```bash
# used for initiating git in the selected folder
git init
```

Creates a README.md (this file) outside of the terminal

```bash
#Adds the readme file to the staging area
git add README.md

#I make sure that everything looks correctly, the md file is staged
git status

#make a commit
git commit -m "initial commit, created README.md"

#I take a look at the what information is tracked about the commit. Since there is only on I do not use --oneline
git log
```

Next I will use the following commands (writing them here before I use them in the terminal to avoid an infinite recursion of commiting updates to this file talking about the previous commits)

```bash
#Same as before
git add README.md
git commit -m "Documented my actions so far in README.md and edited it to use the md format"
```
