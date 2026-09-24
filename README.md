
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
## Github

Created Github repository, then folowing the process from last lecture to connect it

```bash
#connect to the Github repository
git remote add origin https://github.com/AntonHallgren/Lexicon-workshop-git-Task-1.git
#verify
git remote -v
#push my branch to the remote repository
git push -u origin main
```
After doing this I can see on that my branch has been added to the remote repository in my browser. 

Then I will track my work so far
```bash
git status
git add README.md
git commit -m "Updated README.md with the process of connecting to a remote repository"
```
and after that clear the command prompt
```bash
cls
```

## Track changes
I will add more files to to track changes in.
```bash
#Checking if git noticed that I added a new file, notes.txt
git status

#Adding all files to the staging area
git add .

#Checking that the new file is added correctly
git status

git git commit -m "Added the file notes.txt"
```

Now I will try pushing.

```bash
#sends my changes to the remote repository
git push
```
And I can look at the remote repository and see that it has updated

## .gitignore

Before going further with adding and edditing files to have for the sake of having something to push I will start with a gitignore file


```bash
#The usual procedure
git status
git add .gitignore
git commit -m "Created .gitignore file"
git push
```
Now that I have a .gitignore file I can add a file "secrets.txt" and make sure that it is not tracked by git. 

```bash
#Creates file secrets.txt
git status
#See that the file is detected by git

#updates .gitignore (in text editor)
git status
#sees that secrets.txt is no longer tracked, and .gitignore has changes
```