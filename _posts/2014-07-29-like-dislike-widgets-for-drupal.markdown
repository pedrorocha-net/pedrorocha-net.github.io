---
layout: post
title:  "Like & Dislike widgets for Drupal"
date:   2014-07-29 00:00:00 -0300
---
![](https://www.drupal.org/files/styles/grid-3/public/project-images/like_and_dislike.png?itok=ko_HMfP1)

It sounds simple, but while Drupal has the awesome [Voting API](https://drupal.org/project/votingapi), with [Fiverstar](https://drupal.org/project/fivestar), [Vote Up/Down](https://drupal.org/project/vote_up_down) and many other voting like modules, we didn't have a "ready to use" solution for a "Like" widget, as we see on Facebook and many other social networks. Another issue is that many people avoid, but sometimes we do need the "Dislike" widget too.

While developing a video centered social network, this was a key part, and as i didn't find a stable and complete solution, i decided to create one, to play a little more with my new toys: [COOL module](https://www.drupal.org/project/cool)(you can read more at [OOP in Drupal 7: Cool module in practice](http://pedrorocha.net/en/2014/7/oop-in-drupal-7-cool-module-in-practice)), for an OOP Drupal development, and the combo [Coffeescript](http://coffeescript.org/) + [Grunt](http://gruntjs.com/).  
There isn't a better way to practice more and more with Coffeescript, test and understand more about Grunt, than creating a module and sharing it to receive feedback!

With this in mind, i created the [Like & Dislike module](https://www.drupal.org/project/like_and_dislike), that  provides the "like" and "dislike" widgets for contents inside Drupal, making it easiers to promote features as told before.

Technically speaking, the module provides 2 tags for Voting API, "like" and "dislike", working in a different way from [Vote Up/Down](https://www.drupal.org/project/vote_up_down), that is like a "plus or minus" approach. Likes are separate from Dislikes here.

### How it works

Like/Dislike widget works for any Entity Types and Bundles, and includes a settings page to specify on which bundles the user wants the widgets available(node types, comments, files, users, etc). By default, none of them are available, so it is needed to go at "/admin/config/search/like_and_dislike" and enable the wanted ones.

Well, if you have any suggestion or feedback, just drop it on the issue queue!

Hope it can be useful!