# PP5

## Goal

In this exercise you will:

* Use Git **locally** on your own machine: create branches, make commits, and merge them back.
* Set up and interact with a **bare** Git repository on an SSH‐accessible server (e.g. **vorlesungsserver**, or any machine you have SSH access to).
* Push and pull to/from **GitHub** and the **THGA GitLab** server.
* Practice **forking** an existing repo, making changes, and submitting a **Pull Request** (on GitHub) or **Merge Request** (on GitLab).

**Important:** Start a stopwatch when you begin and work uninterruptedly for **90 minutes**. Once time is up, stop immediately and document exactly where you had to pause.

---

## Workflow

1. **Fork** this repository
2. **Modify & commit** your solution
3. **Submit your link for Review**

---

## Prerequisites

* Several starter repos are available here:
  [https://github.com/orgs/STEMgraph/repositories?q=Git%3A](https://github.com/orgs/STEMgraph/repositories?q=Git%3A)
* Ensure you have **SSH access** to a remote server (e.g., “vorlesungsserver”).
* Throughout, consult Git’s built-in man-pages (`git help <command>`) for explanations and options.

---

## Tasks

### Task 1: Local Git – Branching & Merging

1. Create a new directory in your home directory and initialize a repository in it. 
2. In one of your cloned repos, initialize a new branch called `feature-1`.
3. On `feature-1`, create a file `feature.txt` containing a short description of what you’re doing.
4. Commit your changes, then switch back to `master` (or `main`), and merge `feature-1` into your `master`.
5. Resolve any merge conflicts (if they arise) by hand, then commit the merge. 

**Your Commands & Output**

nick@DESKTOP-F0EDLD6:/mnt/c/Users/Nick$ cd ..
nick@DESKTOP-F0EDLD6:/mnt/c/Users$ cd \Projekt
#nick@DESKTOP-F0EDLD6:/mnt/c/Users/Projekt$sudo git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /mnt/c/Users/Projekt/.git/
nick@DESKTOP-F0EDLD6:/mnt/c/Users/Projekt$
nick@DESKTOP-F0EDLD6:/mnt/c/Users/Projekt$ touch feature-1
nick@DESKTOP-F0EDLD6:/mnt/c/Users/Projekt$ touch feachre-1 feature.txt
nick@DESKTOP-F0EDLD6:/mnt/c/Users/Projekt$ cd feature-1
-bash: cd: feature-1: Not a directory
nick@DESKTOP-F0EDLD6:/mnt/c/Users/Projekt$ main feature-1
Command 'main' not found, did you mean:
  command 'rain' from deb bsdgames (2.17-30)
  command 'maim' from deb maim (5.7.4-2)
  command 'mail' from deb mailutils (1:3.16-1build1)
  command 'man' from deb man-db (2.12.0-1)
Try: sudo apt install <deb name>



### Task 2: Bare Repository on an SSH Server

1. On your SSH server (e.g., “vorlesungsserver”), create a **bare** repo at `~/repos/myproject.git`:

   ```bash
   ssh youruser@vorlesungsserver \
     "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"
   ```
2. On your local machine, add it as a remote named `origin-ssh`:

   ```bash
   git remote add origin-ssh youruser@vorlesungsserver:~/repos/myproject.git
   ```
3. Push your `master` branch to `origin-ssh`, then clone it into a fresh directory to verify.

**Your Commands & Output**

nick@DESKTOP-F0EDLD6:/mnt/c/Users/Projekt$ ssh user97@128.140.85.215
user97@128.140.85.215's password:
Permission denied, please try again.
user97@128.140.85.215's password:
Linux vorlesung 6.1.0-21-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.90-1 (2024-05-03) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Mon May 19 12:54:03 2025 from 88.153.44.136
user97@vorlesung:~$ mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /home/user97/repos/myproject.git/
user97@vorlesung:~/repos/myproject.git$
user97@vorlesung:~/repos/myproject.git$ git remote add origin-ssh user97@128.140.85.215 :~/repos/myproject.git
usage: git remote add [<options>] <name> <url>

    -f, --fetch           fetch the remote branches
    --tags                import all tags and associated objects when fetching
                          or do not fetch any tag at all (--no-tags)
    -t, --track <branch>  branch(es) to track
    -m, --master <branch>
                          master branch
    --mirror[=(push|fetch)]
                          set up remote as a mirror to push to or fetch from

user97@vorlesung:~/repos/myproject.git$
user97@vorlesung:~/repos/myproject.git$ git remote add --mirror=fetch user97@128.140.85.215 :~/repos/myproject.git
error: remote user97@128.140.85.215 already exists.
user97@vorlesung:~/repos/myproject.git$

### Task 3: GitHub & THGA GitLab

1. On [GitHub](github.com), create a new empty repo under your account named `myproject-gh`.
2. On [THGA GitLab](gitlab.thga.de), create a new project named `myproject-gl`.
3. In your local repository, add these as remotes:

   ```bash
   git remote add github  git@github.com:YOUR_USERNAME/myproject-gh.git
   git remote add gitlab  git@gitlab.thga.de:YOUR_USERNAME/myproject-gl.git
   ```
4. Push your `master` branch to both `github` and `gitlab` remotes.

> Hint: You are just adding two more bare-remotes to your already existing repository!

**Your Commands & Output**

user97@vorlesung:~/repos/myproject.git$ git remote add github  git@github.com:NickTluczykont/myproject-gh.git
user97@vorlesung:~/repos/myproject.git$ git remote add gitlab  git@gitlab.thga.de:nick.tluczykont/myproject-gl.git
user97@vorlesung:~/repos/myproject.git$ git branch
user97@vorlesung:~/repos/myproject.git$ git main
git: 'main' is not a git command. See 'git --help'.

The most similar command is
        mailinfo
user97@vorlesung:~/repos/myproject.git$ git commit -m NickTluczykont/myproject-gh.git
fatal: this operation must be run in a work tree
user97@vorlesung:~/repos/myproject.git$ git commit -m nick.tluczykont/myproject-gl.git
fatal: this operation must be run in a work tree


### Task 4: Fork, Modify, and Pull/Merge Request

1. On GitHub, **fork** one of the repos from the STEMgraph org.
2. Clone your fork locally, create a branch `pp5-changes`, and make a small change (e.g., update the README).
3. Commit and push `pp5-changes` to **your** fork, then open a **Pull Request** against the original repo.
4. Repeat on THGA GitLab: fork another students repository, clone, branch, change, push, and open a **Merge Request**. If your peers opened a merge request to your repository, review and merge or decline it!

**Your PR/MR Links & Descriptions**

* GitHub PR: *paste URL and a one-sentence summary*
* GitLab MR: *paste URL and a one-sentence summary*

---

**Remember:** Stop working after **90 minutes** and record where you stopped!
