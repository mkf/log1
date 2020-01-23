---
title: "Today I asked on Super User: Are .gitignore files from directories above the repository's or from home directory loaded in any versions of Git?"
date: 2020-01-23T04:12:09+01:00
draft: false
---

Today I asked on Super User: Are `.gitignore` files from directories above the repository's or from home directory loaded in any versions of Git?

https://superuser.com/questions/1519345/are-gitignore-files-from-directories-above-the-repositorys-or-from-home-direct

https://dev.to/mkf/i-just-asked-are-gitignore-files-from-directories-above-the-repository-s-or-from-home-directory-loaded-in-any-versions-of-git-5744

-------

Are `.gitignore` files from directories above the repository's or from home directory (`~/.gitignore`) loaded in any versions of Git?

`~/.gitignore` is mentioned by some advisory web postings despite not working in the version of Git on my system, and my system manual is unclear about how far up Git will walk looking for a `.gitignore`, although only mentions `$XDG_CONFIG_HOME/git/ignore` as a home directory global gitignore file location.

My problem stems from, to manage my home directory dotfiles i have presently chosen to use Git with a custom `GIT_DIR` environment variable setting, which does fine with not having Git default to that repository in any subdirectories of my `~`.

But, as `.gitignore` is hardcoded and can't be selected by an environment variable (which i would like to be like `"${GIT_DIR%/}ignore"`), being afraid that on some of my systems `~/.gitignore` could end up applying either globally or in repositories in the subdirectories of `~`, i resorted to adding the below snippet to my `${GIT_DIR}/info/exclude` and then staging the `${GIT_DIR}/info/exclude` file into the repository, keeping all my gitignore entries that are to apply to my dotfiles management repository in there (and in `.gitignore` files in dotfiles-only subdirectories). What i don't like about it is that it's pretty dirty and it might cause minor problems sometimes.

The snippet mentioned above, with `.gd` being my `$GIT_DIR`:
```gitignore
/.gd/**
!/.gd/info/
!/.gd/info/exclude
```

------
