---
title: heroku
date: 2018-10-15 14:20:09
tags:
---

This installation method is required for users on ARM and BSD. You must have `node` and `npm`installed already.

```
$ npm install -g heroku
```

<!--more-->  <!--more-->

## [Verifying your installation](https://devcenter.heroku.com/articles/heroku-cli#verifying-your-installation)

To verify your CLI installation, use the `heroku --version` command:

```
$ heroku --version
heroku/7.0.0 (darwin-x64) node-v8.0.0
```

You should see `heroku/x.y.z` in the output. If you don’t, but you have installed the Heroku CLI, it’s possible you have an old `heroku` gem on your system. Uninstall it with [these instructions](https://devcenter.heroku.com/articles/heroku-cli#uninstalling-the-legacy-heroku-gem).

## [Getting started](https://devcenter.heroku.com/articles/heroku-cli#getting-started)

After you install the CLI, run the `heroku login` command to log in with your Heroku account credentials:

```
$ heroku login
Enter your Heroku credentials.
Email: adam@example.com
Password (typing will be hidden):
Authentication successful.
```

The CLI saves your email address and an API token to `~/.netrc` for future use. For more information, see [Heroku CLI Authentication](https://devcenter.heroku.com/articles/authentication).

Now you’re ready to create your first Heroku app:

```
$ cd ~/myapp
$ heroku create
Creating app... done, ⬢ sleepy-meadow-81798
https://sleepy-meadow-81798.herokuapp.com/ | https://git.heroku.com/sleepy-meadow-81798.git
```

Check out your preferred language’s [getting started guide](https://devcenter.heroku.com/start) for a comprehensive introduction to deploying your first app.

## [Tracking your app in Git](https://devcenter.heroku.com/articles/git#tracking-your-app-in-git)

If your app is already tracked in a Git repository, proceed to [Creating a Heroku remote](https://devcenter.heroku.com/articles/git#creating-a-heroku-remote).

Before you can deploy your app to Heroku, you need to initialize a local Git repository and commit your application code to it.

The following example demonstrates initializing a Git repository for an app that lives in the `myapp`directory:

```
$ cd myapp
$ git init
Initialized empty Git repository in .git/
$ git add .
$ git commit -m "My first commit"
Created initial commit 5df2d09: My first commit
 44 files changed, 8393 insertions(+), 0 deletions(-)
 create mode 100644 README
 create mode 100644 Procfile
 create mode 100644 app/controllers/source_file
...
```

Be sure to initialize the Git repository in your app’s root directory. If your app is in a subdirectory of your repository, it won’t run when it is pushed to Heroku.

Your app’s code is now tracked in a local Git repository. It has not yet been pushed to any remote servers.

## [Creating a Heroku remote](https://devcenter.heroku.com/articles/git#creating-a-heroku-remote)

Git [remotes](http://git-scm.com/book/en/Git-Basics-Working-with-Remotes) are versions of your repository that live on other servers. You deploy your app by pushing its code to a special Heroku-hosted remote that’s associated with your app.

### [For a new Heroku app](https://devcenter.heroku.com/articles/git#for-a-new-heroku-app)

The `heroku create` CLI command creates a new empty application on Heroku, along with an associated empty Git repository. If you run this command from your app’s root directory, the empty Heroku Git repository is automatically set as a remote for your local repository.

```
$ heroku create
Creating app... done, ⬢ thawing-inlet-61413
https://thawing-inlet-61413.herokuapp.com/ | https://git.heroku.com/thawing-inlet-61413.git
```

You can use the `git remote` command to confirm that a remote named `heroku` has been set for your app:

```
$ git remote -v
heroku  https://git.heroku.com/thawing-inlet-61413.git (fetch)
heroku  https://git.heroku.com/thawing-inlet-61413.git (push)
```

### [For an existing Heroku app](https://devcenter.heroku.com/articles/git#for-an-existing-heroku-app)

If you have already created your Heroku app, you can easily add a remote to your local repository with the `heroku git:remote` command. All you need is your Heroku app’s name:

```
$ heroku git:remote -a thawing-inlet-61413
set git remote heroku to https://git.heroku.com/thawing-inlet-61413.git
```

### [Renaming remotes](https://devcenter.heroku.com/articles/git#renaming-remotes)

By default, the Heroku CLI names all of the Heroku remotes it creates for your app `heroku`. You can rename your remotes with the `git remote rename` command:

```
$ git remote rename heroku heroku-staging
```

Renaming your Heroku remote can be handy if you have multiple Heroku apps that use the same codebase (for example, the staging and production versions of an app). In this case, each Heroku app has its own remote in your local repository.

The remainder of this article assumes your app has a single Heroku remote that is named `heroku`.

## [Deploying code](https://devcenter.heroku.com/articles/git#deploying-code)

To deploy your app to Heroku, you typically use the `git push` command to push the code from your local repository’s `master` branch to your `heroku` remote, like so:

```
$ git push heroku master
Initializing repository, done.
updating 'refs/heads/master'
...
```

Use this same command whenever you want to deploy the latest committed version of your code to Heroku.

Note that Heroku only deploys code that you push to the `master` branch of the `heroku` remote. Pushing code to another branch of the remote has no effect.

### [Deploying from a branch besides master](https://devcenter.heroku.com/articles/git#deploying-from-a-branch-besides-master)

If you want to deploy code to Heroku from a non-`master` branch of your local repository (for example, `testbranch`), use the following syntax to ensure it is pushed to the remote’s `master`branch:

```
$ git push heroku testbranch:master
```
