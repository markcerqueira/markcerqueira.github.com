## Introduction
This repository is automatically transformed by [Jekyll][1] into a static site whenever I push to GitHub.

## Set-Up
* See this helpful [GitHub page on setting up Jekyll][11] - specifically the Installing Jekyll section.
* To reset your RubyGem state: `mv Gemfile.lock Gemfile.lock.backup && sudo bundle clean --force && bundle install`

## Common Tasks and Commands
* `bundle exec jekyll serve --watch` to run the blog locally
* `bundle exec rake post title="New Post"` to create a new blog post
* `bundle exec rake publish` pushes changes to the source branch and publishes blog to the master branch

## Credits
* Using modified version of [the-program Jekyll theme][2]
* Source Sans Pro font from [Google Fonts][3]
* Code higlighting by [Pygments][4]
* pygments.css modified from [madhur's pygments.css][5]
* [Web icons][6] from Fairhead Creative's WebIcons Set
* [Sitemap.xml generator][7] by Michael Levin
* [RSS xml feed template][8] from George Mandis
* Local rendering done easily with [these instructions][9] by ixti
* Related Posts generated using Liquid code from [here][10] by Wenli Zhang
* Powered up Rakefile with git awareness from [git-rake][12] by flavorjones
* Auto-deplying using [Travis][13] with [setup instructions by domenic][14]

## License
The following files/directories and their contents are Copyright Mark Cerqueira. You may not reuse anything therein without my permission:

*   _posts/
*   assets/
*   projects.html
*   blog.html
*   404.html
*   index.html

All other directories and files are [MIT](http://opensource.org/licenses/MIT) licensed.

[1]: https://github.com/mojombo/jekyll
[2]: https://github.com/jekyllbootstrap/theme-the-program
[3]: http://www.google.com/fonts/
[4]: http://pygments.org/
[5]: https://github.com/madhur/madhur.github.com/blob/master/files/css/syntax.css
[6]: https://github.com/adamfairhead/webicons
[7]: https://github.com/kinnetica/jekyll-plugins
[8]: https://github.com/snaptortoise/jekyll-rss-feeds
[9]: http://ixti.net/software/2013/01/28/using-jekyll-plugins-on-github-pages.html
[10]: http://zhangwenli.com/blog/2014/07/15/jekyll-related-posts-without-plugin/
[11]: https://help.github.com/articles/using-jekyll-with-pages/
[12]: https://github.com/flavorjones/git-rake/blob/master/git.rake
[13]: https://travis-ci.org/
[14]: https://gist.github.com/domenic/ec8b0fc8ab45f39403dd
