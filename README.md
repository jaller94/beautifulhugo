# Beautiful Hugo - An adaptation of the Beautiful Jekyll theme

![Beautiful Hugo Theme Screenshot](https://github.com/halogenica/beautifulhugo/blob/master/images/screenshot.png)

## Changes compared to halogenica/beautifulhugo
- Removed: Many JavaScript features
  - Highlight
    - `.Site.Params.useHLJS` has been removed
  - Katex - rendering LaTeX math equations
  - Mermaid
  - PhotoSwipe - image gallery
  - Recaptcha
  - Staticman
- Removed: Content from external URLs
  - `.Site.Params.selfHosted` has been removed and become the default
  - Disqus - comments
  - Google Search modal
   - `.Site.Params.gcse` is now broken
- Removed: Some obsolete HTML headers
  - SEO meta tags specific to Twitter / X
  - `<meta http-equiv="X-UA-Compatible" content="IE=edge">`
- Removed: Script for random emoticon on the 404 page
- Changed: Add `aria-hidden="true"` for the emoticon on the 404 page
- Changed: Show dates and modification dates of articles
- Changed: Hide preview content of an article
- Changed: Fonts and use of font-weight
  - Don't make titles larger on small screens
  - Remove most `font-weight: 800;`
  - Only two font-family definitions: headings and everything else
- Added:`.Params.toc` will show a Table of Content in an article

### Should be upstream
- Changed: Article application/ld+json in seo/structured/article.html
- Changed: Post application/ld+json in seo/structured/post.html
- Changed: Use `<main>` instead of `role="main"`
- Fixed: BreadcrumbList application/ld+json in seo/structured/breadcrumb.html
- Fixed: Added :focus-within on many styles that had :hover for keyboard accessibility
- Fixed: Keyboard navigation for the language dropdown

## Live demo

See https://chrpaul.de

## Installation

Install Hugo and create a new site. See [the Hugo documentation](https://gohugo.io/getting-started/quick-start/) for details.

### Git Submodule

Add Beautifulhugo as git submodule:

    $ git submodule add https://github.com/halogenica/beautifulhugo.git themes/beautifulhugo

### Hugo module

Initialize your site as hugo module:

    $ hugo mod init github.com/USERNAME/SITENAME

Add Beautifulhugo module as a dependency of your site:

    $ hugo mod get github.com/halogenica/beautifulhugo

### Site preview

Copy the content of `exampleSite` at the root of your project:

    cp -r themes/beautifulhugo/exampleSite/* . -iv

If you installed Beautifulhugo as hugo module, set your theme in your config file (hugo.toml):

    [[module.imports]]
      path = "github.com/halogenica/beautifulhugo"

Start Hugo:

    hugo serve

## Extra Features

### Responsive

This theme is designed to look great on both large-screen and small-screen (mobile) devices.

### Syntax highlighting

This theme has support for either Hugo's lightning fast Chroma, or both server side and client side highlighting. See [the Hugo docs for more](https://gohugo.io/content-management/syntax-highlighting/).

#### Chroma - New server side syntax highlighting

To enable Chroma, add the following to your site parameters:

```
pygmentsCodeFences = true
pygmentsUseClasses = true
```

Then, you can generate a different style by running:

```
hugo gen chromastyles --style=trac > static/css/syntax.css
```

### Site Disclaimer

If you need to put a Disclaimer on your website (e.g. "My views are my own and not my employer's"), you can do so via the following:

* Uncomment and edit the `disclaimerText` parameter in `config.toml`.
* If you need to adjust the disclaimer's styling, modify the declarations within the `footer div.disclaimer` selector in `static/css/main.css`.

> The code for the disclaimer text is in `layouts/partials/footer.html`.  Moving this code block to another partial file (or relocating it within `footer.html`) will require changes to the css selector in `main.css` as well.

### Commit SHA on the footer

If the source of your site is in a Git repo, the SHA corresponding to the commit the site is built from can be shown on the footer. To do so, two site parameters `commit` has to be defined in the config file `config.toml`:

```
enableGitInfo = true
[Params]
  commit = "https://github.com/<username>/<siterepo>/tree/"
```

See at [vincenttam/vincenttam.gitlab.io](https://gitlab.com/vincenttam/vincenttam.gitlab.io) for an example of how to add it to a continuous integration system.

### Multilingual

To allow Beautiful Hugo to go multilingual, you need to define the languages
you want to use inside the `languages` parameter on `config.toml` file, also
redefining the content dir for each one. Check the `i18n/` folder to see all
languages available.

```toml
[languages]
  [languages.en] 
    contentDir = "content/en" # English
  [languages.ja]
    contentDir = "content/ja" # Japanese
  [languages.br]
    contentDir = "content/br" # Brazilian Portuguese
```

Now you just need to create a subdir within the `content/` folder for each
language and just put stuff inside `page/` and `post/` regular directories.
```
content/      content/      content/  
└── en/       └── br/       └── ja/ 
    ├── page/     ├── page/     ├── page/
    └── post/     └── post/     └── post/

```

### Self Hosted assets for GDPR / EU-DSGVO compliance

With default settings, visiting to a website using Beautifulhugo connects also to remote services like google fonts or jsdelivr to embed fonts, js and other assets.

To avoid this, set the following param in config.toml:

```
[Params]
  selfHosted = true
```

### Extra shortcodes

There are two extra shortcodes provided (along with the customized figure shortcode):

#### Details

This simply adds the html5 detail attribute, supported on all *modern* browsers. Use it like this:

```
{{< details "This is the details title (click to expand)" >}}
This is the content (hidden until clicked).
{{< /details >}}
```

#### Split

This adds a two column side-by-side environment (will turn into 1 col for narrow devices):

```
{{< columns >}}
This is column 1.
{{< column >}}
This is column 2.
{{< endcolumns >}}
```

### Social Media Icons

In order to show social media icons in the footer, add a section like this to your `config.yaml`.  You can see the full list of supported social media sites in `data/beautifulhugo/social.toml`.

```yaml
author: 
  name: "Author Name"
  website: "https://example.com"
  github: halogenica/beautifulhugo
  twitter: username
  discord: 96VAXXvjCB
```

## About

This is an adaptation of the Jekyll theme [Beautiful Jekyll](https://deanattali.com/beautiful-jekyll/) by [Dean Attali](https://deanattali.com/aboutme#contact). It supports most of the features of the original theme, and many new features. It has diverged from the Jekyll theme over time, with years of community updates.

## License

MIT Licensed, see [LICENSE](https://github.com/halogenica/Hugo-BeautifulHugo/blob/master/LICENSE).
