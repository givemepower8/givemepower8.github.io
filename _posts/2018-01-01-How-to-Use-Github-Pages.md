---
layout: post
title:  How to use GitHub Pages
subtitle: How to use GitHub Pages
date:   2018-01-01 16:16:01 -0800
categories: [GithubPages]
tags: [jekyll, GithubPages]
---
# How to use GitHub Pages

Best ways to learn is to practice, write and teach.

>[GitHub Pages](https://pages.github.com/) is a static site hosting service designed to host your personal, organization, or project pages directly from a GitHub repository.

To me, GitHub Pages is the perfect place to jog down all the technical notes in my lifelong learning process.

Some benefits I can think of:

* Markdown syntax helps to focus on the documentation structure and content writing
  * use headings can greatly organize the topic
  * the content is not mixed with html tags
  * best versioning of the documentation
* Jekyll and Liquid are great engines for the web pages
  * tags, categories in Front Matter are great
  * posts, pages, and paging support

The following is the list of some good resources to start off the pages.

[GitHub Pages Basics](https://help.github.com/categories/github-pages-basics/)

[GitHub Pages Learning Lab](https://lab.github.com/githubtraining/github-pages)

[Using a custom domain with GitHub Pages](https://help.github.com/articles/using-a-custom-domain-with-github-pages/)

To write the posts, place the new blog posts into the _posts folder. Jekyll templating engine has strict naming rules. The names of the blog posts need to use the following naming convention: `year-month-date-{slug}.md`

## Jekyll

>[Jekyll](https://jekyllrb.com) is a simple, blog-aware, static site generator.
>
>Jekyll is the engine behind [GitHub Pages](https://pages.github.com/).
>
>It takes a template directory containing raw text files in various formats, runs it through a converter like [Markdown](https://daringfireball.net/projects/markdown/syntax) and [Liquid](https://shopify.github.io/liquid/) renderer, and renders out a complete, ready-to-publish static website.

After grokking the [directory structure](https://jekyllrb.com/docs/structure/), you need to understand the [Pages](https://jekyllrb.com/docs/pages/) and [Posts](https://jekyllrb.com/docs/posts/). Those two are the most important building blocks for creating content.

[YAML](https://yaml.org/) [Front Matter](https://jekyllrb.com/docs/front-matter/) is used to configure the variables in the posts and pages. Some commons are categories and tags which can determine the [Permanent links](https://jekyllrb.com/docs/permalinks/), which  is used to instruct Jekyll how the urls are generated.

[Default github page Themes](https://pages.github.com/themes/) has built-in features and you still can [customize CSS and HTML in themes](https://help.github.com/articles/customizing-css-and-html-in-your-jekyll-theme/).

If you don't like the default themes, you can use the _sass, _layouts, _includes and assets folders to implement your own design.

## Liquid

> Safe, customer-facing template language for flexible web apps.

Liquid use double curly braces to render content.

Curly braces and percent signs create the logic and control flow for templates.

Liquid supports [control flows](http://shopify.github.io/liquid/tags/control-flow/) which is often used with site.* variables.

"\|" add filter support inside the curly braces.

[Standard Liquid filters](https://jekyllrb.com/docs/liquid/filters/#standard-liquid-filters)

[Liquid filters](https://shopify.github.io/liquid/filters)

[Liquid more](https://help.shopify.com/en/themes/liquid)

[Jekyll Liquid filters](https://jekyllrb.com/docs/liquid/filters/)

[https://www.siteleaf.com/blog/tags/liquid/](https://www.siteleaf.com/blog/tags/liquid/)

### Bloggers use GitHub Pages

[http://longqian.me](https://github.com/qian256/qian256.github.io)

[http://www.minddust.com](https://github.com/minddust/minddust.github.io)

[http://codinfox.github.io](https://github.com/codinfox/codinfox-lanyon)