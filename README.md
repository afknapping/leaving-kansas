# Leaving Kansas

How to set up *The Wonderful World of Ruby and Rails*™ on OS X.

Supported: 10.6 Snow Leopard and 10.7 Lion. Sorry, **no 10.5 Leopard**.

- You should have [tried Ruby](http://tryruby.org/).

- [Stack Overflow](http://stackoverflow.com/) is the better Google for coding matters while [DuckDuckGo](http://duckduckgo.com) doesn't track you, has the nicer UI and some [nifty goodies](http://duckduckgo.com/tech.html).  Tattoo **"search the interwebs!!11!"** on the back of your hands. Whenever you read a word you do not understand, **look on the back of your hands!** 


- If you've never used the terminal before, find out how to write a tilde (`~`) and do [5 minutes of shell basics](http://community.linuxmint.com/tutorial/view/100).

- Install [1password](https://agilebits.com/onepassword/mac) and [its browser extensions](http://help.agilebits.com/1Password3/extension_install_update.html).

- [Set up your ssh-key](https://help.github.com/articles/generating-ssh-keys).

- Sign up for accounts on [Twitter](http://twitter.com), [Github](http://github.com) and [Heroku](http://heroku.com).


## 1. Prepare and Install

- ### OS X

  Update to latest version of 10.6 Snow Leopard or 10.7 Lion.
  
  **Set up a Backup with Time Machine!!11!** Yes, that might include going to the store and buying a harddrive. Do not continue without having a backup!

- ### [XCode](https://developer.apple.com/xcode/) >= 4.3

  It's huge. This will take some time to download.

  We also need the Command Line Tools for Xcode from within Xcode's Download preferences:

  ![](http://dl.dropbox.com/u/2146484/images/leaving-kansas/xcode-cli-install.png)

   *Note:* It would be **much** lighter to use [OS X GCC](https://github.com/kennethreitz/osx-gcc-installer/), but [that is missing `xcodebuild`](https://github.com/mxcl/homebrew/issues/10960), so we need the 5 gig download of XCode through the Mac App Store to install Homebrew without errors :(

- ### Finder

  Make hidden files visible by pasting this into the terminal

        $ defaults write com.apple.Finder AppleShowAllFiles YES
        
  and restart the finder:

  ![](http://dl.dropbox.com/u/2146484/images/leaving-kansas/finder-restart.png)
  
  Then activate keyboard control for system dialogues:
  
  ![](http://dl.dropbox.com/u/2146484/images/leaving-kansas/finder-keyboard-control.png)

- ### Tools

  Check out [Markdown](http://daringfireball.net/projects/markdown/) and install [Mou](http://mouapp.com/). Also install  [iTerm2](http://iterm2.com/) and [Sublime Text](http://www.sublimetext.com/2).


- ### [Homebrew](https://github.com/mxcl/homebrew/wiki/installation)

  is currently installed by doing:

        $ /usr/bin/ruby -e "$(/usr/bin/curl -fsSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"

  Then do
  
        $ brew doctor
      
  which will tell you to do

        $ sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer
      
  after which  another
  
        $ brew doctor
      
  should happily announce that:
  
        Your system is raring to brew.    

- ### [git](http://git-scm.com/)

  We want to uninstall the git version that came with OS X and install an up-to-do version with homebrew:
	
        $ which git
	    
  will output (on Lion at least)
  
        /usr/bin/git
        
  so we need to do
  		
        $ sudo rm -rf /usr/bin/git

  to remove the old git and
  
        $ brew install git
         
  to install the new version. Now you can do
  
        $ git --version

  and

        $ which git
       
       
         

- ### [rbenv](https://github.com/sstephenson/rbenv) + [rubybuild]()


        $ brew install rbenv
        $ brew install ruby-build
       
  We now need to edit the bash profile which doesn't exist on a freh system. Do:
  
        $ touch ~/.bash_profile
      
      
  and paste the line

        eval "$(rbenv init -)"
    
  and restart the terminal.
  
        $ rbenv versions
     
  shows nothing. We need to install a Ruby into rbenv by doing:


        $ rbenv install 1.9.3-p194
        
  This may take a while. Then do:
  
        $ rbenv rehash
 	 
  Now

        $ rbenv versions
  	 
  should output:
  
        1.9.3-p194

  Do
  	 
        $ rbenv global 1.9.3-p194
        $ rbenv versions
        $ rbenv version


- ## [Bundler](http://gembundler.com/)
  
  Do:
  
        $ gem install bundler
        
  and restart the terminal. *Note:* if you get a permission error, you must do `sudo gem install bundler` –– same with other gems.
        

- ## [the heroku cli](http://github.com/heroku/gem)

        $ gem install heroku

  and restart the terminal. Then do:

        $ heroku login





## 2. Fork and deploy a test app

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

## 3. Run the app locally on your machine

You don't have to push every change to Heroku to check it out. You can run a server on your very own machine.

- Install [thin](http://code.macournoyer.com/thin/):

        $ gem install thin
        
- go to your blog directory and start the server:

        $ cd ~/projects/my_awesome_blog
        $ thin start
        
- open [`0.0.0.0:3000`](http://0.0.0.0:3000) in your webbrowser

Do you see your local copy of the blog? Congratulations #2!


## 4. Mod it

- Open the file `~/projects/my_awesome_blog/templates/layout.rhtml` in your code editor
- Find line 23
- Change "My Blog" to "Hello World"
- Save the file
- [Check it out by updating your browser!](http://0.0.0.0:3000)

Do you see your changes? Congratulations #3!

Have a look at the terminal window where you started thin. You can see the requests your local server is answering.

Now commit and push:

        $ git commit -am "Effyeah, my first commit evah!"
        $ git push heroku master
        $ git push origin master

Do you see your changes on your deployed version of the blog and on your github repo? Congratulations #4!

## You did it! Now take a break,…

…get a beer and pat yourself on the back for next couple hours. Bold move, bro!

That also means that this tutorial worked out. [Tell your friends about it](the long tweet thing...).



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
- Try to [get a rails app running](http://railsapps.github.com/rails-heroku-tutorial.html)
- Try [Pow](http://pow.cx/)
- [Learn more shell](http://cli.learncodethehardway.org/book/)
- [Learn more Ruby](http://rubymonk.com/)
- [Learn some JavaScript](http://www.codecademy.com/) –– or if you know JavaScript, check out [CoffeeScript](http://coffeescript.org)
- get [more good advice](http://goodfuckingdesignadvice.com/)…
- …and [give feedback](http://twitter.com/filtercake).

---

### Credits

A very special thanks to [5v3n](https://github.com/5v3n). This doc originated as part of documentation for [The Ratpack Workshop](link).

Also thanks to the [*Hamburg Ruby Community*](http://hamburg.onruby.de/), especially [blindgaenger](https://github.com/blindgaenger) and [the mindmatters crew](https://github.com/mindmatters).

HT to  [Ben](http://twitter.com/salzig) for the hint on enabling keybard control for all system dialogues.

---
### Further reading and links

- [Git](http://rogerdudler.github.com/git-guide/), [Git](http://nfarina.com/post/9868516270/git-is-simpler) and [Git](http://git-scm.com/video/what-is-version-control). Really, you can never know enough about [git](http://blip.tv/scott-chacon/git-talk-4113729) and [git](http://importantshock.wordpress.com/2008/08/07/git-vs-mercurial/).
- [How do RVM and RBENV actually work?](http://stackoverflow.com/questions/9394338/how-do-rvm-and-rbenv-actually-work)

(more coming. maybe.)

###### TODO

- http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/ -- https://github.com/nvie/gitflow/wiki/Installation
- https://github.com/aanand/git-up
- https://github.com/kennethreitz/legit

- https://github.com/scoz/rbenv-rehash
