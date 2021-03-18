---
layout: post
title: "Git lb: how to get the last branches you have worked with"
date: 2021-03-18T18:18:56.555Z
---

For work reasons, I have changed my laptop. In copy all my configurations want share with you this git alias for get the recent branches.
This name of this alias is `git lb` (last branch) and this is the output:

```
  31 minutes ago: fun-branch
  2 days ago: remove-things
  3 days ago: staging
  6 days ago: remove-bugs
  7 days ago: add-bugs
  7 days ago: master
  2 days ago: dev
  3 weeks ago: enhance_something
  3 weeks ago: hotfix-1
  4 weeks ago: undo-mess

```

To use this alias, add the following to your `~/.gitconfig`:

```
    lb = !git reflog show --pretty=format:'%gs ~ %gd' --date=relative | grep 'checkout:' | grep -oE '[^ ]+ ~ .*' | awk -F~ '!seen[$1]++' | head -n 10 | awk -F' ~ HEAD@{' '{printf(\"  \\033[33m%s: \\033[37m %s\\033[0m\\n\", substr($2, 1, length($2)-1), $1)}'

```

The alias was create by Scott Stafford and this is the [link](http://ses4j.github.io/2020/04/01/git-alias-recent-branches/) for more details about this alias.
