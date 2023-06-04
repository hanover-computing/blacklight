# Blacklight
> An open platform for analyzing the web

## Project Goals
Users and applications have to visit untrusted, unverified web pages of unknowable quality every day, with questions such as:
- is it "safe" to visit?
  - does it have viruses?
  - is the page phishing/scamming people?
  - what about extreme/NSFW content?
- even if it's "safe", how "painful" is it to visit?
  - how many ads are there?
  - how does it load? (e.g. how does it fare on Google's Lighthouse score?)
  - how privacy-invasive is it/how many trackers are there?
  - is it painful to browse through? (e.g. does it hijack clicks and back buttons? how bad are the popups? cookie banners? etc)
- is it paywalled?
- how reputable is the site?
  - if the site is a content aggregator, how reputable is the user?
- is this a repost of something else? (there are entire websites "copying" other websites' content)

and so on.

The idea is to have a single service that is able to measure all of these "metrics" about the site/page/user in an automated way (i.e. without human moderation/correction), so that applications that link to arbitrary pages, or aim to analyze the web, can do so, page-by-page, by simply relying on this service.

The plan is to have a service with a pluggable architecture, where the plugins can measure individual "metrics", interact with and observe the page using playwright APIs, and can request related pages to be queued up/visited next so that we can measure "transitive" properties (at the moment, it's not quite clear how to let the plugins control the page queue, but it's clear that the queue needs to be limited to prevent infinite requests, that the metrics need to be returned as each page is being "measured", and that not all measurements need to be taken for each page, especially for the "subsequent" ones).
