Git has a hooking system that can be exploited for fun and profit.

## Background and Warning
<b>WARNING: this is HIGHLY experimental. No warranties. I am not responsible for any damages, emotional or otherwise, directly or indirectly caused by following this guide</b> 

The hook we are interested in is the pre-commit hook. Git allows us to do whatever we want and then tell it whether or not this commit can be made. We will use this to check if the commit is clean and up to standards. We will use a gem called `pre-commit` that applies pre-commit checks, and a gem called `rubocop` that applies ruby style checks.

This setup will check for various things, like 'debugger' code, committed merge conflicts, bad ruby code style (various naming problems, whitespace, bad conventions, etc), and other things too.

After you do this, and you try to make an offending commit you will be presented the offending lines and asked to fix them before you can continue.

## Setup
This specific setup is for Rails projects obviously.

First we need to include the `pre-commit` and `rubocop` gems in the Gemfile. We will use the version of of `pre-commit` from [mnzaki](https://github.com/mnzaki)'s (yours truly) fork, as there are fixes (and rubocop integration!) that have not made it into upstream yet.

So in your Gemfile, specifically in the test and development groups, you need this:
```
group :test, :development do
  gem 'pre-commit', :git => 'https://github.com/mnzaki/pre-commit.git'
  gem 'rubocop', :git => 'https://github.com/bbatsov/rubocop.git'
end
```

Now the normal way to use pre-commit is to install the hook using `pre-commit install` but we will force installation (and setup) on every load of the rails environment using an initializer file. So create a new initializer file, git_config.rb for example, and put this into it:  
(Note: the following is only a guideline. Please read it and change it according to your needs.)
```
# config/initializers/git_config.rb
# Not the best way to do this
# But it's one way

require 'fileutils'

FileUtils.cd '..' do
  # We install a custom hook because pre-commit is installed in the bundle
  # NOTE: do not redirect the output of 'which' because it messes with the exit status
  interp =
    if system('which rvm')
      'rvm default do ruby'
    else
      'ruby'
    end
  File.open('.git/hooks/pre-commit', 'w') do |f|
    f.write <<-eos.strip_heredoc
      #!/usr/bin/env #{interp}
      require 'fileutils'
      FileUtils::cd '#{Rails.root}' do
        require 'bundler/setup'
        require 'pre-commit'
        FileUtils::cd '..' do
          PreCommit.run
        end
      end
    eos
  end
  FileUtils.chmod(0755, '.git/hooks/pre-commit')

  # Change the enabled checks as you see fit.
  system('git config pre-commit.checks ' +
         '"rubocop_all, debugger, pry, merge_conflict, white_space, tabs, console_log, migrations"')
  # Some helpful settings to stop Windoze from messing things up
  system('git config core.fileMode false')
  system('git config core.eol lf')
  system('git config core.autocrlf true')
end
```

You can check the readme at <https://github.com/mnzaki/pre-commit> for more info.

Finally, you need a `.rubocop.yml` file at the base of your git repo. This will contain the rubocop checks you want applied. See <https://github.com/bbatsov/rubocop> for more info.

An example `.rubocop.yml` file (with some annoying checks turned off) can be found [here](https://raw.github.com/DevYah/coolsoft-13/master/.rubocop.yml)

For a more friendly description of some of the `rubocop` errors, see our [conventions](https://github.com/DevYah/coolsoft-13/wiki/Conventions-and-Guidelines#common-rubocop-errors) wiki page.
