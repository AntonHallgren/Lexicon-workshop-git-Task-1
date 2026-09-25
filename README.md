
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

#The usual procedure
git add .
git commit -m "Updated .gitignore so that some files are not tracked. Updated progress in README.md"
git push
```

Now I would like an overview about what I have done so far so I check the log
```bash
#writes out a list of all commits with a hash and commit message, but no further detailed information
git log --oneline

#then I clear the command promt again
cls
```

I intend to do a bit more practice on Task 1 part 3, but first I will try to do Task 2

## Task 2
I will try to clone the repository into a new folder. I am not completely sure how this is done correctly so I will just test:

```bash
git init
git clone https://github.com/Lexicon-Smaland/Hello-World.git

```
This seems to have been incorrect: What I get is a new folder that does itself contain a .git file, so I was perhaps not sopposed to start with git init. I will start over and see if things work that way. 

```bash
#Trying clone again
git clone https://github.com/Lexicon-Smaland/Hello-World.git

#Since the .git file is inside the folder Hello-world i assume that I should step into it. This is done with the cd command. 
cd Hello-World

#Now I want to see that things work correctly, and what is inside this repository. I do this with git log --oneline
git log --oneline
```

This seems to have worked out correctly

I should now change the remote connection to my own github account. First I create a second repository on Github. 

```bash
#checking what it looked like before
git remote -v

#This was incorect
git remote add origin https://github.com/AntonHallgren/Lexicon-workshop-git-Task-2.git

#After a quick search this seems to be the correct way, wich makes more sense. 
git remote set-url origin https://github.com/AntonHallgren/Lexicon-workshop-git-Task-2.git

#confirming that it is now correct
git remote -v

#And push. 
git push -u origin main
```

Now I can see the content of the repository on my Github page. And I noticed that it keeps track of previous contributors, Mehrdad Javan and Simon Elbrink, wich is great. 

After editing the file I commit and push. 

```bash
git status
git add .
git status
git commit -m "Added description of how the table of contents in README.md is constructed using md to README.md."

#Now I can push it and see the result on my github
git push
```

Whith this, I belive task 2 is done. 

## Back to Task 1
```bash
git status
git add .
git commit -m "Updated README.md with process of Task 2"
git push
```

I will try some parts of Task 3

## Branching

I have now tried branching. To not confuse myself, I kept note of what I did elsewhere and are adding them here afterwards. 

```bash
git status
it add .
git status
git commit -m "Making sure that the latest changes to README.md are commited before I start trying branching"
git status

#I used git log --oneline as often as possible to make sure that I understand everything that happens when I create and switch between branches
git log --oneline

#Create one branch, then move to it
git branch sideBranch1
git checkout sideBranch1
git log --oneline

#Doing some changes to notes.txt
git add .
git commit -m "Adding content to notes.txt"

#Creating a second branch
git checkout main
git log --oneline
git branch sideBranch2
git checkout sideBranch2

#added and commited a new file
git add .
git commit -m "Created new file otherNotes.txt"
git log --oneline

#going back to side branch 1
git checkout sideBranch1
#noticing that the file added on sideBranch2 is not there, as expected
#editing notes.txt
git add .
git commit -m "further changes in the notes file"

#now I will try merging
git merge sideBranch1
git log --oneline


git checkout sideBranch2
#changes to document
git add .
git commit -m "Added text to otherNotes.txt"

#now try merging the other branch
git merge sideBranch2
#this was a bit confusing. it took me to a different looking interface and asked me to enter a commit mesege, which was not mentioned in the instructions I was folloing. I was able to find an explaination on how to progress, and it seems like everithing resolved correctly. 

#finally I delete the branches and look again on the log to see how it turned out. 
git log --oneline
git branch -d sideBranch1
git branch -d sideBranch2
git log --oneline

```

## Tagging
Next I thought I would try tagging. It makes sense to me to put a mark on what I was able to complete during yesterdays workshop. 
```bash
#since I am in a new session I begin with a log command to recall where I am in the project
git log --oneline

#creating a tag for last days work. 
git tag -a v1.0 -m "This was completed on thursday"

#gives a list of all tags. Currently only one
git tag

#this writes out some information about the tag and the tagged commit, inculding all changes in the commit. It took me a little bit to figure out how to get back to the commandprompt, getting to the end of the changes did not do it. Eventually I figured out that I get back by pressing 'q' for quit. 
git show v1.0

#Testing again to confirm 'q' for quit and see if it is possible to quit early, before seeing all changes. The instructions that I was following did not mention any of this
git show v1.0

#thought this would send the tag to github, but apparantly that is not how it works
git push

#after reading a bit further I found this is how you push tags to github
git push origin v1.0
#and it does indeed become visible when I go to the github page. Though not in the list of commits?

#checking the list of my commits again. 
git log --oneline
#here I do see the commit marked by the tag

#clear
cls
```

