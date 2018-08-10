---
layout: page
title:  Write a blog post
description: Some git and markdown magic
background: '/img/bg-blog.jpg'
---

### \#0: install git and Jekyll

See install instructions [here](https://fabienmaussion.info/teaching/git-jekyll-workshop/).
Don't forget to set-up your [git identity](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)!

### \#1: fork and clone the repository (one time thing)

First, you need to be logged in your [GitHub](https://github.com/) account.

Then, navigate to the [website's repository](https://github.com/agroclim-huaraz/agroclim-huaraz.github.io)
and [fork it](https://help.github.com/articles/fork-a-repo/) to your personal
account. Now clone **your fork** into your computer (this creates a new directory
at the location you are executing the command from):

```console
$ git clone https://github.com/username/agroclim-huaraz.github.io
```

Once this is done, navigate to the website's root folder and run:

```console
git remote add upstream https://github.com/agroclim-huaraz/agroclim-huaraz.github.io
```

To check that everything worked well, run ``git remote -v`` and verify that the output looks like:

```
origin	https://github.com/username/agroclim-huaraz.github.io (fetch)
origin	https://github.com/username/agroclim-huaraz.github.io (push)
upstream	https://github.com/agroclim-huaraz/agroclim-huaraz.github.io (fetch)
upstream	https://github.com/agroclim-huaraz/agroclim-huaraz.github.io (push)
```


### \#2: check that you can build the Website

From the website's root folder, run:

```bash
$ bundle exec jekyll serve
```

If packages ("gems") are missing, you might need to install them:

```bash
$ bundle install
```


### \#3: before writing a new post or actualizing the website, always update!

You want the **local master branch** to be always up-to-date with the **remote** one.
To do this, do:

```bash
# go to master
$ git checkout master
# get the info online (internet required)
$ git fetch upstream
# update
$ git merge upstream/master
```

Never change anything in the master branch! If you changed something in
master that you'd like to keep, copy the changed files somewhere else and run:

```bash
# this will overwrite all your changes
$ git checkout master
$ git reset --hard upstream/master
```

### \#4: writing a new post

Make sure that you are up-to-date (\#3). Then create a new branch:

```bash
$ git checkout -b my-new-blog-post-branch
```

Create a new markdown file in the ``_posts`` folder **following the filename
conventions**. Edit the content at your wish by changing title, subtitle, date,
author in the header. Then write your own post!

### \#5: submitting your changes

Once finished, add your file to git (necessary only for new posts).
From the root folder, run:

```bash
$ git add _posts/my-blog-post.md
```

Then commit your changes:

```bash
# This commits changes to all files.
# If you want to change only one file,
# replace -a with the file's path
$ git commit -a -m "Informative short commit message"
```

And push them to your fork:

```bash
$ git push origin my-new-blog-post-branch
```

Now, your new branch with the changes is online. Navigate to your fork's
github website, and (if github doesn't propose to do so already), select your
feature branch and propose a pull-request.

### \#6: resolution

If your post is merged right away, you're done! You can delete the branch
locally and online if you want to, but you don't *need* to. Start at \#3 again.

If you want to do further changes before merge, do:

```bash
$ git checkout my-new-blog-post-branch
# Edit the file...
# ... then commit again:
$ git commit -a -m "I made some changes"
# And push to your fork:
$ git push origin my-new-blog-post-branch
```

This will update the pull-request automatically!
