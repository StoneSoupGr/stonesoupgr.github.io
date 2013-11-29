require 'bundler'
require 'bundler/setup'
Bundler.require(:default)

namespace :github do
  desc "Build site to in master branch"
  task :build do
    `jekyll build`
    `ls | grep -v _site | grep -v CNAME | xargs rm -rf`
    `mv _site/* .`
    `rm -rf _site/`
    `git symbolic-ref HEAD refs/heads/master`
    `git add .`
    `git ci -a -m 'Generate site'`
    `git reset`
    `git checkout development`
  end
end