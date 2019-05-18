---
title: "How we migrated 10 years of SVN history to Git"
tags: [git,svn,migrate,bitbucket,git-svn]
description: "In this post, we'll take a look at how my team took an SVN repository with 10 years history and 55000 revisions, and migrated it all over to Git."
---

<TYPE YO POST HERE, AND DON'T FORGET THE COVER IMAGE!>

Start by generating a list of all SVN authors.

In Git Bash:

```
svn log -q | awk -F '|' '/^r/ {sub("^ ", "", $2); sub(" $", "", $2); print $2" = "$2" <"$2">"}' | sort -u > authors-transform.txt
```

```
callen = callen <callen>
```

Edit the file as necessary to set the proper name and email for each given username
```
callen = Calvin Allen <calvin.allen@outlook.com>
```

Once you have your authors mapping file, you can clone the svn repo -
```
git svn clone http://source.heuristics.net:81/svn/hs_products/learningbuilder/ --prefix=svn/ --no-minimize-url --no-metadata --ignore-paths="docs|marketing|materials|sandbox" --authors-file "authors-transform.txt" --stdlayout D:\Heuristics\Projects\LB-TRUNK-GIT-4

```

Utilize `--stdlayout` if you have traditional folders for "trunk", "branches", and "tags". Or, specify `--trunk`, `--branches`, and `--tags` instead.
Utilize `--no-metadata` to stop gumping up the log messages during conversion with git stuff.
Utilize `--no-minimize-url` if the "folder" you are cloning is not at the root of the repository itself
Utilize `--prefix` to "prefix" all of the branches and tags - default is 'origin'
Utilize `--ignore-paths` if you want to ignore certain folders during the migration


To move the tags to be proper Git tags, run:

```
cp -Rf .git/refs/remotes/tags/* .git/refs/tags/
rm -Rf .git/refs/remotes/tags
```

This takes the references that were remote branches that started with tag/ and makes them real (lightweight) tags.

Next, move the rest of the references under refs/remotes to be local branches:
```
cp -Rf .git/refs/remotes/* .git/refs/heads/
rm -Rf .git/refs/remotes
```