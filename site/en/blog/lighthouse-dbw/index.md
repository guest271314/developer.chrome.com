---
layout: 'layouts/blog-post.njk'
title: Building a better web with Lighthouse
description: >
    What's new in Lighthouse. Redesign, new best practice audits, and an online report viewer.
authors:
  - ericbidelman
date: 2016-12-19 
updated: 2016-12-19 
---

{% Aside %}
[Lighthouse](https://developers.google.com/web/tools/lighthouse/) is an
[open-source](https://github.com/GoogleChrome/lighthouse), automated tool for
improving the quality of your web apps. You can install it as a
[Chrome Extension][crx] or run it as a Node command line tool. When you
give Lighthouse a URL, it runs a barrage of tests against the page and then
generates a report explaining how well the page did and indicating areas for 
improvement.
{% endAside %}


Since Google I/O, we've been hard at work making Lighthouse an awesome companion
for building great [Progressive Web Apps](https://developers.google.com/web/progressive-web-apps/):

- Welcomed 50 new [contributors][contribs] to the project
- Shipped 15 [releases](https://github.com/GoogleChrome/lighthouse/releases)
- Added ~20 additional [audit tests][audits] (~50 total)

Today, we're happy to announce the 1.3 release of Lighthouse. Lighthouse 1.3
includes a bunch of big new features, audits, and the usual bug fixes. You can
install it from npm (`npm i -g lighthouse`) or [download the extension][crx]
from the Chrome Web Store.

So what's new?

## New look and feel

If you've used an earlier version of Lighthouse, you may have noticed that the
logo is new! The HTML report and Chrome Extension have also undergone a complete
refresh, with a cleaner presentation of scoring and more consistency across
audit results. We've also added helpful debug information when you fail a test
and include pointers to recommended workarounds.

<figure>
{% Img src="image/T4FyVKpzu4WKF1kBNvXepbi08t52/ButIvrow5XReY690hZCI.png", alt="Lighthouse Report", width="800", height="542" %}
</figure>

## New Best Practices

To date, Lighthouse has focused on performance metrics and the quality of PWAs.
However, an overarching goal of the project is to provide a guidebook for all of
web development. This includes guidance on general best practices, performance
and accessibility tips, and end-to-end help on making quality apps. 

"Do Better Web" is an effort within the Lighthouse project to help developers do
better on the web. In other words, help them modernize and optimize their web
applications. Oftentimes, web devs use outdated practices, anti-patterns, or hit
known performance pitfalls without realizing it. For example, it is
[widely known](https://developers.google.com/web/fundamentals/design-and-ux/animations/) that JS-based
animations should be done with [`requestAnimationFrame()`][raf] instead of
[`setInterval()`][setinterval]. However, if the developer is unaware of the
newer API, their web app needlessly suffers.

Lighthouse 1.3 includes 20+ [new best practice][dbwaudits] suggestions ranging
from tips for modernizing CSS & JavaScript features to performance
recommendations like: "Reduce the number of render-blocking assets", "Use
[passive event listeners](https://developers.google.com/web/updates/2016/06/passive-event-listeners) to
improve scrolling performance".

<figure>
{% Img src="image/T4FyVKpzu4WKF1kBNvXepbi08t52/Wxax0drJwJQNjJM4YOwH.png", alt="Do better web best practices.", width="800", height="544" %}
</figure>

We'll continue to add more recommendations over time. If you have suggestions
for best practices or want to help us write an audit, [file an issue][dbwissues]
on GitHub.

## Report Viewer

Last but not least, we're excited to announce a new web viewer for Lighthouse
results. Visit [googlechrome.github.io/lighthouse/viewer][viewer], drag and drop
the output of a Lighthouse run (or click to upload your file), and voila. "Insta"
Lighthouse HTML report.

<figure>
  {% Img src="image/T4FyVKpzu4WKF1kBNvXepbi08t52/uwSIGy3PULkJNgXT8W9K.png", alt="Report viewer.", width="656", height="320", class="screenshot" %}
  <figcaption>
    <a href="https://googlechrome.github.io/lighthouse/viewer"
       target="_blank">Report Viewer</a>
  </figcaption>
</figure>

Lighthouse Viewer also lets you share reports with others. Clicking the share 
icon will sign you in to GitHub. We stash reports as secret gist in your account
so you can easily delete a shared report or update it later on. Using GitHub for
data storage also means you get version control for free!

<figure>
 {% Img src="image/T4FyVKpzu4WKF1kBNvXepbi08t52/fN5y3WEasrogn6hA6HNW.png", alt="Viewer architecture.", width="422", height="294" %}
  <figcaption>Viewer Architecture</figcaption>
</figure>

Existing reports can be reloaded by Lighthouse Viewer by adding `?gist=GIST_ID`
to the URL:

<figure>
  {% Img src="image/T4FyVKpzu4WKF1kBNvXepbi08t52/CpZv3c1hE0DiJFhCTgzc.png", alt="Viewer architecture 2.", width="418", height="237" %}
  <figcaption>Viewer Architecture 2</figcaption>
</figure>

For all the details on the latest in Lighthouse, see the
[full release notes](https://github.com/GoogleChrome/lighthouse/tags) over on
GitHub. As always, [hit us up][contribs] to [report bugs][lhbugs], file feature
requests, or brainstorm [ideas](https://github.com/GoogleChrome/lighthouse/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+bug%22) on what you'd like
to see next.

[crx]: https://chrome.google.com/webstore/detail/lighthouse/blipmdconlkpinefehnmjammfjpmpbjk
[contribs]: https://github.com/GoogleChrome/lighthouse/graphs/contributors
[lhbugs]: https://github.com/GoogleChrome/lighthouse/issues
[audits]: https://github.com/GoogleChrome/lighthouse/tree/master/lighthouse-core/audits
[dbwaudits]: https://github.com/GoogleChrome/lighthouse/tree/master/lighthouse-core/audits/dobetterweb
[dbwissues]: https://github.com/GoogleChrome/lighthouse/issues?q=is%3Aissue+is%3Aopen+label%3ADoBetterWeb
[raf]: https://developer.mozilla.org/docs/Web/API/window/requestAnimationFrame
[setinterval]: https://developer.mozilla.org/docs/Web/API/WindowTimers/setInterval
[viewer]: https://googlechrome.github.io/lighthouse/viewer
