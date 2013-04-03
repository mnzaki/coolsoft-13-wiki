### Git
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
# FIXME
```

## Ubuntu
If you are clever enough to realize that life is much easier dealing with ruby and rails and development in general on Ubuntu, then kudos! And here's a few things you will want to set up after you install Ubuntu (specially if through wubi!)

### Update the repos, setup x86 libraries, install java (we need it for solr!)
```sh
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install ia32-libs
sudo apt-get install default-jre
```
### Install synaptic package manager and some utilites
```sh
sudo apt-get install synaptic vim htop curl
```
### Install git, rails3
```sh
sudo apt-get install git rails3
```
### Install sublime
```sh
sudo add-apt-repository ppa:webupd8team/sublime-text-2
sudo apt-get update
sudo apt-get install sublime-text
```
### Install skype
Open the dash (press the windows button on your keyboard) and search for "Software Sources". Click the "Other Software" tab, and from there check the "Canonical Partners" repository. Now in a terminal:
```sh
sudo apt-get install skype skype-bin
```