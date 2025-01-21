# Version Control, Git, and GitHub



## Why are we doing this?

* Because everone does version control.  Learning some good tools makes life easier.
* Because people in data science jobs spend a *lot* of time doing this.
* Because GitHub is the biggest and most popular repository of open source tools out there.
* Because the resources for this class are on GitHub too.



## Why Version Control?

* Because life without it quickly becomes a nightmare.
* Because science gets done in teams, and you don't want to mess up your team.
* Because writing papers involves making little side trips in the code (branches).
* Because bugs will happen, and you need to find where they were introduced.
 * Ideally there are also regression tests, but that's not for today.


## Also, *Provenance*

The provenance of data is the history of where
it came from, and how to reproduce it.

Good science requires good provenance! (And
publishing papers without going crazy does
too).

Part of the provenance of data is the _exact_ code
used to generate/process it, so version
control is a critical part of provenance.



## A Little History
Well, *my* history anyway.

Stage 1: "I just keep copies of my old code".

Stage 2: Revision Control System (circa 1982).
Pretty much like stage 1.

Stage 3: Concurrent Versions System (1986).
Scripts on top of RCS

Stage 4: Subversion (or SVN, 2000)

Stage 5: Git


## Is Git The Answer?

Well, it's the dominant answer _for now_.

There are competitors, like [Mercurial](https://www.mercurial-scm.org/).

Git is also still gaining new features.  We'll have to wait and see.



## Git can be confusing when you're not used to it
[![XKCD on Git](images/xkcd_git.png)](https://xkcd.com/1597/)


## There are lots of docs and tutorials available

So many that I'm not even going to list them.


## Things To Remember When Reading Tutorials

Git has a lot of potential patterns of use
(unfortunately). Which one is the tutorial
describing?

Remember that there can be *lots* of live
branches in your personal local repo. Your
actual code directory only shows one of them.
Changing branches will change which code is visible.



# Git and GitHub

GitHub is a very popular web host for open-source code.  It *uses* git,
but so do many other places.  Git came out of the Linux project and predates GitHub.

Some other sites that use git:
* [GitLab](https://about.gitlab.com/)
* [BitBucket](https://bitbucket.org/product/)  (now owned by Atlassian)

We host our class on GitHub because of history, and because they do a good job.



# Order Of Discussion
1. Big features of the architecture
2. Setting up a repo
3. Editing within the repo
4. Sharing your code
 * With your group
 * With a primary developer


We'll work through the necessary ideas and commands,
and then we'll try it all out on our test repo.



## Order Of Discussion
1. Big features of the architecture
 * It's all about a connected graph of commits.
 * The graph can have remote connections (more on this later).
 * Your source files only show one node at a time, but your git environment knows all the nodes and can switch back and forth.
 * Files need to be added to the index before they can be committed.


## A Network Of Commits

![Commits form a connected graph](images/git_history_graph.png)



## Git has an "Indexed" State

![Git Index State](images/git_index_state.png)


## Managing Indexed State

To add a file to the index (stage it):
```
git add <filename>
```
To remove an already-indexed file:
```
git rm <filename>
```
To revert to the node you were editing, undoing your add:
```
git reset <filename>
```


To check what's what:
```
git status
```
We will talk about using the `git commit` command shortly...




## Order Of Discussion
1. ...
2. Setting up a repo

To clone this class:
```
git clone https://github.com/jswelling/CMU-MS-DAS-Vis-S25
```
To create a local repo with no GitHub partner:
```
git init
```
To see what repos your clone is connected with:
```
git remote -v
```



## Order Of Discussion
1. ...
2. ...
3. Editing within the repo

Suppose you've edited a file and used `git add` to put the chenged file in the Indexed/Staged state.

To turn your indexed files into a node on your local graph:
```
git commit
```


This will open an annoying editor window for your *commit message*.  You can avoid that by
including the message on the command line:
```
git commit -m "This is my commit message"
```
After your commit, you can jump to any branch or node with:
```
git checkout <branch-or-node-hash>
```



## Order Of Discussion
1. ...
2. ...
3. ...
4. Sharing Your Code

We already learned that `git clone` connects you to a remote *origin* repo.


To get any recent changes from *upstream* (your remote origin):
```
git pull
```
* This is equivalent to `git fetch` plus `git merge`.
* It may produce *merge conflicts* which you will have to *resolve*.


To send your changes to your remote origin:
```
git push
```
But your request to push may be refused if:
* you don't have the most recent updates. (use `git pull`.)
* you don't have permission. (check to see if you can write to the remote origin.)
* some conflict arises with the graph. (stay calm, get some coffee, and think.)



## Other Useful Commands

```
git branch  # tells you what branch you are on

git merge <branch>  # explicitly merge two branches

git diff --stat

git diff

git log --graph

git rebase  # loved by many, but not by me

git bisect  # for locating bugs!
```


You can change the editor which git opens with:
```
git config --global core.editor emacs
```



# Experiments!

Now we try all of these things out.



## Preliminaries

* Accept the invitation to join the repo
 [CMU-MS-DAS-Vis-S25-GITCLASS](https://github.com/jswelling/CMU-MS-DAS-Vis-S25-GITCLASS)
 if you have not already done so.
* Clone that repo. Unless you have a shared ssh key with GitHub, use the '''https://''' form
 to make the clone.


* To push changes to the repo without a shared ssh key, you will need a GitHub personal access token.
Follow along with the instructor for the steps to create one.
 * It's best to use a [Personal Access Token (Classic)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic) today.
 * If you lose it, you will have to create a new one!


 * Whenever git asks for a password, paste in this token instead.
 * When you paste it in, it won't be visible because it's working like a password and thus is hidden.
  Don't paste it twice!



## The Game Plan

We are dividing into groups, with one experienced person per group.

Each group has a branch.  Working together, the group will update the branch.

The group leader will submit a PR to merge the updated branch back into Main.


* Each member will check out the current version of the branch, create a
  new working branch, make an edit, and then push their edit back to GitHub.
* Each member will then submit a PR to their group leader for their edit.
* The group leader will review the edit and merge the edit back into the group branch.


I'll review each group leader's PR and merge the PRs back into Main.

The tricky bit is that we are all working on the same file- `helloworld.py`.
There will be a lot of edit conflicts.  Understanding those is really the point
of the exercise.



## If You Find Yourself In A Strange Editor!

Many git commands record messages.  You can generally include your message
on the command line, with the '-m' option.

If you don't, git may throw you into a strange editor for your message.  By
default that editor is probably `vim`, which only old Linux gurus know :-(


Things to try if you find yourself in an editor you don't recognize:
* type 'a' to start inserting text.
* type escape to *stop* inserting text.
* type 'ZZ' to exit, saving your changes.
* type ':q!' to exit without saving changes.



## If you are using Git and GitHub within VSCode

Start by getting a Personal Access Token, as described above.

Here are some useful links:
* [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
* [Working with GitHub in VS Code](https://code.visualstudio.com/docs/sourcecontrol/github)
* [VS Code Home on GitHub](https://github.com/microsoft/vscode)



## Steps To Follow

To complete this in-class task, your name needs to end up in the version of
`helloworld.py` on the main branch.  We do this by editing changes into one
of the group_* branches and merging things back into main.

Start by cloning the repo to your laptop, as described earlier.  If you're
not experienced pushing code to GitHub, clone it using the `https://` version
of the repo link.


```
git clone https://github.com/jswelling/CMU-MS-DAS-Vis-S25-GITCLASS.git
cd CMU-MS-DAS-Vis-S25-GITCLASS
git pull  # probably unnecessary but a good habit
```


Check out the branch for your work group.  We'll say it's Group 3 here.
```
git checkout group_3
```
The working directory now contains the current state of the `group_3` branch.


Create your own branch from `group_3`.  The new branch will keep your work
separate from others until your group leader merges it.
Groups I've worked with usually use the developer's name to help identify
this work branch.  This is just convention;
you can call it anything as long as there are no spaces in the name.
```
git checkout -b welling/add_my_name
```


Edit the file to add your name, then add (stage) and commit the file.
```
cd src/helloworld/
<edit helloworld.py with whatever editor is convenient>
git add helloworld.py
git commit -m "some message goes here"
```


Push the resulting branch back up to GitHub.  The command below will
actually produce a warning message, because GitHub doesn't know about the
branch you created.  The warning will contain the correct command!
```
git push
```


Go back to the repo on GitHub and create a PR to merge your change branch
into your group branch (`group_3` in this case).  Be sure the "target" branch
is set to your group branch, not the main branch! Request a review from your
group leader.  We'll walk through this part in class.


You're done with the exercise!  You can watch your group leader resolve any
merge conflicts as your updates get merged with your other team members.
It's often easier to do this merge step locally rather than on GitHub,
but we'll do it on GitHub to make things quicker.

Usually, different members of a group are working on different files, so
conflicts aren't such a big problem.



## Pull Requests

Once all groups have updated their branches, we will work through the process of merging
all the branches back into the *main* branch using pull requests.  Please follow along,
because this is the way it is usually done in real work environments.
