# Static Blog Demo (Jekyll)

This was set up in the afternoon / evening of May 6th, 2023. I don't know Ruby and this is the first time I've deployed Jekyll, but figured it was the best solution for getting a nice site up and running very fast.

## Thinking

* Setting up a database is always a hassle - let's not do that. Let's not even go near a database.
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
sudo apt update
sudo apt install ruby ruby-dev apache2-utils
sudo gem install jekyll bundler
```

Copied contents of repository to remote server. Installed using `bundle install`. Used minimal mistakes jekyll theme.

Setup and configured nginx.

Using following guide as reference, setup services to automatically host admin and static site separately.
https://jekyll.github.io/jekyll-admin/self-hosting

Setup basic HTTP auth with htpasswd.

Setup HTTPS using certbot. Setup crontab for auto-renewal.

Added content and configured.

## Issues / Upgrades

* Would have preferred a Docker container based setup, but would have been frustratingly complex to set up in timeframe given available images.
    * If had used a Docker-based setup, would have been a lot easier to save and load and have portable config.
* Unfamiliar with Ruby / Jekyll workflow - first time setting up this structure. Some weirdness around gem locations / setup as a result.
* Uses HTTPS auth - fine for now, but could have a nicer portal given more time.
* Could have set static site to be pushed to a CDN of some sort e.g. Cloudfront.
* Would be cool to set up processes to keep the blog and this git repository in sync.
    * Server-side, watching for changes to the flat files and pushing updates to the git periodically (if any changes).
    * Client-side, pushes to the git repo should trigger an upload and rebuild on the server.