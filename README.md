# Ryan's Blog [https://rwibawa.github.io/]
Ryan's Technology Corner.

## Use docker to run `jekyll`
```sh
# Clone and build
$ git clone https://github.com/rwibawa/rwibawa.github.io.git
$ cd rwibawa.github.io/

# Get docker image: jekyll:4
$ docker pull jekyll/jekyll:4

# Build jekyll
$ export JEKYLL_VERSION=4
$ rm Gemfile.lock 
$ docker run --rm --volume="$PWD:/srv/jekyll" -it jekyll/jekyll:$JEKYLL_VERSION jekyll build
$ bundle add webrick
$ docker run --name newblog --volume="$PWD:/srv/jekyll" -p 4000:4000 -it jekyll/jekyll:$JEKYLL_VERSION jekyll serve --watch --drafts

$ docker ps -a
$ docker rmi newblog

# Create new blog
$ docker run --rm --volume="$PWD:/srv/jekyll" -it jekyll/jekyll:$JEKYLL_VERSION jekyll new .

```
open [http://localhost:4000](http://localhost:4000).

### References
* [Running Jekyll in Docker](https://ddewaele.github.io/running-jekyll-in-docker/)
* [webrick (LoadError)](https://devcoops.com/cannot-load-such-file-webrick/)


## 1. Install Jekyll
```bash
# Clone and build
  $ git clone https://github.com/rwibawa/rwibawa.github.io.git
  $ cd rwibawa.github.io/
  $ gem install nokogiri -v '1.8.0' --source 'https://rubygems.org/' -- --use-system-libraries
  $ bundle install

# Get jekyll
  $ rvm list
  $ rvm gemset list
  $ gem install jekyll
  $ jekyll -v

# Create a new project
  $ jekyll help
  $ jekyll new rwibawa.github.io
  $ cd rwibawa.github.io/
  $ ls -lah
  $ jekyll build
  $ jekyll serve

  $ ls -lah ryan.wibawa/_site/
  $ cat _posts/2017-07-10-welcome-to-jekyll.markdown

  $ git add -A
  $ git commit -m "Initial commit"
  $ git push -u origin master
```

## 2. Add jekyll themes.
* [https://jekyllrb.com/docs/themes/]
* [https://github.com/joshgerdes/jekyll-uno]
* [http://jekyllthemes.org/page5/]
* [https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme]

## 3. Drafts
Add the draft of a post in directory `_drafts/` and run jekyll with `--drafts` option.

```bash
$ jekyll serve --drafts
```
