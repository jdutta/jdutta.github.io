---
layout: post
title: Photography portfolio using reveal.js
category: posts
---

More than 6 years ago I created my first photoblog by handcrafting html pages that scrolled horizontally.
It was a popular way to showcase photos in a category. Years later the pixelpost platform became the
next hot thing for photographers as "photoblogging" became a trend. 
My good friend Francesco inspired me to move on to pixelpost, then learn jQuery to tweak the site 
to my fancy. I was happy with it for a few years and then figured it would be worth moving to 
wordpress with a decent theme, and avoid manual deployments. I took the migration as an excuse to
refine my earlier set of images, culling out the older ones that I no longer wanted to show in 
the portfolio. But the manual update process on the wordpress site is slow. Besides, I started
missing the ability to locally preview changes instead of changing directly in production. 
The desire to mess with a local php/mysql setup no longer exists.

Of late, creating static sites powered by tools like jekyll among others have become very popular.
A developer of today can now edit posts/pages in markdown or another favorite format, locally
preview changes, generate the static html files and push to github to make them live
at once in github pages. In my view there is no better way to showcase projects.

Although I considered jekyll to power my photoblog, the simplicity and interactivity of revealjs
made it a no-brainer choice. The yeoman generator for revealjs is very useful as it lets me
create separate slide files and change their order in a json list.
To manage the source and dist and avoid switching between `master` and `gh-pages` branch I did the
following trick:

* Local folder `photography` is the clone of [photography](https://github.com/jdutta/photography) repo.
* Local folder `photography-dist/photography` is the clone of same repo, but with only `gh-pages` 
branch. The `master` branch is removed.
* Make source changes in `photography`, like adding/changing slides, then `grunt dist` to generate
static content in `photography/dist`.
* Do an rsync to copy the changed static files. `rsync -avz dist/ ../photography-dist/photography/`.
* Go to `photography-dist/photography` to commit the changes and push to github.
* [http://jdutta.github.io/photography](http://jdutta.github.io/photography) will have new content.

Experimented with *IMG* tag vs background images to showcase large images. I prefer background image
but then I had to override this style so that the whole image is visible all the time:

```
.reveal .slide-background {
    background-size: contain;
}
```
Note: The photo portfolio is not final/official yet. Will have to find a way to link it from
joyduttaphoto.com.
