---
layout: post
title: "Installing from github without git"
date: 2015-06-24 12:00:00
tags: "python, pip, git, github"
---

You can install python packages from github (or any Git, Mercurial, Subversion and Bazaar repo) if you have git (or other vcs command) available:
	
	pip install git+git://github.com/<user>/<repo>

You can also just install from a remote archive file which github will make for you!

	pip install --upgrade https://github.com/<user>/<repo>/tarball/master
