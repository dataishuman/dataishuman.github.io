# [dataishuman](https://dataishuman.github.io)

dataishuman is a website on the human side of data. 

## What is it

Primarily a collection of data works on open data, or data we retrieve from public sources and API's, with the underlying intention of visualising relations non trivial to spot. It is fundamentally a show of data.

## How it is built

With the HTML5 [Spectral theme](https://html5up.net/spectral) by [@ajlkn](https://twitter.com/ajlkn) and forking from [arkadianriver](https://github.com/arkadianriver/arkadianriver.com), to whom goes all of the gratitude for making this template available and writing very useful documentation on how to customise it, part of which is reported here.

All the visualisations are built in [D3](https://d3js.org).

## How to run it

With Jekyll installed, 

`bundle exec jekyll serve`

## Posts and their categories

Data "posts" are in category "pieces". Posts (in `_posts`) have category name in front, see folder. 

Other categories can be created. Category corresponds to a page in `_pages`.

### YAML front matter

Fields are:

* `layout`: optional for post or pages (defaults in `_config.yml`), useful for posts outside posts or pages

* `title`: title of post

* `categories`: category post belongs to 

* `excerpt`: small description of post

* `background-image`: file (in `_images/`) of background image if desired

* `tags`: one per line, tags of post

* `author`: to display the snippet in `_data/authors.yml`

* `options`: to customize page, options are
   - minihead      # as minimal a title as possible, and no date printed
   - fullwidth     # leaving only a tiny margin on all media sizes
   - nocomment     # disable disqus comments for this post
   - nomenu        # for pages, don't add to the menu
   - nolanding     # for pages and featured posts, don't add to the landing page

* `changefreq`: the default change frequency for all pages in the site map is `monthly`. Depending on how often you think you'll edit a page, you can set the page change frequency. See [why](https://www.v9seo.com/blog/2011/12/27/sitemap-xml-why-changefreq-priority-are-important/) this is important. 

* `key`: all files in the `_pages` folder are displayed in the nav menu unless you set the `nomenu` option. Use `key` to specify the order (an integer) you want the pages listed in the nav menu. Values are sorted in ascending order.

* `lastmod`, `date`: if you want the site map `lastmod` setting to be updated, you can set one or both of these to your new modified date as `YYYY-MM-DD HH:MM:SS +/-TTTT` (`lastmod` has priority). If you use `date`, the date shown on the page is also modified, overriding the date in the filename. The timestamp is assumed to be UTC unless you specify the time zone offset afterward. Example:

```
lastmod: 2016-03-13 23:11:00
date: 2016-01-01 00:00:00 -0800
```

* `priority`: use `priority` (a float 0-1) to specify two things:
   - the grouping in the pieces index
   - the site map priority
In the pieces index, the pieces are grouped by priority, listed by descending priority and by descending date within each priority. Note that pieces must have a priority set for the ordering to work, throws `can't compare float with nil` Jekyll error otherwise. Default priorities in the `sitemap.xml` file:
   + `1.0` - Landing page
   + `0.7` - posts
   + `0.5` - Pages

* `sitemap_exclude`: set to `yes` if you want to exclude a page from the sitemap.

* `includes`: if your page needs to include stylesheets or scripts, provide 'em as either local or remote URLs. Prefix remote urls with `//`, not `http`. Stylesheets are included in the header and scripts at the bottom before the body closes.

```
style-includes:
  - /local/path/to/stylesheet.css
  - //remote.com/url/to/stylesheet.css
script-includes:
  - /local/path/to/script.js
  - //remote.com/url/to/script.js
```

* `style, script`: these are useful when you want to embed styles and scripts outside of the `{% raw %}{{ content }}{% endraw %}` area. Use the yaml `|` indented block to ensure line breaks are preserved. The styles are included in the header below stylesheet includes; scripts are included at the bottom below script includes.

```
style: |
  /* some css block here */
  .some-class {
    somestyle: definition;
  }
script: |
  // some script block here...
  $(document).ready(function(){
    ...
  });
```
