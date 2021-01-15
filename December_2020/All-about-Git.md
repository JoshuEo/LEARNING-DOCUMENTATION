# Step 1: Creating a local git repository
When creating a new project on your local machine using git, you'll first create a new repository (*repo* for short)
- git init: Used to initialize a git repository of the folder
```git
~> git init
Initialized empty Git repository in /home/.git/
```

# Step 2: Add a new file to the repo
```git
 ~> git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        test

nothing added to commit but untracked files present (use "git add" to track)
```
- What this basically says is "Hey, we noticed you created a new file called test, but unless you use the 'git add' command we aren't going to do anything with it."



# Step 3: Add a file to the staging environment

A *commit* is a record of what files you have changed since the last time you made a commit. Essentially, you make changes to your repo (for example, adding a file or modifying one) and then tell git to put those files into a commit.
- Commits make up the essence of your project and allow you to go back to the state of a project at any point.

To add a file to a commit, you first need to add the staging environment: git add <filename>
Once you've used the git add command to add the files to the staging environment, you can then etll git ot package them into a ocmmit using the *git commit* command

```git

 ~> git add test
 ~> git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   test
```
- The file has not yet been added to a commit, but it's about to be.

# Step 4: Create a commit
```git
git commit -m "Your message about the commit"
```
- The message at the end of the commit should be something related to what the commit contains - maybe it's a new feature, maybe it's a bug fix, maybe it's just fixing a typo.

```git
$ git commit -m "This is my first commit!"
[master (root-commit) 0fd7dc8] This is my first commit!
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
```

# Step 5: Create a new branch
Say you want to make a new feature but are worried about making changes to the main project while developing the feature. This is where *git branches* come in.
- Branches allow you to move back and forth between 'states' of a project
- Once you're done with the page, you can *merge* your changes from your branch into the primary branch


git checkout -b <branch>: Create a new branch
git branch: List branches


# Step 6: Create a new repository on GitHub
If you only want to keep track of your code locally, you don't need to use GitHub. But if you want to work with a team, you can use GitHub to collaboratively modify the project's code.

To create a new repo on GitHub, log in and go to the GitHub home page. You should see a green '+ New repository' button: 

After clicking the button, GitHub will ask you to name your repo and provide a brief description

When you're done filling out the information, press the 'Create repository' button to make your new repo.

GitHub will ask if you want to create a new repo from scratch or if you want to add a repo you have created locally. In this case, since we've already created a new repo locally, we want to push that onto GitHub so follow the '....or push an existing repository from the command line' section: 

git remote add origin https://github.com/test/test.git
git branch -M main
git push -u origin main

```git
$ git remote add origin https://github.com/test/test.git
$ git branch -M main
$ git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 234 bytes | 234.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/test/test.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

Step 7: Push a branch to GitHub
Now we'll push the commit in your branch to your new GitHub repo. This allows other people to see the changes you've made. If they're approved by the repository's owner, the changes can then be merged into the primary branch.

To push changes onto a new branch on GitHub, you'll want to run git push origin yourbranchname. GitHub will automatically create the branch for you on the remote repository

You might be wondering what that "origin" word means in the command above. What happens is that when you clone a remote repository to your local machine, git creates an alias for you. In nearly all cases this alias is called "origin." It's essentially shorthand for the remote repository's URL. So, to push your changes to the remote repository, you could've used either the command: 
- git push git@github.com:git/git.git yourbranchname or
- git push origin yourbranchname


https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners
