#Setting up a good development environment on a Mac


###Install OSX Yosemite
* OK Wipe your hard drive by powering on your Mac while holding down the Option key, select the OSX USB drive, go to Utilities > Disk Utility, and format your hard disk in Mac OSX (Journaled) format.
* Gjorde det. (Don't sign in with your Apple ID right away.)


###Xcode:
* OK Download Xcode from the App Store. It will take a while so do this first.
* OK Install all updates for your OS etc.
* OK Get Xcode's command line tools to get GCC, git and other goodies.
* OK Once it downloads do ````xcode-select --install```` to get the command line tools.



###System preferences:
While Xcode takes forever to download
OK
* *Dock*: Shrink the dock. 
* *Mission Control*: Set up hot corners for mission control and show desktop.
* *Displays*: Arrangement-> uncheck mirror displays, arrange second monitor to your liking. 
* *Trackpad*: Tap to click, X scroll direction, X swipe between pages 

###Fix (some) Privacy Intrusions
Inte gjort
Apple is just going to send your data to fucking Microsoft of all places if you don't do this.
* Follow the instructions at [Fix Mac OSX](https://fix-macosx.com) You can even do this automatically by running a Python script, but we aren't ready for that yet.

### Get Rid of Apple's stupid shit programs
OK
In a Terminal window, enter: 

````sudo chflags hidden /Applications/Bullshit.app````
(Replace "Bullshit" with Maps, for example.)
 
This will hide Apple's perplexingly awful default programs that are inadvisable to delete outright.

I also deleted the stock alerts in the notifications panel.


###Homebrew
OK
````
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
==> This script will install:
/usr/local/bin/brew
/usr/local/Library/...
/usr/local/share/man/man1/brew.1
````

* Homebrew will ask you to download Xcode command line tools. When finished, run: 

````
OK brew doctor
Ok brew update
````
### Rbenv, Ruby, and Rails
Much of this follows some of the instructions on [GoRails](https://gorails.com/setup/osx/10.10-yosemite).

````
OK brew install rbenv ruby-build
````

````
OK echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
Ok source ~/.bash_profile
````

````
OK rbenv install 2.1.3
OK rbenv global 2.1.3
OK gem install rails
OK rbenv rehash
````

#####Check thyself before you wreck thyself:
```` ruby -v ```` should give you 2.1.3 and ````rails --version```` should output 4.1.6
Min output: ruby 2.1.3p242 (2014-09-19 revision 47630) [x86_64-darwin14.0]
Min output: Rails 4.2.1


###Git and Github
* Git config:
OK
````
git config --global color.ui true
git config --global user.name "First Last"
git config --global user.email "flast@yo.com"
````
Set up 2-factor authentication on github.

###Generate SSH keys:
* In Terminal:
OK
````
cd ~/.ssh
ssh-keygen -t rsa -C "you@yo.com"
#don't enter a passphrase
pbcopy < ~/.ssh/id_rsa.pub
````
* Paste the entire resulting RSA key to [Github](https://github.com/settings/ssh).

````ssh -T git@github.com```` checks that this actually worked.

###Postgresql
skippade detta
````
brew install postgresql
ln -sfv /usr/local/opt/postgresql/*plist ~/Library/LaunchAgents

launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist


````
###Firefox
* Get the [developer edition!](https://www.mozilla.org/en-US/firefox/developer/)
nope, chrome

###Sublime Text 3:
OK
* [Download](http://www.sublimetext.com/)
* [Package control](https://sublime.wbond.net/installation)
* Emmet
* Sublime Linter
* Set up subl command line shortcut: 
OK
````ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl````


* Some settings to get you started:
ok
````
{
	"bold_folder_labels": true,
	"color_scheme": "Packages/Color Scheme - Default/Solarized (Light).tmTheme",
	"fade_fold_buttons": false,
	"highlight_line": true,
	"highlight_modified_tabs": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"line_padding_bottom": 1,
	"line_padding_top": 1,
	"word_wrap": true,
	"font_face": "AnonymousPro",
	"font_size": 18
}
````
###iTerm2:
* ok [Download](http://www.iterm2.com/#/section/home)
* skippade det I highly recommend a [heads-up terminal](http://ivanvillareal.com/osx/setup-iterm2-to-behave-like-guake/) for running servers 
* ok and some color schemes such as [solarized](http://iterm2colorschemes.com/)

###Chrome:
att göra Set up gmail, drive, and 2-factor authentication
Suggested Extensions:

*JSONView
*Pesticide
*Live Reload

###Python, pip and virtualenv

`````
ok brew install python # python comes with OSX but this installs pip and some other stuff
ok pip install virtualenv

ok pip install virtualenvwrapper
Installing collected packages: pbr, six, argparse, stevedore, virtualenv-clone, virtualenvwrapper




  Running setup.py install for virtualenv-clone
    Installing virtualenv-clone script to /usr/local/bin

Successfully installed argparse-1.3.0 pbr-0.10.8 six-1.9.0 stevedore-1.4.0 virtualenv-clone-0.2.5 virtualenvwrapper-4.5.0

`````

###Mongodb
* Installation with homebrew:

````	
ok brew install mongodb
````
* To start mongodb server, run ```` mongod ```` 
* For a shell, just type ```` mongo ```` 

###Vim
* inte än get yourself a nice vim distro like spf13 

````curl https://j.mp/spf13-vim3 -L > spf13-vim.sh && sh spf13-vim.sh)````


###Other Apps:
* Dash
* Spectacle
* Skype
* Spider Oak (fuck Dropbox for hiring Condoleeza Rice. Seriously, anyone without the war in Iraq and warrantless wiretapping on their resume would have been better.)
* Tor 
* OnionShare 
* Android Studio
* Pocket
* Mou
* Twitter
* Libre Office
* 


### Installerade pyproj
gjorde dessa steg:
clone github repo or download source release at http://python.org/pypi/pyproj.
python setup.py build
python setup.py install (with sudo if necessary).
To test, run python -c "import pyproj; pyproj.test()"
(test passed)

### installerade google app engine sdk
Google App Engine Launcher finns nu i /Applications
Symbolic links in /usr/local/bin have been created for the following commands:
_php_runtime.py _python_runtime.py api_server.py appcfg.py backends_conversion.py bulkload_client.py bulkloader.py dev_appserver.py download_appstats.py endpointscfg.py gen_protorpc.py google_sql.py php_cli.py remote_api_shell.py run_tests.py wrapper_util.py 
In addition, /usr/local/google_appengine points to the SDK.

* not från django-nonrel:
* Since Google App Engine runs your Python code from within a sandbox, some standard Python installation methods are unavailable. For example, you cannot install django or other Python modules in your system’s Python library. All code for your app must be installed in your project directory.

### Installerade Mysql
 Mac OS X ver. 10.9 (x86, 64-bit), DMG Archive
 
 Installerade Mysqlclient:
 Successfully installed mysqlclient-1.3.6
 Lade till detta i /etc/paths:
 /usr/local/mysql/bin
 (efter rekommendation här http://stackoverflow.com/a/12621216)
 
 ### installerade Django
 pip install django
Collecting django
  Downloading Django-1.8-py2.py3-none-any.whl (6.2MB)
    100% |################################| 6.2MB 46kB/s
Installing collected packages: django

Successfully installed django-1.8


Gjorde denna symlänk:
sudo ln -s /usr/local/mysql/lib/libmysqlclient.18.dylib /usr/lib/libmysqlclient.18.dylib

efter att ha fått detta fel:
"django.core.exceptions.ImproperlyConfigured: Error loading MySQLdb module: dlopen(/usr/local/lib/python2.7/site-packages/_mysql.so, 2): Library not loaded: libmysqlclient.18.dylib
  Referenced from: /usr/local/lib/python2.7/site-packages/_mysql.so
  Reason: image not found"
  
 Lösningen fanns här: http://codingtip.blogspot.se/2014/01/error-loading-mysqldb-module-image-not.html

### installerade pytz
https://docs.djangoproject.com/en/1.8/topics/i18n/
Successfully installed pytz-2015.2

### bower
npm install -g bower
