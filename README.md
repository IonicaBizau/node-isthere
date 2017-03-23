
[![is-there](http://i.imgur.com/ZHzpvvE.png)](#)

# is-there

 [![Support me on Patreon][badge_patreon]][patreon] [![Buy me a book][badge_amazon]][amazon] [![PayPal][badge_paypal_donate]][paypal-donations] [![Travis](https://img.shields.io/travis/IonicaBizau/node-is-there.svg)](https://travis-ci.org/IonicaBizau/node-is-there/) [![Version](https://img.shields.io/npm/v/is-there.svg)](https://www.npmjs.com/package/is-there) [![Downloads](https://img.shields.io/npm/dt/is-there.svg)](https://www.npmjs.com/package/is-there)

> Check if a file or directory exists in a given path.

## Why? `fs.exists` already does the job!

Because `fs.exists` and `fs.existsSync` ~~will be~~ are deprecated and in some cases we still need them!

> `fs.exists()` is an anachronism and exists only for historical reasons. There should almost never be a reason to use it in your own code.
> In particular, checking if a file exists before opening it is an anti-pattern that leaves you vulnerable to race conditions: another process may remove the file between the calls to `fs.exists()` and `fs.open()`. Just open the file and handle the error when it's not there.
> **`fs.exists()` will be deprecated.**
> <sup>([Source](http://nodejs.org/api/fs.html#fs_fs_exists_path_callback), emphasis added)</sup>


## :cloud: Installation

```sh
$ npm i --save is-there
```


## :clipboard: Example



```js
// Dependencies
var IsThere = require("is-there");

// Paths to test
var paths = [
    // exist
    "dir"
  , "dir/another"
  , "dir/another/file"
  , "dir/file"
  , "file"
  , "file.ext"
    // don't exist
  , "foo"
  , "foo/bar"
  , "foo.bar"
  , "foo/bar.foo"
].map(function (c) {
    return __dirname + "/contents/" + c;
});

// Sync
console.log("> Testing sync method.");
paths.forEach(function (c) {
    console.log("> %s %s", c, IsThere(c) ? "exists" : "doesn't exist");
});


console.log("> Testing async method.");
function doSeq(i) {
    i = i || 0;
    var cPath = paths[i];
    if (!cPath) { return; }
    IsThere(cPath, function (exists) {
        console.log("> %s %s", cPath, exists ? "exists" : "doesn't exist");
        doSeq(i + 1);
    });
}

doSeq();
```

## :question: Get Help

There are few ways to get help:

 1. Please [post questions on Stack Overflow](https://stackoverflow.com/questions/ask). You can open issues with questions, as long you add a link to your Stack Overflow question.
 2. For bug reports and feature requests, open issues. :bug:
 3. For direct and quick help from me, you can [use Codementor](https://www.codementor.io/johnnyb). :rocket:


## :memo: Documentation


### isThere

Checks if a file or directory exists on given path.
Use without the new keyword.

#### Params
- **String** `path`: The path to the file or directory.
- **Function** `callback`: The callback function called with a boolean value representing if the file or directory exists. If this parameter is not a
function, the function will run synchronously and return the value.

#### Return
- **isThere|Boolean** The `isThere` function if the `callback` parameter was provided, otherwise a boolean value indicating if the file/directory
exists or not.

### `directory(path, callback)`
Checks if the path exists and it is a directory.

#### Params
- **String** `path`: The path to the directory.
- **Function** `callback`: The callback function called with a boolean value representing if the directory exists. If this parameter is not a
function, the function will run synchronously and return the value.

#### Return
- **isThere|Boolean** The `isThere` function if the `callback` parameter was provided, otherwise a boolean value indicating if the directory exists or not.

### `file(path, callback)`
Check if the path exists and it is a file.

#### Params
- **String** `path`: The path to the file.
- **Function** `callback`: The callback function called with a boolean value representing if the file exists. If this parameter is not a
function, the function will run synchronously and return the value.

#### Return
- **isThere|Boolean** The `isThere` function if the `callback` parameter was provided, otherwise a boolean value indicating if the file exists or not.



## :yum: How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].


## :sparkling_heart: Support my projects

I open-source almost everything I can, and I try to reply everyone needing help using these projects. Obviously,
this takes time. You can integrate and use these projects in your applications *for free*! You can even change the source code and redistribute (even resell it).

However, if you get some profit from this or just want to encourage me to continue creating stuff, there are few ways you can do it:

 - Starring and sharing the projects you like :rocket:
 - [![PayPal][badge_paypal]][paypal-donations]—You can make one-time donations via PayPal. I'll probably buy a ~~coffee~~ tea. :tea:
 - [![Support me on Patreon][badge_patreon]][patreon]—Set up a recurring monthly donation and you will get interesting news about what I'm doing (things that I don't share with everyone).
 - **Bitcoin**—You can send me bitcoins at this address (or scanning the code below): `1P9BRsmazNQcuyTxEqveUsnf5CERdq35V6`

    ![](https://i.imgur.com/z6OQI95.png)

Thanks! :heart:


## :dizzy: Where is this library used?
If you are using this library in one of your projects, add it in this list. :sparkles:


 - [`a-csv`](https://github.com/jillix/a-csv) (by jillix)—A lightweight CSV parser.
 - [`ajs`](https://github.com/IonicaBizau/ajs#readme)—Asynchronous templating in Node.js
 - [`ali-oss-extra`](https://github.com/jackytck/ali-oss-extra#readme) (by Jacky Tang)—Extend the official ali-oss with more convenient methods, such as listing, syncing or deleting a directory, put or delete a list of files etc.
 - [`artstack-downloader`](https://github.com/IonicaBizau/artstack-downloader)—Download artworks from your following users.
 - [`be-goods`](https://github.com/gulpsome/be-goods#readme) (by Orlin M Bozhinov)—let there be beverage goods
 - [`better-history`](https://github.com/jiacai2050/better-history) (by Jiacai Liu)—💡 Get a better sense of browsing history via Chrome/Firefox
 - [`bible`](https://github.com/BibleJS/BibleApp)—Read the Holy Bible via the command line.
 - [`blah`](https://github.com/IonicaBizau/blah)—A command line tool to optimize the repetitive actions.
 - [`bower-license-webpack-plugin`](https://github.com/blattmann/bower-license-webpack-plugin#readme) (by S K)—Outputs licenses from 3rd party libraries to a file
 - [`bowerrc`](https://github.com/mithun/bowerrc#readme) (by Mithun Ayachit)—Switch between different .bowerrc files
 - [`caipi`](https://github.com/CaipiLabs/caipi#readme) (by Nathan Braun)—Caipi reactor - Isomorphic CMS based on ES6+React+webpack+mongo+etc
 - [`cdnjs-importer`](https://github.com/cdnjs/cdnjs-importer)—Easy way to import a library into CDNJS.
 - [`cecil`](https://github.com/MikeyBurkman/Cecil#readme) (by Michael Burkman)—For running single-file NodeJS scripts with external dependencies
 - [`confetti-cli`](https://github.com/andreamangano/confetti-cli#readme) (by Andrea Mangano)—Command line interface for Confetti, a tool for enriching your online slide decks.
 - [`emartech-node-sass-json-importer`](https://github.com/emartech/node-sass-json-importer#readme)—Allows importing json in sass files parsed by node-sass.
 - [`engine-app`](https://github.com/jillix/engine-app#readme) (by jillix)—Engine app related helper functions.
 - [`engine-composition-crud`](https://github.com/jillix/engine-composition-crud#readme) (by jillix)—The default module for creating, reading, updating and deleting Engine instances.
 - [`engine-tools`](https://github.com/jillix/engine-tools) (by jillix)—Engine Tools library and CLI app.
 - [`f-watcher`](https://github.com/IonicaBizau/node-fwatcher)—Watch files for changes.
 - [`find-file-in-dirs`](https://github.com/IonicaBizau/find-file-in-dirs#readme)—Find a file in different directories.
 - [`firstant2gradle`](https://github.com/FIRST-Team-2557-The-SOTABots/FIRSTAntToGradle#readme) (by Philip Rader)—Automatically converts an Ant build system to Gradle for FIRST Robotics Competition teams
 - [`fontify`](https://github.com/YoussefKababe/fontify#readme) (by Youssef Kababe)—Copy font files from node_modules folder
 - [`friendly-typed-css-modules`](https://github.com/TheMallen/typed-css-modules#readme) (by themallen)—Creates .d.ts files from CSS Modules .css files
 - [`fwatcher`](https://github.com/IonicaBizau/node-fwatcher)—Watch files for changes.
 - [`gd-cli`](https://npmjs.com/package/gd-cli) (by Sylvain Baronnet)—GD Command Line Interface
 - [`generator-arwen`](https://github.com/jasonvillalon/generator-arwen) (by Jason Villalon)—Generator Atomic Restify Web NodeJS
 - [`generator-atomus`](https://bitbucket.org/generator-react-component/atomus-cli) (by Jason Villalon)—Generator React Components
 - [`generator-catena`](https://github.com/damirkusar/catena-generator#readme) (by Damir Kusar)—Yeoman generator for Meteor and AngularJS
 - [`generator-catena-angular-meteor-bootstrap`](https://github.com/damirkusar/generator-catena-angular-meteor-bootstrap#readme) (by Damir Kusar)—Yeoman generator for Meteor and AngularJS
 - [`generator-catena-angular-meteor-material`](https://github.com/damirkusar/catena-generator#readme) (by Damir Kusar)—Yeoman generator for Meteor and AngularJS
 - [`generator-leptir`](https://github.com/damirkusar/leptir-generator#readme) (by Damir Kusar)—Yeoman generator for AngularJS with gulp, browserify, bootstrap, SCSS, angular-ui, angular-translate, karma, jasmine and ftp deployment
 - [`generator-leptir-angular-bootstrap`](https://github.com/damirkusar/generator-leptir-angular-bootstrap#readme) (by Damir Kusar)—Yeoman generator for AngularJS with gulp, browserify, bootstrap, SCSS, angular-ui, angular-translate, karma, jasmine and ftp deployment
 - [`generator-leptir-angular-material`](https://github.com/damirkusar/generator-leptir-angular-material#readme) (by Damir Kusar)—Yeoman generator for AngularJS with gulp, browserify, Angular-Material, SCSS, angular-ui, angular-translate, karma, jasmine and ftp deployment
 - [`generator-morf`](https://github.com/p1100i/generator-morf) (by p1100i)—A yeoman generator to bootstrap a finely tuned project [node, angular], w/ Grunt.
 - [`gif-cli`](https://github.com/IonicaBizau/gif-cli)—Gif animations in your terminal!
 - [`git-issues`](https://github.com/softwarescales/git-issues) (by Gabriel Petrovay)—Git issues extension to list issues of a Git project
 - [`git-stats`](https://github.com/IonicaBizau/git-stats)—Local git statistics including GitHub-like contributions calendars.
 - [`git-stats-importer`](https://github.com/IonicaBizau/git-stats-importer)—Imports your commits from a repository into git-stats history.
 - [`gpm`](https://github.com/IonicaBizau/gpm)—npm + git = gpm - Install NPM packages and dependencies from git repositories.
 - [`grunt-md5symlink`](https://github.com/p1100i/grunt-md5symlink) (by peters)—Create symlink by the md5 of given files.
 - [`gulp-app-build-tasks`](https://github.com/jimmyfortinx/gulp-app-build-tasks) (by Jimmy Fortin)—This module will add standard gulp tasks to start building a web application.
 - [`gulp-common-build-tasks`](https://github.com/jimmyfortinx/gulp-common-build-tasks) (by Jimmy Fortin)—You can found in this library some utilities and tasks that can be shared between multiple gulp's build processes.
 - [`hal-rc`](https://github.com/gulpsome/hal-rc#readme)—*hints-and-lints rc*
 - [`heroku-container-registry`](https://github.com/heroku/heroku-container-registry#readme) (by Hunter Loftis)—Use containers to build and deploy Heroku apps
 - [`heroku-container-tools`](https://github.com/heroku/heroku-container-tools#readme) (by Hunter Loftis)—Use containers to build and deploy Heroku apps
 - [`heroku-docker`](https://github.com/heroku/heroku-container-tools#readme) (by Hunter Loftis)—DEPRECATED: use heroku-container-tools
 - [`hg-plus`](https://github.com/jdalrymple/node-hg-plus#readme) (by Justin Dalrymple)—A Mercurial client for Node
 - [`idea`](https://github.com/IonicaBizau/idea)—A lightweight CLI tool and module for keeping ideas in a safe place quick and easy.
 - [`image-to-ascii-cli`](https://github.com/IonicaBizau/image-to-ascii-cli#readme)—View images in text format, in your terminal.
 - [`is-git-check`](https://npmjs.com/package/is-git-check) (by Dominik Winter)—Simple module to check whether a directory is a git repository or not
 - [`jisc_build`](https://github.com/gooii/jisc_build#readme) (by Martin Wood-Mitrovski)—Shared jisc build scripts and configuration for JJA and JHT
 - [`joomlascan`](https://github.com/robations/joomlascan#readme)—Searches paths for Joomla installations and outputs the installed version number.
 - [`kaomojify`](https://github.com/kokororin/kaomojify#readme) (by kokororin)—Kaomojify Javascript code
 - [`kaomojify-webpack-plugin`](https://github.com/kokororin/kaomojify-webpack-plugin#readme) (by kokororin)—convert your built JavaScript code to Japanese kawaii kaomoji(かわいい顔文字)
 - [`kotori-webpack-plugin`](https://github.com/kokororin/kotori-webpack-plugin#readme) (by kokororin)—Yet another webpack plugin
 - [`le-serf`](https://github.com/1vasari/le-serf#readme) (by Nathan McCallum)—Your trusty assistant in your Lacuna Expanse misadventures!
 - [`low-cli`](https://github.com/lowjs/low-cli#readme) (by Jeremy Rylan)—undefined
 - [`matanza`](https://github.com/fredybawa/matanza#readme) (by Alfredo Monteiro)—Matanza =======
 - [`memories`](https://github.com/data-doge/memories#readme) (by data-doge)—cli for a timestamped markdown journal
 - [`minipod`](https://github.com/DonYang/minipod#readme) (by DonYang)—Customize cocoapods specs for just you need.
 - [`node-dynamo`](https://github.com/louislarry/node-dynamo#readme) (by Louis Larry)—Easily create and recreate dynamodb tables and sample data. This package provides the cli and sdk.
 - [`node-sass-json-importer`](https://github.com/Updater/node-sass-json-importer#readme)—Allows importing json in sass files parsed by node-sass.
 - [`npm-interlink`](https://github.com/orlin/npm-interlink#readme) (by Orlin M Bozhinov)—because `npm link ...` can be tedious
 - [`panes`](https://github.com/joelchu/panes#readme) (by Joel Chu)—PANES.JS core lib and cli http://panesjs.com
 - [`parent-search`](https://github.com/IonicaBizau/node-parent-search)—Search files and folders in parent directories.
 - [`payname`](https://npmjs.com/package/payname) (by Florian CHEVALLIER)—Module nodejs permettant d'intégrer Payname à vos projets
 - [`ramda-cli`](https://github.com/raine/ramda-cli#readme) (by Raine Virta)—A command-line tool for processing JSON with Ramda and LiveScript
 - [`reindex-cli`](https://github.com/reindexio/reindex-cli#readme) (by Reindex)—CLI interface for Reindex
 - [`singular_sake`](https://npmjs.com/package/singular_sake) (by Juan Castro Fernández)—Singular MVC PHP Framework command line tool
 - [`sourcegate`](https://github.com/orlin/sourcegate#readme) (by Orlin M Bozhinov)—have any json object you want
 - [`sp-load`](https://github.com/pavel06081991/sp-load#readme) (by pavel06081991)—Modules loader. No lots of require calls on the top of files. On demand modules loading. Local modules.
 - [`tester-init`](https://github.com/IonicaBizau/tester-init#readme)—Init tests for tester.
 - [`tilda-init`](https://github.com/IonicaBizau/tilda-init#readme)—Init cli applications.
 - [`tithe`](https://github.com/IonicaBizau/tithe)—Organize and track the tithe payments.
 - [`typed-css-modules`](https://github.com/Quramy/typed-css-modules#readme) (by quramy)—Creates .d.ts files from CSS Modules .css files
 - [`unity-asset-sync`](https://npmjs.com/package/unity-asset-sync) (by Chris Jaynes)—Allows safe, effective sharing of code between Unity projects.
 - [`unity-link`](https://npmjs.com/package/unity-link) (by Chris Jaynes)—A utility for Unity developers to symlink scripts into their Assets folders. Useful for library development.
 - [`uturi-caching`](https://npmjs.com/package/uturi-caching)—undefined
 - [`valkctl`](https://npmjs.com/package/valkctl)—simple command wrapper
 - [`valkyrja`](https://github.com/freialib/valkyrja#readme) (by srcspider)—the deploy tool
 - [`vimhelp`](https://github.com/thinca/node-vimhelp) (by thinca)—Show vim help.
 - [`viur-ignite-css`](http://ignite.viur.is) (by VIUR)—Core of VIUR Ignite - a less framework
 - [`viur-ignite-html`](https://github.com/viur-ignite/viur-ignite-html#readme) (by VIUR)—Simple Template Render | Extension of viur-ignite-css
 - [`viur-ignite-icons`](https://github.com/viur-ignite/viur-ignite-icons#readme) (by VIUR)—Icon libary | Extension of viur-ignite-css
 - [`viur-ignite-js`](https://github.com/viur-ignite/viur-ignite-js#readme) (by VIUR)—Javascript Libary | Extension of viur-ignite-css
 - [`web-term`](https://github.com/IonicaBizau/web-term)—A full screen terminal in your browser.
 - [`wml`](https://github.com/wix/wml#readme) (by dutzi)—Replaces npm link with something that actually works!
 - [`zow`](https://github.com/zowley/zow#readme) (by Jeremy Rylan)—undefined

## :scroll: License

[MIT][license] © [Ionică Bizău][website]

[badge_patreon]: http://ionicabizau.github.io/badges/patreon.svg
[badge_amazon]: http://ionicabizau.github.io/badges/amazon.svg
[badge_paypal]: http://ionicabizau.github.io/badges/paypal.svg
[badge_paypal_donate]: http://ionicabizau.github.io/badges/paypal_donate.svg
[patreon]: https://www.patreon.com/ionicabizau
[amazon]: http://amzn.eu/hRo9sIZ
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(https%3A%2F%2Fionicabizau.net)&year=2015#license-mit
[website]: https://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md
