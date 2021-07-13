# automaticanalysis.github.io
automaticanalysis documentation

## How to update the website

### How to serve the website locally

If you want to check how things look locally before you push any changes on github, you can serve the website locally.

Make sure that you have [ruby](https://www.ruby-lang.org/en/downloads) installed. On Windows, you need [ruby+devkit](https://rubyinstaller.org/downloads).

From the directory where you have cloned this repository, run:
```
bundle exec jekyll serve
```
#### On Windows ###
You need to adapt the gem configuration before rendering locally.

1. Add the following lines to the Gemfile:
```
gem 'wdm', '>= 0.1.0'
gem "webrick"
```
2. Update gems:
```
bundle update
```
**Important**: Do not PR the modified Gemfile and Gemfile.lock to the main repo!
