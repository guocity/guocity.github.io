# how to change theme in jekyll

theme repo:

    https://github.com/topics/jekyll-theme

go to rubygems.org and search for the theme you want to use. For example, I want to use the [minima](https://rubygems.org/gems/minima) theme. So I will add the following line to the Gemfile:


    try: minimal-mistakes

open gemfile and add the following line:

    gem "minima", "~> 2.5"

then run the following command:

    bundle install

then open the _config.yml file and add the following line:

    theme: minima

then run the following command:

    bundle update
    
then run the following command:

    bundle exec jekyll serve

