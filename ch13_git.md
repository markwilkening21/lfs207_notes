# Chapter 13 - git

You can get a basic list of git commands by just typing git, which will give the list below.

There are only a few global options that apply, those prefixed with -- in the below listing. Many of the subcommands have their own options.

Visit the official reference where you can find the complete list of subcommands, environment variables, and more - by specific git version.

## Core Git Commands

### start a working area (see also: git help tutorial)
|  command      |  description                   |
|------------|------------------------------------------------------------------------|
|   clone    |         Clone a repository into a new directory                        |
|   init     |         Create an empty Git repository or reinitialize an existing one |

### work on the current change (see also: git help everyday)
| command | description |
| --------|------------|
|   add   |            Add file contents to the index |
|   mv     |           Move or rename a file, a directory, or a symlink|
|  restore  |         Restore working tree files|
|   rm       |         Remove files from the working tree and from the index|
|   sparse-checkout |  Initialize and modify the sparse-checkout |


### examine the history and state (see also: git help revisions)
| command | description |
| --------|------------|
|   bisect|            Use binary search to find the commit that introduced a bug|
|   diff|              Show changes between commits, commit and working tree, etc|
|   grep|              Print lines matching a pattern|
|   log|               Show commit logs|
|   show|              Show various types of objects|
|   status|            Show the working tree status |

### grow, mark and tweak your common history 
| command | description |
| --------|------------|
|   branch|            List, create, or delete branches|
|   commit|            Record changes to the repository|
|   merge|             Join two or more development histories together|
|   rebase|            Reapply commits on top of another base tip|
|   reset|             Reset current HEAD to the specified state|
|   switch|            Switch branches|
|   tag|               Create, list, delete or verify a tag object signed with GPG |

### collaborate (see also: git help workflows)
| command | description |
| --------|------------|
|   fetch|             Download objects and refs from another repository|
|   pull|              Fetch from and integrate with another repository or a local branch|
|   push|              Update remote refs along with associated objects|


## Minimal Global Configuration
Unlike some other recent revision control systems, git wants you to set up an author name and email address rather than just default to
your current user id. Let’s set that up now and additionally prefer the more modern default branch name main.

**$ git config --global user.name "Gladys West"**

**$ git config --global user.email "gwest@example.com"**

**$ git config --global init.defaultBranch main**

These settings will get written to your ˜/.gitconfig. The ˜/.gitconfig file can contain quite a lot more. Many people have shortcuts
for frequently typed commands, custom ways to print histories, and different diff commands.

## Create and Initialize Repository

### Create a new directory and initialize it as a git repository:

**$ mkdir /tmp/LFgit**

**$ cd /tmp/LFgit**

**$ git init**

## Branch Analogy

Branch Analogy
It can be useful to employ analogies to physical objects to understand git concepts. If we think of each commit like a page in a binder, then we can think of a branch
as a binder that happens to have an organizer tab at the very back to make it easy to flip to the last and latest page.

When we make a commit by adding a page at the end of the binder, that end tab is still going to bring us quickly to the last and latest page/commit.

Making a new branch from this one is akin to copying all pages and putting them in a new binder. If we then add new pages to the new binder, our old binder is unchanged 
with the original last page and final tab.

Finally, let’s think about each of these binder/branches that we’ve made, as all residing on the same shelf, with that shelf being our git repository, residing
locally in a directory with a .git subdirectory.

To create a new branch from the current branch as the source for the copy:

**$ git checkout -b <name>**

To create a new branch with the upstream branch as the source for the copy:

**$ git checkout -b <name> remotes/origin/main**
