# Leaving Kansas

This is the tl;dr-version (or merely a checklist) of a tutorial on how to set up *The Wonderful World of Ruby and Rails*™ on OS X.

##### What's inside?

All the steps, links and commands needed to start forking, modding and (prototypically) deploying Ruby applications.

(If you are looking for "a Rails tutorial" and think you are wrong: Rails is an application framework based on the programming language "Ruby". So: *every* Rails application is a Ruby application.)

##### How?

Just follow the steps, in the order they are written. Skip steps at your own peril. 



### 0. Prerequisites

- [Try Ruby](http://tryruby.org/)
- Update OS X to 10.6 Snow Leopard or 10.7 Lion. Sorry, no 10.5 Leopard.
- Get your mess of passwords organized with [KeePassX](http://www.keepassx.org/).
- Set up a backup with Time Machine. Yes, that might include going to the store and buying a harddrive. Do not continue without having a backup!
- Tattoo "search the interwebs!!11!" on the back of your hands. Whenever you read a word you do not understand, *look on the back of your hands!* [Stack Overflow](http://stackoverflow.com/) is the better Google for coding matters while [DuckDuckGo](http://duckduckgo.com) doesn't track you, has the better UI and some [nifty goodies](http://duckduckgo.com/tech.html).
- Find out how to write a tilde: `~`
- Do [5 minutes of shell basics](http://community.linuxmint.com/tutorial/view/100). Conviniently, the program to do so on OS X is already installed and called "Terminal".
- Install [iTerm2](http://iterm2.com/) for added shell convinience.
- Create a folder called `projects` in your home directory.
- Sign up for accounts on [Twitter](http://twitter.com), [Github](http://github.com) and [Heroku](http://heroku.com).
- Check out [Markdown](http://daringfireball.net/projects/markdown/) and install [Mou](http://mouapp.com/).
- Install [Sublime Text](http://www.sublimetext.com/2) or [Textmate](http://macromates.com/).


### 1. Install all the stuff

- [OS X GCC](https://github.com/kennethreitz/osx-gcc-installer/)

- [RVM (Ruby Version Manager)](https://rvm.io/)...

        $ curl -L get.rvm.io | bash -s stable

- …a newer ruby (this will take a while, go get some coffee)…

        $ rvm install 1.9.3
        $ rvm use 1.9.3
        
- …and let's set that to default while we're at it:

        $ rvm --default use 1.9.3

- The [Heroku Toolbelt](https://toolbelt.heroku.com/) (which conviniently includes [git](http://git-scm.com/)). Make sure to follow the "Getting started" part on that page too, including the ssh-key part. Your Github-Account also has a place for that ssh-key.


- [Rubygems](http://rubygems.org/pages/download). Instructions on how to install are in the included Readme within the .zip.

- [Bundler](http://gembundler.com/) is the first gem we need, it will install other packs of gems later:

        $ gem install bundler
        
    You just installed your first gem. Well done!

- [Homebrew](https://github.com/mxcl/homebrew/wiki/installation)


### 2. Fork and deploy a test app

- create a folder called `my_awesome_blog` in your `projects`-folder
- log into github
- go to <https://github.com/5v3n/karathy>
- [fork and clone it](http://help.github.com/fork-a-repo/) into `~/projects/my_awesome_blog`

- install needed gems with bundler:

        $ cd ~/projects/my_awesome_blog
        $ bundle install

- [create a new heroku app](https://devcenter.heroku.com/articles/creating-apps):

        $ heroku create --stack cedar

- push your app online:

        $ git push heroku master

- Open the URL in your browser.

Do you see your new blog? Congratulations #1!

### 3. Run the app locally on your machine

You don't have to push every change to Heroku to check it out. You can run a server on your very own machine.

- Install [thin](http://code.macournoyer.com/thin/):

        $ gem install thin
        
- go to your blog directory and start the server:

        $ cd ~/projects/my_awesome_blog
        $ thin start
        
- open [`0.0.0.0:3000`](http://0.0.0.0:3000) in your webbrowser

Do you see your local copy of the blog? Congratulations #2!


### 4. Mod it

- Open the file `~/projects/my_awesome_blog/templates/layout.rhtml` in your code editor
- Find line 23
- Change "My Blog" to "Hello World"
- Save the file
- [Check it out by updating your browser!](http://0.0.0.0:3000)

Do you see your changes? Congratulations #3!

Have a look at the terminal window where you started thin. You can see the requests your local server is answering.


### 5. commit and push changes

        $ git commit -am "Effyeah, my first commit evah!"
        $ git push heroku master
        $ git push origin master

Do you see your changes on your deployed version of the blog and on your github repo? Congratulations #4!

### You did it! Now take a break…

…and pat yourself on the back for next couple hours. Bold move, bro!

That also means that this tutorial worked out. Tell your friends about it.



### Then: have fun…

For example:

- Start blogging (you now have your own blog, you know?)
- Take a long walk (always helps)
- Do lots of reading about the tools you are using
- Find your local [Ruby usergroup](http://www.rubyusergroups.org/) or [Railsgirls group](http://railsgirls.com/). If there is none, start one!
- Find the nearest BarCamp on Ruby and Rails. If there is none, start one!
- Check out out how to map your new blog to your own domain
- Drink more water
- Make a branch of your blog, change the design, later merge it to your master branch
- Learn [HAML](http://haml-lang.com/) and [SASS](sass-lang.com)
- try to [get a rails app running](http://railsapps.github.com/rails-heroku-tutorial.html)
- Try [Pow](http://pow.cx/)
- [Learn more shell](http://cli.learncodethehardway.org/book/)
- [Learn more Ruby](http://rubymonk.com/)
- [Learn some JavaScript](http://www.codecademy.com/)
- Don't mention the war!

### …get [more good advice](http://goodfuckingdesignadvice.com/)…

### …and [give feedback](http://twitter.com/filtercake).

---

###### Credits

A very special thanks to [5v3n](https://github.com/5v3n).

Also thanks to the [*Hamburg Ruby Community*](http://hamburg.onruby.de/), especially [blindgaenger](https://github.com/blindgaenger) and [the mindmatters crew](https://github.com/mindmatters).

---
### Further reading

- [Git](http://rogerdudler.github.com/git-guide/), [Git](http://nfarina.com/post/9868516270/git-is-simpler) and Git. Really, you can never read enough about git.
- [Hacker News](http://news.ycombinator.com/)
- [Getting Real](http://gettingreal.37signals.com/toc.php)


(more coming soon.)




