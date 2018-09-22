# ODK Website

![Platform](https://img.shields.io/badge/platform-Jekyll-blue.svg) [![Ruby version](https://img.shields.io/badge/ruby-2.5.1-blue.svg)](https://www.ruby-lang.org/en/downloads/) [![License](https://img.shields.io/badge/license-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/) [![Build status](https://circleci.com/gh/opendatakit/website.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/opendatakit/website/) [![Slack status](http://slack.opendatakit.org/badge.svg)](http://slack.opendatakit.org/)

This repository is home to the [ODK homepage](https://opendatakit.org/).

## Table of Contents

* [Developing locally](#developing-locally)
	- [Installing Ruby](#installing-ruby)
		- [*nix](#macos,-gnu/linux)
		- [Windows](#microsoft-windows)
	- [Installing website](#installing/running-opendatakit/website)
* [Contributing](#contributing)
* [Troubleshooting](#troubleshooting)

## Developing locally

### Installing Ruby

The ODK website is built with [Ruby](https://www.ruby-lang.org/en/downloads/).

#### MacOS, GNU/Linux

1. **Installing `rbenv`**
*MacOS:* Simple installation instructions using Homebrew can be found in the [`rbenv` documentation](https://github.com/rbenv/rbenv#homebrew-on-macos). This is the preferred method for MacOS. To install `rbenv` without Homebrew, refer to the GNU/Linux instructions.

	*GNU/Linux:* The [`rbenv-installer`](https://github.com/rbenv/rbenv-installer#rbenv-installer) is a script which idempotently installs or updates `rbenv` on your system.

2. **Installing Ruby**
Once `rbenv` has been installed, install the latest Ruby (currently `2.5.1`):
```
$ rbenv install 2.5.1
```

#### Microsoft Windows

Windows users should use [RubyInstaller](https://rubyinstaller.org/).

### Installing/Running OpenDataKit/website

1. Follow the instructions in the [contribution guide](https://github.com/opendatakit/website/blob/master/CONTRIBUTING.md) to [fork](https://help.github.com/articles/fork-a-repo/) the website repository and then [clone](https://help.github.com/articles/cloning-a-repository/) your fork.

2. Configure your project to use the correct version of Ruby.
	a. Navigate to the root directory of your project.

	```
	$ cd /MY/DEVELOPMENT/DIRECTORY/website
	```

	b. Set the local application-specific Ruby version by using [`rbenv-local`](https://github.com/rbenv/rbenv#rbenv-local).

	```
	$ rbenv local 2.5.1
	```

	c. Verify that your project is using Ruby version `2.5.1`:
	```
	$ ruby -v
	```

3. Install `bundler`.
`$ gem install bundler`

4. Install this project.
`$ bundle install`

5. Launch the server.
`$ bundle exec jekyll serve`

The local site will update as changes are made.

## Contributing

One quick way to contribute is to review the [website](https://opendatakit.org) and [file issues](https://github.com/opendatakit/website/issues) documenting the problems you see. If you would like to help fix those issues, see [the contribution guide](CONTRIBUTING.md).

## Troubleshooting

### Permissions

If you encounter the following error:
`You don't have write permissions for the /var/lib/gems/2.3.0 directory.`
then please review the installation instructions to make use of `rbenv`.

Only root has write permissions for `/var/lib`; using `sudo` for subsequent `gem install` comands won't work, and changing permissions for that directory using `chmod` is considered dangerous. This issue is avoided when using `rbenv`.

### Nokogiri

[Nokogiri (鋸)](http://www.nokogiri.org/) is a Rubygem providing HTML, XML, SAX, and Reader parsers with XPath and CSS selector support.

The installation command `bundle install` tries to install `nokogiri`.

If you face following error:
	`Gem::Ext::BuildError: ERROR: Failed to build gem native extension.`

You can fix it as follows:

For Ubuntu/Debian OS:
Run the command `sudo apt-get install build-essential patch ruby-dev zlib1g-dev liblzma-dev` and try again.

If you are using any other OS, you can follow the instructions mentioned here:
http://www.nokogiri.org/tutorials/installing_nokogiri.html
