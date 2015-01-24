Hypothesis: More people would try Meteor if they could evaluate its front-end behavior first, independently of its server components.

# The Solution
I have released a package to Bower, and to Npm, called Mini-Meteor. This gives developers access to the Reactive capabilities of Meteor, including utilities for making reactive JS objects. It can be used as a replacement for Angular, Ember, or Backbone, though it will be most familiar to those accustomed to the Knockout library.

# The Docs
See http://manual.meteor.com for a focus on the reactive components of Tracker, which
are exposed under the Meteor global in Mini-Meteor. See http://docs.meteor.com for general
Meteor info.

# The Problem
*(Isn't it just like an engineer to jump right to the solution?)*

The decision to choose a JavaScript tool is a complicated one to make already. Since most tools out there assume you have a server already to speak REST to, developers don't know how to figure the Full Meteor into their comparisons. They may already have a substantial Rails investment, or can't run Mongo, and thus will not even look at Meteor to solve their front-end woes.

# The Design

Following the convention of MiniMongo, MiniMeteor exposes a Meteor global. This object's main method of interest is .run- an alias for Tracker.autorun. I thought Tracker was a little too vague, and autorun sounded a bit magical (concealing that the function *is* run immediately, for example). So Meteor.run runs the function you pass it, sets up dependencies, and reruns the function as those dependencies require.

I included ReactiveDict (renamed to ReactiveMap), and the ES5-property based ReactiveObject, but did not yet try to include much beyond that, for lack of a modular build system. See [The Future](#The Future) below..

Initially, I created a single JS file containing Tracker and its dependencies. I included underscore, but not JQuery, and put the 30kb minified file on a CDN, in Bower and in Npm as version 1.0.0.

In this version, you have no Mini-Mongo, router, Blaze templating, or HTTP. Still, this is enough to demonstrate lightning-fast DOM data-binding that beats the pants off of other frameworks in terms of less code, and fewer concepts to understand (and *no* conventions to memorize). It's the MVP/POC (pick your TLA) version. But the future holds bigger plans.

# The Future
* An automated build process
* A real module system, so it need not ship Unserscore or JQuery.
* A builder, like for JQuery UI, to create builds optionally with Blaze, MiniMongo, or other modules, ideally related to ISObuild
* It should include its own tests.
* MDG could support this, (or support my doing it-that'd be fine too)

Anyway, I'd love to hear your thoughts. The few Angular fans I showed Meteor code to wondered where all the complexity was, and I explained there just wasn't any!

Let's not forget those who are stuck with other servers, or a hard Front-End/Back-End split, as we labor on to take others on this Meteoric ride that we enjoy so much.
