# Source for chenwang.org

![Publish Status](https://github.com/cwang/cwang.github.io/actions/workflows/publish.yml/badge.svg)

It relies on [Hugo](https://gohugo.io) to generate the static site. 

It then uses [GitHub Pages](https://pages.github.com/) coupled with [GitHub Actions](https://github.com/features/actions) to deploy the site.

A few caveats:
- It uses themes directly (via `git checkout-index`) instead of git submodules as recommended by Hugo: it is secure and friendly towards local customisations.
- It has some local shortcodes to help embed HTML into pages.
- It uses `2012-01-01T00:00:00Z` as a magic timestamp to indicate pages other than blog posts to allow some customisations - *hacky I know :)*

*Feel free to fork the repo for building your own site with the tech stack above*