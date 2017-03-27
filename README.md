# [dataishuman](https://dataishuman.github.io)

dataishuman is a website on the human side of data. 

## What is it

Primarily a collection of data works on open data, or data we retrieve from public sources and API's, with the underlying intention of visualising relations non trivial to spot. It is fundamentally a show of data.

## How it is built

With the HTML5 [Spectral theme](https://html5up.net/spectral) and forking from [arkadianriver](https://github.com/arkadianriver/arkadianriver.com), to whom goes all of the gratitude for making this template available and writing very useful documentation on how to customise it.

All the visualisations are built in [D3](https://d3js.org).

## How to run it

With Jekyll installed, 

`bundle exec jekyll serve`

## Posts and their categories

Data "posts" are in category "pieces". Posts (in `_posts`) have category name in front, see folder. 

Other categories can be created. Category corresponds to a page in `_pages`.

### YAML front matter

Fields available to use better explained with an example

```
---
layout: post
title:  "Testing"
categories: pieces
excerpt: testing the test
background-image: dummy.jpg
tags:
  - test
  - testing
author: martinapugliese   # don't use, I don't like it, see issue #
---
```

Other fields are

* `layout`

For both posts and pages, there's no need to specify the layout.
Specifying the layout is optional because defaults
are set in the `_config.yml` file to set the layout based on the folder it's in
(`_posts` or `_pages`). The layout _is_ useful for pages outside of these folders,
however.

{% highlight yaml %}
layout: {page|post}
{% endhighlight %}

* `options`

The options allow you to customize the page somewhat.

{% highlight yaml %}
options:
  - minihead      # as minimal a title as possible, and no date printed
  - fullwidth     # leaving only a tiny margin on all media sizes
  - nocomment     # disable disqus comments for this post
  - nomenu        # for pages, don't add to the menu
  - nolanding     # for pages and featured posts, don't add to the landing page
{% endhighlight %}

* `changefreq`

The default change frequency for all pages in the site map is `monthly`.
Depending on how often you think you'll edit a page, you can set the page
change frequency. <a target="_blank"
href="https://www.v9seo.com/blog/2011/12/27/sitemap-xml-why-changefreq-priority-are-important/">Here's
a good guide</a> on when to use the available values.

{% highlight yaml %}
changefreq: weekly
{% endhighlight %}

* `key`

All files in the `_pages` folder are displayed in the nav menu unless you
set the `nomenu` option.
Use `key` to specify the order you want the pages listed in the nav menu.
Values are sorted in ascending order.

{% highlight yaml %}
key: 2
{% endhighlight %}

* `lastmod`, `date`

If you want the site map `lastmod` setting to be updated, you can set one or both of
these to your new modified date as `YYYY-MM-DD HH:MM:SS +/-TTTT` (`lastmod` has priority).
If you use `date`, the date shown on the page is also modified, overriding the
date in the filename. The timestamp is assumed to be UTC unless you specify the
time zone offset afterward.

{% highlight yaml %}
lastmod: 2016-03-13 23:11:00
date: 2016-01-01 00:00:00 -0800
{% endhighlight %}

* `priority`

Use `priority` to specify two things:

- the grouping in the works index
- the site map priority

{% highlight yaml %}
priority: 0.8
{% endhighlight %}

In the works index, the works are grouped by priority, listed by descending priority
and by descending date within each priority.

**Note:** For now, `works` posts _must_ have a priority set for the ordering
          to work. If you get a "`can't compare float with nil`" error in your
          jekyll build, there's a missing priority somewhere.

Because the value is used to set the site map priority,
it must be set to a value between 0 and 1.0.
I have three groups of works, using priorities 0.7, 0.6, and 0.5.
None as high as featured posts, but then, I'm not looking for a job right now. ;-)

Default priorities in the `sitemap.xml` file:

- `1.0` - Landing page
- `0.9` - Featured posts
- `0.7` - Other posts
- `0.5` - Pages

* `sitemap_exclude`

Set to `yes` if you want to exclude a page from the sitemap.

{% highlight yaml %}
sitemap_exclude: yes
{% endhighlight %}

### `tags`

For _topics_ posts, the only tag that has an effect right now is `featured`,
which adds it to the top of the `/topics/` page. The most recent eight
featured posts are also added to the main landing page.

{% highlight yaml %}
tags: featured
{% endhighlight %}

For _works_ posts, the tags become a listing of skills demonstrated. For example:

{% highlight yaml %}
tags:
  - C
  - Windows DLL
  - SGML
{% endhighlight %}

![web page display of the preceding tags]({{ '/images/skills.png' | prepend: site.baseurl }})

You can add the `featured` tag to a work if you want it to appear on the main landing page.
The `featured` tag is excluded from the list of skills on the page and `works` index.
However, its page priority overrides the standard priority of featured posts in the site map.

* `includes`

If your page needs to include stylesheets or scripts, provide 'em as either
local or remote URLs. Prefix remote urls with `//`, not `http`. Stylesheets
are included in the header and scripts at the bottom before the body closes.

{% highlight yaml %}
style-includes:
  - /local/path/to/stylesheet.css
  - //remote.com/url/to/stylesheet.css
{% endhighlight %}

{% highlight yaml %}
script-includes:
  - /local/path/to/script.js
  - //remote.com/url/to/script.js
{% endhighlight %}

* `style, script`

These are useful when you want to embed styles and scripts outside of the
`{% raw %}{{ content }}{% endraw %}` area.
Use the yaml `|` indented block to ensure line breaks are preserved.
The styles are included in the header below stylesheet includes;
scripts are included at the bottom below script includes.

{% highlight yaml %}
style: |
  /* some css block here */
  .some-class {
    somestyle: definition;
  }
{% endhighlight %}

{% highlight yaml %}
script: |
  // some script block here...
  $(document).ready(function(){
    ...
  });
{% endhighlight %}

## TODOs

   b. Add a `_data/tokens.yml` file with your IDs & mail program.
      See the `_data/tokens-template.yml.` file for example entries.

   c. Add author info for yourself in `_data/authors.yml` as the first
      author entry in the file.


