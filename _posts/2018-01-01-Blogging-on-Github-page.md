---
layout: post
title:  GitHub Page notes 
date:   2018-01-01 16:16:01 -0800
categories: jekyll
---

# Blogging on GitHub Page

## Jekyll

>[Jekyll](https://jekyllrb.com) is a simple, blog-aware, static site generator.
>
>Jekyll is the engine behind [GitHub Pages](https://pages.github.com/).
>
>It takes a template directory containing raw text files in various formats, runs it through a converter like [Markdown](https://daringfireball.net/projects/markdown/syntax) and [Liquid](https://shopify.github.io/liquid/) renderer, and renders out a complete, ready-to-publish static website.

### Common tasks

[YAML](https://yaml.org/) [Front Matter](https://jekyllrb.com/docs/front-matter/) is used to configure the posts and pages.

[permanent links](https://jekyllrb.com/docs/permalinks/) is used to instruct how the urls are generated.

[Default github page Themes](https://pages.github.com/themes/) has built-in features and you still can [customize CSS and HTML in themes](https://help.github.com/articles/customizing-css-and-html-in-your-jekyll-theme/).

## Liquid

> Safe, customer-facing template language for flexible web apps.

Liquid use `{{ }}` template syntax to render content.

Curly braces and percent signs: `{% %}` create the logic and control flow for templates

```liquid
{% if user %}
  Hello {{ user.name }}!
{% endif %}
```

[More control flows](http://shopify.github.io/liquid/tags/control-flow/)

"|" add filter support. For example, `[storm troop cat]({{ "/assets/imgs/storm_troop_cat.jpg" | absolute_url }})` produces `https://givemepower8.github.io/assets/imgs/storm_troop_cat.jpg`

[Standard Liquid filters](https://jekyllrb.com/docs/liquid/filters/#standard-liquid-filters)

[Liquid filters](https://shopify.github.io/liquid/filters)

[Liquid more](https://help.shopify.com/en/themes/liquid)

[Jekyll Liquid filters](https://jekyllrb.com/docs/liquid/filters/)

## GitHub Pages

>GitHub Pages is a static site hosting service designed to host your personal, organization, or project pages directly from a GitHub repository.

[GitHub Pages Learning Lab](https://lab.github.com/githubtraining/github-pages)

[Using a custom domain with GitHub Pages](https://help.github.com/articles/using-a-custom-domain-with-github-pages/)