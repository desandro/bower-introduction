## npm

A large part of the success of Node JS as a platform is its package management, provided by npm.

So let's say you want to do some fun stuff with Twitter, you can do so! Because someone else has already built a Twitter client

https://github.com/AvianFlu/ntwitter

    var twitter = require('ntwitter');

That person was able to build the twitter client, because someone else already built an Ouath client

https://github.com/ciaranj/node-oauth

     var oauth = require('oauth');

A package that gets built upon another package gets to take advantage of the work done by a previous author. With each package that gets registered, the benefits start piling up recursively.

<!-- Ideally, any novice programmer can build an application with serious complexity, by utilizing packages that are d -->

Oh man, don't you want that? Right now our packages are fractured. Some are wrapped up in monolithic libraries, and some have CSS, and some are JS, and some need to be downloaded, and some need to be cloned and built.
