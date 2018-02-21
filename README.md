# calvinallen / calvinallen.net

This is the repo for my blog, which accepts pull requests/issues/etc.

This repo is connected to Netlify. Every push triggers a build and deploy.  TLS is enabled, and required, using a LetsEncrypt certificate
from Netlify.

I also set up a Microsoft Flow event that triggers every night at midnight that pings Netlify and tells them to build and deploy the site.  This
lets me push a blog post with a future date, and then have it deployed at midnight the day of.

Netlify rocks.
