# Git The Basics

Fundamentals of using git, in an hour or less.

## What's this repo for?

This repo was set up to provide additional resources for folks planning to
learn the basics of using version control or run a session for students
wishing to do so. It was originally created by
[@gleeblezoid](https://github.com/gleeblezoid) for a seminar held at
Oxford University intended for second year students embarking on a group
project.

## Basics of version control

### Setting up git and GitHub

The docs on GitHub provide a fantastic [quickstart guide](https://docs.github.com/en/get-started/quickstart) which you should really check out.

A basic rundown of what's needed though is:

1. Install git on your machine - you can find it [here](https://git-scm.com/downloads) or use your favourite package manager.
1. Set up a global git username: `git config --global user.name "<your username>"`.
1. Set up a global git email: `git config --global user.email "<your email>"`.
1. Go to a repo (maybe use this one) and run a clone using HTTPS (in your command line app of choice): `git clone https://github.com/gleeblezoid/git-basics.git`
1. You'll be prompted for GitHub login details when you do this - when you're prompted for a password you should generate a PAT instead and enter that, you'll need to use [this page](https://github.com/settings/tokens) to generate one if you're not prompted to authenticate using your web browser.

> You can use <https://github.com/git-ecosystem/git-credential-manager> to help with safely storing your credentials.

### Covering the basics in an hour

This section is intended for folks wanting a summary of the seminar contents or to run their own session about version control.

#### Git Core Concepts

Some technical fundamentals that will help git make more sense.

##### Repositories and Commits

- Repositories are folders with change tracking (have a look in the `.git` folder of a local repo).
- Running `git clone` to copy down a remote repository creates a repo on your machine with git configuration.
- You can have many local repos for a given remote repo.
- Commits are changes tracked using git, git keeps a unique ID for every commit you make and you can use that to do all kinds of things.

##### Branches and HEAD

- A branch is just a reference to a specific commit and a history of other logged commits.
- Creating and working from branches protects your main codebase and makes splitting work easier.
- HEAD is just the commit you’re working from in the moment, you can check what it is locally from the HEAD text file in your .git/ folder (if you wanted to “go back in time” to a previous commit then `git reset --hard HEAD~2` would reset your branch to 2 commits ago).

> For relatively small group project a feature workflow is probably the best to use - if you've worked on a larger OSS project you might have encountered a forking workflow.

#### Why use version control?

Some of the top reasons for using version control.

- Even solo projects benefit from having somewhere to live where you can manage changes.
- Version control (particularly with a distributed system like git) allows multiple people to work on the same thing remotely, sync or async, and by splitting work up.
- Issues and pull requests are great for setting up tasks and communicating with each other on changes.
- The ability to track and revert changes, and branch your code, means you can try things out and safely make mistakes or break things.
- Having a change history allows you to really look at what worked and what didn't for your project.
- It's a lot easier to share your work and get help from other people without exposing more of your work than you want to.

#### Things to bear in mind

Some of the gotchas or really useful things to know when using git and GitHub.

##### The 99% workflow

You’ll need to `git clone` to get your code to your machine from your remote repo but then mostly you’ll…

- `git pull` - update code to latest before making changes
- `git add .` - line up changes for commit
- `git commit -m “message”` - commit your changes with a description
- `git push` - push your commit to your remote repo

If you know these commands then you can do most of what you need with git.

##### Not everything should be tracked in your repo

Use a [.gitignore](https://git-scm.com/docs/gitignore) file - when you set up a repo in GitHub you have the option to auto-generate one for your programming language, there's one in this repo for the demo site too [here](https://github.com/gleeblezoid/gitception/blob/main/sample-site/.gitignore).

##### Protect your secrets

- Don't put secrets in your code: Use environment variables, a password manager API, or some kind of vault.
- Separate testing from production: Keep secrets used in local testing separate from production in case of leaks when a change is pushed.
- If you ever push something sensitive to GitHub (like a password) assume it is exposed and remove the danger (e.g. by changing the password for that service). Even if you remove the commit from your Git History, once it's in GitHub there's a URL associated with your commit that can still be reached via the API.
- GitHub has [secret scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning), this is great, it doesn't remove the need for basic sensible security practices.

##### Keep changes small and talk to each other

Version control is a great tool but it can't do everything! You need to have a consensus on how to work on your project and talk to each other about changes and how they'll be managed.

- Try keeping to one change per branch/pull request: The smaller and easier to describe a change is, the more sense your git history will make.
- Be descriptive, use branches: Separate changes into branches so you can talk about them before merging to main.
- Decide how you’re going to work: Version control is a tool, you need to agree how you’ll assign and manage work.

### Further resources

For more information check out the resources at [skills.github.com](https://skills.github.com) and [git-scm.com/doc](https://git-scm.com/doc).

If you're planning to run a locally hosted git demo check out this repo's doc on configuring a gogs server [here](https://github.com/gleeblezoid/gitception/blob/main/docs/setting_up_a_gogs_demo_server.md).

There's also a sample Flask site [here](https://github.com/gleeblezoid/gitception/blob/main/sample-site) if you want something to play around with - you'll need python3, pipenv, and pre-commit installed.
