---
layout: post
title: Managing project pages in github.io
category: posts
---

`xyz.github.io` is a great place to host personal coding projects. To manage the source and dist and to avoid switching between `master` and `gh-pages` branch the following workflow seems to work well:

Lets say the project folder is `photography` which should be available in 
`jdutta.github.io/photography`.

* Local folder `photography` is the clone of [photography](https://github.com/jdutta/photography) repo.
* Local folder `gh-pages/photography` is the clone of same repo, but with only `gh-pages` 
branch. The `master` branch is removed.
* Make source changes in `photography`, like adding/changing slides, then `grunt dist` to generate
static content in `photography/dist`.
* Do an rsync to copy the changed static files. `rsync -avz dist/ ../gh-pages/photography/`.
* Go to `gh-pages/photography` to commit the changes and push to github.
* [http://jdutta.github.io/photography](http://jdutta.github.io/photography) will have new content.
