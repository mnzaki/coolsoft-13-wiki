## GUC Proxy Setup
For Git Bash and Ubuntu users, you can create a nice little Bash function. Open a **new** shell window, then:
```sh
# use your favorite editor to open .bashrc
gedit .bashrc
```
Now add this to `.bashrc` but change the username and password below
```sh
function gucproxy {
  export http_proxy=http://your.guc.username:yourGUCpassword@50.0.0.5:8080
  export https_proxy=$http_proxy
}
```
Now save the file and close the shell. In any *new* shell you open, there will now be a command called `gucproxy` which you can call and it will set the proxy for the current shell, and for the current shell *only*.

## Git
Some basics:
```sh
# set your name and email
git config --global user.name "Mina Nagy"
git config --global user.email "someone@somewhere.com"
# turn on colors
git config --global color.ui auto
git config --global color.diff auto
git config --global color.status auto
git config --global color.interactive auto
git config --global color.branch auto
```
Set your editor (the text editor that pops up when you `git commit`)  
#### For Ubuntu:
**Nano**:  
```sh
git config --global core.editor nano
```
**GEdit**:  
```sh
git config --global core.editor "gedit --standalone"
```
**Sublime**:  
```sh
git config --global core.editor "subl -n -w"
```

#### For Mac:
**Sublime**:  
```sh
git config --global core.editor "'/Applications/Sublime Text 2.app/Contents/MacOS/Sublime Text 2' -w"
```
**Nano**:  
```sh
git config --global core.editor nano
```
To use nano, just edit text normally, then exit by pressing `Ctrl-X`, it will ask you to save, press `Y`, it will ask for a filename, press `Enter`

#### For Windows:
**Sublime**:  
```
git config --global core.editor "'C:/Program Files/Sublime Text 2/sublime_text.exe' -w"
```
Make sure to edit the path to match the path that exists on your computer.

**Notepad++**:  
```
git config --global core.editor "'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```
Make sure to edit the path to match the path that exists on your computer.

## Configuring Sublime
### Plugins
First you need to install Sublime Package Control. Follow the instructions [here](http://wbond.net/sublime_packages/package_control/installation) or in short:
1. Press Ctrl-`
2. Paste this into the console that pops up and wait for it to finish and ask you to restart sublime:
```
import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print("\n\n\n\n\n\n\n\n\nPlease restart Sublime Text to finish installation")
```

### Line endings
To not mess up your console (if you are on windows, *sigh*) when you copy and paste code from sublime you need to set it to use only unix line endings. To do this, edit the default settings (from `Preference -> Settings-Default`)
`Ctrl-f` and find "default_line_ending" and change it to this:
```
"default_line_ending": "unix",
```

### Indentation
Now `Ctrl-f` again and find "tab_size" and change that block to:
```
// The number of spaces a tab is considered equal to
"tab_size": 2,

// Set to true to insert spaces when tab is pressed
"translate_tabs_to_spaces": true,
```
This sets it up to only uses spaces.

Now we will install and use the BeutifyRuby plugin.  
First open a terminal and install the htmlbeautifier gem:
```
sudo gem install htmlbeautifier
```

Now in sublime, go to `Preferences -> Package Control`. Click on `Install Package`. Wait for it to load. Now type `BeautifyRuby` into the search and click on it when it is filtered out. Wait for it to install. Once done, restart sublime.

Now when you are editing any ruby file (including ERB!) all you have to do is press `Ctrl-Alt-k` or `Ctrl-Cmd-k` on Mac OS and all your ruby gets formatted beautifully!

### Whitespace
In the Default Settings configuration again, `Ctrl-f` for `trailing_white_space` and make it:
```
 "trim_trailing_white_space_on_save": true,
```

## Ubuntu
If you are clever enough to realize that life is much easier dealing with ruby and rails and development in general on Ubuntu, then kudos! And here's a few things you will want to set up after you install Ubuntu (specially if through wubi!)

### GUC Proxy for GUI programs
1. Open the dash (press the windows button) and type `Network` and click on the network settings.  
2. Click on the `Network Proxy` settings
3. Change the Method from `None` to `Manual`
4. In the `HTTP Proxy` setting, type `your.guc.login:yourGUCpassword@50.0.0.5` and set the `Port` to 8080
5. Do the same for the `HTTPS Proxy` setting

This will set the proxy for Chrome, Firefox, etc

### GUC Proxy in the terminal
Before you do any of the setup below, follow the instructions for exporting the proxy variable as shown [above](configuring-your-environment#guc-proxy-setup)
Now close the terminal and open it again, then run `gucproxy` to export the proxy in this terminal session.

(Note below how we use `sudo -E` instead of just `sudo`. The `-E` param passes the environment (which includes the proxy settings) to `sudo`)

### Update the repositories (this is **important**, do not skip it)
```sh
sudo dpkg --add-architecture i386
sudo -E apt-get update
```

### Install synaptic package manager and some utilites
```sh
sudo -E apt-get install synaptic vim htop curl
```

### Install sublime
```sh
sudo add-apt-repository ppa:webupd8team/sublime-text-2
sudo -E apt-get update
sudo -E apt-get install sublime-text
```

### Install git, and merge tool meld, and rails3
```sh
sudo -E apt-get install git meld rails3
```

### Install some commonly needed development libraries
```sh
sudo -E apt-get install libsqlite3-dev libxml2-dev libxslt-dev
```

### Install java (we need it for solr!)
```sh
sudo -E apt-get install default-jre
```

### Install skype
Open the dash (press the windows button on your keyboard) and search for "Software Sources". Click the "Other Software" tab, and from there check the "Canonical Partners" repository. Now in a terminal:
```sh
sudo -E apt-get install ia32-libs skype skype-bin
```