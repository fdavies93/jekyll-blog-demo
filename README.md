# Static Blog Demo (Jekyll)

## Thinking

* Setting up a database is always a hassle - let's not do that.
* Our spec requires only that we have a headless CMS and that there's a static output.
* Why not just use flat files?
* I could write some git actions to render flat files (e.g. MD files).
* Or I could just use a static site builder like Jekyll.
* I can use the extra time to build some demo content and set up a better deploy than if I write a lot of code.
* Authentication will always be time-consuming, let's sidestep it for now.

### Alternative solution

* Could have used git as my "CMS" and used git actions to automatically deploy. (If I had used **Hyde** then this would have made sense but Hyde is deprecated.)
* This would have simplified authorisation / security and made version control automatic.
* But as git is not really a "Headless CMS",  I figured it was too spicy for the brief.
* In a real-world scenario, having a more conventional CMS backend is probably more helpful for less technical users than forcing everyone to use git.


## Stack

* Amazon EC2 service
* Nginx
* Ruby, Jekyll, Jekyll-Admin

## Server Setup Process

Created new EC2 instance.
Installed needed packages.

```
sudo apt install ruby ruby-dev
sudo gem install jekyll bundler
```

Copied contents of repository to remote server.

Setup and configured nginx.

Using following guide as reference, setup services to automatically host admin and static site separately.
https://jekyll.github.io/jekyll-admin/self-hosting

## Issues

* Would have preferred a Docker container based setup, but would have been too complex to set up in timeframe given available images.
* Unfamiliar with Ruby / Jekyll workflow - first time setting up this structure. Some weirdness around gem locations / setup as a result.