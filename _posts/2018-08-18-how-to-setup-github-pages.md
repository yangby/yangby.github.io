---
layout: post
title: How to Setup GitHub Pages?
categories: [github-pages]
tags: [tex]
---

Last weekend, I tried [GitHub Pages].

I've tried a lot of online services to build a blog in past several years,
such as [Google App Engine], [Red Hat OpenShift] v2, [Heroku].

[GitHub Pages] is more simple than a [PaaS], or running a own web server in
a [VPS].
I can focus on the content of my posts.

[Google App Engine]: https://appengine.google.com
[Red Hat OpenShift]: https://www.openshift.com
[Heroku]: https://www.heroku.com
[GitHub Pages]: https://pages.github.com
[PaaS]: https://en.wikipedia.org/wiki/Platform_as_a_service
[VPS]: https://en.wikipedia.org/wiki/Virtual_private_server

### Create a Repository in GitHub

Since I want to setup a personal site, I just create a repository named
`USERNAME.github.io`.

The I clone the new repository:

```shell
git clone https://github.com/USERNAME/USERNAME.github.io
```

Write a markdown file named `index.md`, add to the repository, commit, then
push to github.

DONE!

### Setting Up A Local Jekyll Environment

+ Create a file `Gemfile`:

  ```
  source 'https://rubygems.org'
  gem 'github-pages', group: :jekyll_plugins
  ```

+ Install [GitHub Pages Ruby Gem]:

  ```shell
  bundle install
  ```

+ Creating a personal access token in [Developer settings / New personal access token]
  with only the `public_repo` scope selected, then:

  ```shell
  export JEKYLL_GITHUB_TOKEN=YOUR_NEW_PERSONAL_ACCESS_TOKEN
  ```

  Use a personal access token can fix the issue:

  ```
  GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
  ```

+ Run GitHub Pages in local:

  ```shell
  bundle exec jekyll serve --incremental
  ```

[GitHub Pages Ruby Gem]: https://github.com/github/pages-gem
[Developer settings / New personal access token]: https://github.com/settings/tokens/new

### Change GitHub Pages Themes

More details can found in follow pages:

+ [Customizing GitHub Pages / Adding a Jekyll theme to your GitHub Pages site](https://help.github.com/articles/adding-a-jekyll-theme-to-your-github-pages-site/)
+ [Jekyll Themes](https://jekyllrb.com/docs/themes/)

#### Activate One of The Officially Supported Themes

There are 13 [GitHub Pages Official Supported Themes]:
  + [Primer](https://pages-themes.github.io/primer/) (default, light, white)
  + [Cayman](https://pages-themes.github.io/cayman/) (light, green)
  + [Slate](https://pages-themes.github.io/slate/) (light, grey)
  + [Merlot](https://pages-themes.github.io/merlot/) (light, yellow)
  + [Time-Machine](https://pages-themes.github.io/time-machine/) (light, grey)
  + [Minimal](https://pages-themes.github.io/minimal/) (light, white)
  + [Leap-Day](https://pages-themes.github.io/leap-day/) (light, yellow & blue)
  + [Modernist](https://pages-themes.github.io/modernist/) (light, lightblue & grey)
  + [Hacker](https://pages-themes.github.io/hacker/) (dark, black & green)
  + [Midnight](https://pages-themes.github.io/midnight/) (dark, brown)
  + [Architect](https://pages-themes.github.io/architect/) (light, blue)
  + [Tactile](https://pages-themes.github.io/tactile/) (light, grey)
  + [Dinky](https://pages-themes.github.io/dinky/) (light, yellow)

Add a new line to `_config.yml`, with the theme name:

```yaml
theme: jekyll-theme-primer
```

[GitHub Pages Official Supported Themes]: https://github.com/pages-themes

#### Activate Any Other Open Source Jekyll Theme Hosted on GitHub

Add a new line to `_config.yml`, with the theme repo:

```yaml
remote_theme: AUTHOR/REPOSITORY@BRANCH_OR_TAG_OR_COMMIT
```

### Math Support

Add [Math Support] to Jekyll, just need add a new line to your posts:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/VERSION/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
```

[Math Support]: https://jekyllrb.com/docs/extras/#math-support

#### Samples

When $$a \ne 0$$, there are two solutions to $$ax^2 + bx + c = 0$$ and they are
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

Maxwell's Equations:

\begin{align}
  \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} & = \frac{4\pi}{c}\vec{\mathbf{j}} \\
  \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\
  \nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\
  \nabla \cdot \vec{\mathbf{B}} & = 0
\end{align}

### Customizing GitHub Pages

More details can found in follow pages:

+ [Customizing GitHub Pages](https://help.github.com/categories/customizing-github-pages/)
+ [Jekyll Docs](https://jekyllrb.com/docs/home/)
+ [Liquid: Safe, customer-facing template language for flexible web apps](https://shopify.github.io/liquid/)
