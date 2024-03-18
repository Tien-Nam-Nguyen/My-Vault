---
type:
  - Tech
tags:
  - Git
  - Source
  - Version
published: true
folder: Tech
---
# What is git?

Git is a version control system that tracks change in any set of computer files, usually used for coordinating work among programmers who are collaboratively developing source code during software development.

Its goals include speed, data integrity and support for distributed, non-linear workflows.

Git is the most popular system nowadays. There are many platforms offerings Git repository services, include Github, SourceForge, BitBucket and GitLab.

![Imgur](https://i.imgur.com/6AKvT7Y.png)

# Some useful commands
- git init: initialize a repo
- git remote add origin *url*: add a remote to current repo
- git remote -v: show remote 
- git remote set-url origin *url*: set remote url
- git remote rename origin destination: change remote name from 'origin' to 'destination'
- git add . : add all the files to staging area
- git add -f *file*: force a file to staging area, even if it is in .gitignore
- git status: show repo's status
- git status -s: show status with short version
- git commit -m "message": create a commit
- git log --oneline: show commit history in short version
- git log --graph: show a commit history in graph
- git log --author='author_name': filter commit by author's name
- git branch *bugFix*: create a branch
- git checkout *bugFix*: switch to a branch
- git checkout -b *bugFix*: create and switch to a branch
- git merge *bugFix*: merge a branch into current branch
- git rebase *main*: copy the current commit to be the new commit in *main* branch

![Imgur](https://i.imgur.com/OV9R1B6.png)

- git reset *commit_id*: return to a specific previous commit and **remove all commits behind that commit**

![google](https://res.cloudinary.com/practicaldev/image/fetch/s--_TOAAWa3--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/o3z2fahi0p3ccer357ov.PNG)

- git revert *commit_id*: create a new commit that is a clone of the commit right before the *commit_id*.
![google](https://res.cloudinary.com/practicaldev/image/fetch/s--uTJUSMXE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tte6mxh17q93t043h2b8.png)

- git mv *old_file_name* *new_file_name*: change file's name
- git rm *file_name*: remove file **even on local machine**
- git clean: delete untracked files

# .gitignore file

It is a file that lists all the files and directory that should not be tracked by repository.

```gitignore
file.txt
dir/
dir/*
*.txt
dir/*.txt
dir*
```
# References

<iframe
		width=600px,
		height=350px,
		src="https://en.wikipedia.org/wiki/Git">			

</iframe>

<iframe
		width=600px,
		height=350px,
		src="https://nulab.com/vi/learn/software-development/git-tutorial/git-commands-settings/basic-git-commands/">			

</iframe>


