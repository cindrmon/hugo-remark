# Hugo Remark + SASS theme

What is **hugo**?

[Hugo](http://gohugo.io/) is a great static site generator built in Go.

What is **remark.js**?

[RemarkJS](https://github.com/gnab/remark) is a simple slide show generator from markdown files. It is not to be confused with a similar project called [Remark](https://github.com/remarkjs/remark), which also deals stuff with markdown, but does **not** primarily make slideshows from markdown.

What is **sass**?
[sass](https://sass-lang.com/), or Syntactically Awesome Stylesheets, is basically similar to CSS, but with more functionality built on top of it. It is also referred to 'CSS with superpowers'.

## About this theme

This theme creates a set of presentations using hugo to generate a set of slideshows generated from markdown content. For styling, this uses `sass` primarily to add more functionality to css when making custom themes out of it.

## Why use Hugo and not just remarkJS?

RemarkJS doesn't come with a way of serving files or reload them on changes. Also it requires you to write all your slides on just one html page.

*By using Hugo:*

- You can serve your slideshows on localhost easily
- Hugo will watch for changes and reload immediatelly
- You can write your slides on different markdown files, Hugo will concatenate them

## Installation

Follow the hugo [installation intructions](http://gohugo.io/). On mac simply do `brew install hugo`

## Requirements

- Hugo Extended version 0.99.x and above
  - [For Debian/Ubuntu](https://github.com/gohugoio/hugo/releases/download/v0.99.1/hugo_extended_0.99.1_Linux-64bit.deb)
  - [For Other Linux Distros](https://github.com/gohugoio/hugo/releases/download/v0.99.1/hugo_extended_0.99.1_Linux-64bit.tar.gz) or search `hugo-extended` on your local package manager.
  - [For MacOS (Intel)](https://github.com/gohugoio/hugo/releases/download/v0.99.1/hugo_extended_0.99.1_macOS-64bit.tar.gz)
  - [For MacOS (M1)](https://github.com/gohugoio/hugo/releases/download/v0.99.1/hugo_extended_0.99.1_macOS-ARM64.tar.gz)
  - [For Windows](https://github.com/gohugoio/hugo/releases/download/v0.99.1/hugo_extended_0.99.1_Windows-64bit.zip)

## How to use

### Generating the site

```bash
hugo new site /path/to/presentations
cd /path/to/presentations
```

### Install this theme

Inside the presentations folder do:

```bash
git clone https://github.com/sporto/hugo-remark themes/remark
```
Add to config file
```
theme = "remark"
```
### Generate new slideshows

Inside the presentations folder do:

```bash
hugo new slideshow.md
```

Note that each markdown file is a single slideshow, so adding multiple slides, you follow the [remarkjs syntax](https://github.com/gnab/remark/wiki/Markdown) of doing so.

Here is an example:
```
## This is Slide 1

---

## This is Slide 2

---

## This is Slide 3

---

...

```

Slideshows will be created on `./content` subfolder.
Edit the slides using markdown.

### Serve your slideshows

To show your slideshows run:

```bash
hugo server --buildDrafts --watch
```

And open the given url in a browser, e.g. `http://localhost:1313`

### Custom styles

You can add custom styles to your slides:

- Create a `custom.scss` file in the path `./assets/sass/` directory, which acts as the `main.scss` file for your custom styles. Create the `assets` folder if necessary.

### Custom JS on the head

- Create a file `./layouts/partials/custom_head.html`
- Link `custom_head.html` in `head.html` by adding `{{ partial "custom_head.html" }}` to where you want.
- In this file add a link to the JS libraries you want to load e.g.
  `<script src="https://code.jquery.com/jquery-2.1.1.min.js"></script>`
  `<script src="/js/[some-name].js"></script>`
- Add your JS in `./static/js/[some-name].js`


### Custom JS on the footer

You can also add custom JS on the footer, this is loaded after the remark initialisation. This is useful for adding custom behaviour to your presentation.

- Create a file `./layouts/partials/custom_footer.html`
- Link `custom_footer.html` in `footer.html` by adding `{{ partial "custom_footer.html" }}` to where you want.
- Add a JS script link there or just write the JS using `script` tags
