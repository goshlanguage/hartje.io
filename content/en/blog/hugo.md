---
title: "Hugo"
date: 2022-02-05T11:02:13-06:00
Description: "How to setup and manage hugo on github pages"
Tags: []
Categories: []
DisableComments: false
draft: false
---

This site is powered by `hugo`. I love the simplicity of writing markdown, pushing it to [this repo](https://github.com/goshlanguage/hartje.io/), and having that transpiled into HTML through a github action. There are a lot of tools in this space, such as the popular `Sphinx`, `Mkdocs`, and `Jekyll`.

I chose `hugo` specifically for how little setup was needed for a self publishing repo to manage my site on Github Pages. Using this service, the project's url becomes `<YOUR USERNAME>.github.io`, or `<YOUR USERNAME>.github.io/<YOUR PROJECT>/`, and supports custom domains.

For more information, see:

- [setup hugo on github pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
- [configure a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
- [getting started with github pages](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)

To get started, create the repo, and `brew install hugo` if it's not already available.

> NOTE: name this repo `<YOUR USERNAME>.github.io` for your personal username repo, otherwise if you're bringing your own repo, you can use whatever name you want

## Initializing the project

Hugo will scaffold out your site for:

```sh
hugo new site hartje.io
cd hartje.io
```

Next, [find a theme](https://themes.gohugo.io/) you like, then click the `Download` button find it's git repo. You now need to add it as a git `submodule`, and then `init` the submodule so it's tracked in your source code. That might practically look like this:

```sh
git submodule add https://github.com/Wtoll/venture.git themes/venture --depth=1
git submodule update --init --recursive # needed when you reclone your repo (submodules may not get cloned automatically)
```

### Configuring Hugo

Hugo has a lot of configuration options. You can configure hugo by creating a `./config.toml` file, or even in whichever format you prefer out of `yaml`, `toml`, and `json`.

### Setup Github Pages in your repo settings

> By default, the GitHub action pushes the generated content to the `gh-pages` branch. This means GitHub has to serve your `gh-pages` branch as a GitHub Pages branch. You can change this setting by going to `Settings > GitHub Pages`, and change the source branch to `gh-pages`.

Source: [Hugo - Hosting on Github](https://gohugo.io/hosting-and-deployment/hosting-on-github/)

### Custom Domains

If you're bringing your own DNS, be sure to add your domain to `/static/CNAME`, as a requirement for `Github Pages`.

```sh
echo "hartje.io" > static/CNAME
```

`/static/CNAME`:

```text
hartje.io
```

### Create a post

`hugo` also has a scaffold for posts. To create a new post run:

```sh
hugo new mypost.md
# or alternatively, you can nest your posts in directories
# hugo new mydir/mypost.md
```

The created markdown files will be in the `content/` folder.

## Automatically publish changes to Github Pages

We can make quick work of an automated deployment for our site, by adopting this simple github workflow. Add this `.github/workflows/gh-pages.yaml` and push your branch to set it up.

`/.github/workflows/gh-pages.yaml`:

```yaml
name: github pages

on:
  push:
    branches:
      - main  # Set a branch to deploy
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

## Customizing Hugo

First, here is a wonderful tutorial for [adding custom css or javascript to your hugo site](https://www.banjocode.com/post/hugo/custom-css/) from `banjocode`.

If you'd like to customize your `hugo` site layout, then first take a look at the structure of our theme:

```bash
tree themes/venture
themes/venture
├── LICENSE
├── README.md
├── archetypes
│   └── default.md
├── assets
│   └── sass
│       └── main.sass
├── images
│   ├── screenshot.png
│   └── tn.png
├── layouts
│   ├── 404.html
│   ├── _default
│   │   ├── baseof.html
│   │   ├── list.html
│   │   └── single.html
│   ├── about
│   │   └── list.html
│   ├── index.html
│   └── partials
│       ├── footer.html
│       ├── head.html
│       └── header.html
├── static
│   └── images
│       └── blank.png
└── theme.toml
```

You might recognize that the theme repo's structure matches the one scaffolded by `hugo`. `hugo` will prefer a root level file, should the theme have a conflicting file, so we can explore what all we can change and experiment by copying to the root level and modifying it.

For instance, if we wanted to update the `layouts/partials/footer.html`, we'd want to first copy the theme's into our root level `layouts/partials`, then modify the file in `/layouts/partials/footer.html`.

```sh
mkdir -p layouts/partials
cp themes/venture/layouts/partials/footer.html layouts/partials/footer.html
```
