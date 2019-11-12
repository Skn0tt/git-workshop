# git-Tutorial

Authors: Jannis Baum, [Simon Knott](https://twitter.com/skn0tt)

This script was conceptualized for a tutorial at [HPI](https://hpi.de)-StubS.

## General Idea

This tutoral is made up of two parts:

1. The theory behind Git (DAGs, immutable commits)
2. A practical introduction using a specific project the audience needs to collaborate on (live!)

This way, the theoretical ideas (which are very helpful to understand Git) can support active learning which is achieved by the practical introduction.
We will use the Git CLI because GUIs hide most of what's going on (they're comfortable to use, but won't help you understanding Git)
After the students got to work with some commands hands-on, I will summarize the most-used git routines so these stick in mind.
At the end, I want to give a quick overview on what can be learned / done from here.

## What do I want to teach?

- The idea of Git
  - Distributed Version Control System (VCS)
  - Made up of an directed, acyclic graph (DAG)
  - a fixed / immutable version history
- Basic Git Commands: `git ...`
  - `init`
  - `add`
  - `rm`
  - `commit`
  - `checkout`
  - `log`
  - `checkout -b`
  - `merge`
  - `push`
  - `pull`
- Git routines
  - Adding files, committing them
  - Pushing & Pulling from remote
  - Merging a branch
- Ways down the rabbit hole
  - Publish one of your projects to GitHub
  - Make a PR to a project you like (you'll first need to find out about PRs beforehand)
  - Find out about rebasing (aka rewriting history, what used to be forbidden)
  - Explore the Git ecosystem (CI; CD; Verification; etc.)
  - <learngitbranching.js.org>
  - [Git Fu Developing](https://www.youtube.com/watch?v=f-Br8cud2eI&t=947s)
    - `git bisect` is especially cool!
- [Git Cheat Sheet by JRebel](https://jrebel.com/wp-content/uploads/2019/05/git-cheat-sheet.pdf)

## How do I teach the practical part?

Prerequisites: a public git repository that all students are invited to.

The following steps are meant to be repeated by the students on their own machines.
I will demonstrate the usage of Git by creating a new repository (`mkdir git-tut && cd git-tut && git init`) and create a file (`echo hallo > hi.txt`).
I'll then show that it was detected, but not yet added to tracking (`git status`).
Then I'll add the file (`git add hi.txt`) and show how it went into staging (`git status`).
I'll then commit the staged changes (`git commit`).
I'll show the newly created commit in the commit log (`git log`).
I'll ask them to do another commit on their own.
After we've done that, I'll show the commit log again (`git log`) and ask them to copy the SHA of the first commit.
I'll then checkout this commit (`git checkout $SHA`) so they see how you can move back in time using Git.

The second part of the tutorial will focus on collaboration.
I will clone the prerequisite Git repository and commit the following text outline:

```
# All you need to know about Git

## Trivia

- Who has invented it?
- What does `git` mean?

## Theoretical

- What data structure is Git based upon?

## Cheat Sheet

- What are commonly used git commands?

## Git Ecosystem

- What are products and companies that center around Git integration?
```

I'll then push that to the repository (`git push`) and ask them to clone the repo (`git clone <...>`).

Now I divide the students into some groups and distribute the different sections of the outline amongst them.
It's important to assign one section to two of the groups, so we've got an example for a merge conflict.

Each of the groups shall branch individually (`git checkout -b <mySection#I>`), fill out their sections, commit them and push them to the remote `git push --set-upstream origin <mySection#I>`.

Once they pushed, I can fetch all the commits and merge into `master` in front of them.
Most of the branches will work out fine, one of the sections will cause a merge conflict.
