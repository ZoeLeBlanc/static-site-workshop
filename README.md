# Static Site Workshop

Last Updated: 2023-03-30

## Overview

*Slides available [here](https://docs.google.com/presentation/d/17MgHFfx2x6ZpIAjfUpqN_nmVWgc0WLBnPmilrggxbs4/edit?usp=sharing).*

1. Discuss minimal computing and static sites
2. Try out writing HTML and discuss how the web works
3. Try out a static site generator
4. Discuss broader tradeoffs and implications


### HTML Exercise

*So what is HTML, actually?*

One key thing to understand is that when you visit a website, you are actually looking at a document (not identical but similar to documents like in the Google Docs or Word document sense). The document in this case is an HTML document, but the principle is essentially the same.

So while in Google Docs, you can write text, in HTML documents, you can also write HTML to help structure how that text appears on the screen.

For example, when we write in Markdown, we use `#` to indicate that the text is a heading. A similar principle applies to HTML.

But rather than symbols, HTML consists of a series of **tags**. Tags have a name, a series of key/value pairs called **attributes**, and some textual content. Attributes are optional.

Let's try an example. Say you wanted to create a website. To start off you might write some very basic text:

```
My first page
```

We can actually try rendering this in a webpage by creating a new HTML document. Create a file in your workspace called `first_page.html` (remember to use `touch`). Open the file in your editor (VSCode or whatever you're using) and add the text above. Then save it and open the file in your browser. You should see the text we wrote!

Now in that same file, try altering the code to include some HTML tags.

```html
<p>My first page!</p>
```

Save it and open the file in your Browser, what do you see? Notice anything different? Probably not!

But we added those tags? So how can we see them...

The trick is to inspect your webpage. To do that let's right click on our page and select `inspect`.

![inspect](https://github.com/ZoeLeBlanc/is310-computing-humanities/blob/gh-pages/assets/images/inspect_pg.png?raw=true)

What we're using is called the Developer Tools Console ([you can find more info on Chrome's version here](https://developers.google.com/web/tools/chrome-devtools/console/) and instructions for [Firefox here](https://developer.mozilla.org/en-US/docs/Tools/Page_Inspector/How_to/Open_the_Inspector)). What we're seeing is called the **source code**.

Now we can see that our tags do exist. But what exactly are they doing and why do they look like that?

![tags](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started/grumpy-cat-small.png)

This diagram is from that same Mozilla docs, where they describe the anatomy of an "HTML element".

> The anatomy of our element is:
>
>- The opening tag: This consists of the name of the element (in this example, p for paragraph), wrapped in opening and closing angle brackets. This opening tag marks where the element begins or starts to take effect. In this example, it precedes the start of the paragraph text.
>- The content: This is the content of the element. In this example, it is the paragraph text.
>- The closing tag: This is the same as the opening tag, except that it includes a forward slash before the element name. This marks where the element ends. Failing to include a closing tag is a common beginner error that can produce peculiar results.
> The element is the opening tag, followed by content, followed by the closing tag.

That's a lot of information, so let's break it down further in our example.

In our HTML page, we created an HTML element using the HTML <p> tag (p means "paragraph"). This example has just one tag in it: a <p> tag. The source code for a tag has two parts, its opening tag (<p>) and its closing tag (</p>). In between the opening and closing tag, you see the tag's contents (in this case, the text says "My first page!").

Let's take a look at some of the more common HTML tags that we can use to create HTML elements [https://www.w3schools.com/tags/ref_byfunc.asp](https://www.w3schools.com/tags/ref_byfunc.asp)

How would we make it into an HTML heading?

```html
<h1>My first page!</h1>
```

Great now what if we wanted to add a link so that you could click on that heading and go to another page (say the iSchool home page <https://ischool.illinois.edu/>)?

Well then we need to add an `attribute`.

![attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started/grumpy-cat-attribute-small.png)

This diagram is also from the Mozilla docs and you can read more about how HTML elements can also have [attributes here](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started#Attributes). Some of the guidelines for using attributes are:

> Attributes contain extra information about the element that won't appear in the content. In this example, the class attribute is an identifying name used to target the element with style information.
>
> An attribute should have:
>
> - A space between it and the element name. (For an element with more than one attribute, the attributes should be separated by spaces too.)
> - The attribute name, followed by an equal sign.
> - An attribute value, wrapped with opening and closing quote marks.

Let's try using the `anchor` tag and `href` attribute to create an HTML element that links to `https://ischool.illinois.edu/`

You can find a list of HTML attributes here [https://www.w3schools.com/tags/ref_attributes.asp](https://www.w3schools.com/tags/ref_attributes.asp)

```html
<h1><a href="https://ischool.illinois.edu/">My first page!</a></h1>
```

How does this new tag change our html page?

Here's another example that we should add to our html page, using the HTML <div> tag:

```html
<div class="header" style="background: blue;">Digital Humanities Tools and Projects</div>
```

In this example, the tag's name is div. The tag has two attributes: class, with value `header`, and style, with value `background: blue;`. The contents of this tag is Digital Humanities Tools and Projects.

Tags can contain other tags, in a hierarchical relationship. For example, here's some HTML to make a bulleted list:

<ul>
  <li>Jekyll</li>
  <li>OpenRefine</li>
  <li>Gephi</li>
</ul>

The `<ul>` tag (ul stands for **unordered list**) in this example has three other `<li>` tags inside of it (li stands for **list item**). The `<ul>` tag is said to be the **parent** of the `<li>` tags, and the `<li>` tags are the **children** of the `<ul>` tag. All tags grouped under a particular parent tag are called **siblings.**

[*HTML's shortcomings by Alison Parrish*](https://github.com/aparrish/dmep-python-intro/blob/master/scraping-html.ipynb)

> HTML documents are intended to add **markup** to text to add information that allows browsers to display the text in different ways---e.g., HTML markup might tell the browser to make the font of the text a particular size, or to position it in a particular place on the screen.

> Because the primary purpose of HTML is to change the appearance of text, HTML markup usually does not tell us anything useful about what the text means, or what kind of data it contains. When you look at a web page in the browser, it might appear to contain a list of newspaper articles, or a table with birth rates, or a series of names with associated biographies, or whatever. But that's information that we get, as humans, from reading the page. There's (usually) no easy way to extract this information with a computer program.

> HTML is also notoriously messy---web browsers are very forgiving of syntax errors and other irregularities in HTML (like mismatched or unclosed tags). For this reason, we need special libraries to parse HTML into data structures that our Python programs can use, libraries that can make a "good guess" about what the structure of an HTML document is, even when that structure is written incorrectly or inconsistently.

For more information, read through this [introduction from Mozilla on HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started#What_is_HTML).

So now that we understand what HTML is, how does this relate to the web and static sites?


#### What is the Web?

[**From Wikipedia:**](https://en.wikipedia.org/wiki/World_Wide_Web)
"The World Wide Web (WWW), commonly known as the Web, is an information system where documents and other web resources are identified by Uniform Resource Locators (URLs, such as <https://www.example.com/>), which may be interlinked by hypertext, and are accessible over the Internet.[1][2] The resources of the WWW are transferred via the Hypertext Transfer Protocol (HTTP) and may be accessed by users by a software application called a web browser and are published by a software application called a web server."

![http](https://2.bp.blogspot.com/_4l9wMe5bbSk/TMpvwVcMT3I/AAAAAAAAAK4/sCEjRQCkF1o/s1600/Client+Server+communication.GIF)

*What does this mean exactly?*

When we type a url for a webpage (say google.com), we're actually sending an **HTTP request** to a **server** that hosts the actual HTML files and data. If the server decides that our request is ok (200), then it will give us access to the webpage.

![404 page](https://user-images.githubusercontent.com/2938045/56276896-af93b580-6103-11e9-9885-74981a49a5ae.png)

If you've ever seen an error message when you go to a webpage saying the page doesn't exist, that means that you received a 404 error, which is a type of status code you get back from an HTTP request.

## What is HTTP?

**Courtesy of [Julia Evans' Zine](https://jvns.ca/blog/2019/09/12/new-zine-on-http/)**

![What is HTTP?](https://pbs.twimg.com/media/EAiEGSgXsAELERE?format=jpg&name=large)

This comic explains a bit more in depth what is comprised of an HTTP request. We also want to have a sense of what types of status codes we can get back from a request.

![HTTP Status Codes](https://pbs.twimg.com/media/D-bI-xyWkAAY0Qb?format=jpg&name=large)

Finally, in our example we used the `GET` method when calling a webpage (using `request.get()`), but there's multiple methods that we can use to send data across the web.

![HTTP Request Methods](https://pbs.twimg.com/media/EB8dt0CWsAAET4b?format=jpg&name=large)

![How to learn more](https://pbs.twimg.com/media/ECvlQX1W4AE9EgP?format=jpg&name=large)

[More information about HTTP from Mozilla Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

If you're interested in the longer history of the internet checkout this timeline from the Computer History Museum, covering the history from the 1960s to the 1990s [https://www.computerhistory.org/internethistory/](https://www.computerhistory.org/internethistory/).
### What is the Web?

[**From Wikipedia:**](https://en.wikipedia.org/wiki/World_Wide_Web)
"The World Wide Web (WWW), commonly known as the Web, is an information system where documents and other web resources are identified by Uniform Resource Locators (URLs, such as <https://www.example.com/>), which may be interlinked by hypertext, and are accessible over the Internet.[1][2] The resources of the WWW are transferred via the Hypertext Transfer Protocol (HTTP) and may be accessed by users by a software application called a web browser and are published by a software application called a web server."

![http](https://2.bp.blogspot.com/_4l9wMe5bbSk/TMpvwVcMT3I/AAAAAAAAAK4/sCEjRQCkF1o/s1600/Client+Server+communication.GIF)

*What does this mean exactly?*

When we type a url for a webpage (say google.com), we're actually sending an **HTTP request** to a **server** that hosts the actual HTML files and data. If the server decides that our request is ok (200), then it will give us access to the webpage.

![404 page](https://user-images.githubusercontent.com/2938045/56276896-af93b580-6103-11e9-9885-74981a49a5ae.png)

If you've ever seen an error message when you go to a webpage saying the page doesn't exist, that means that you received a 404 error, which is a type of status code you get back from an HTTP request.


### Static Site Exercise

1. First, I will be trying to follow the instructions in this tutorial <https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll>.
2. But, I also already have a version of a static site set up here as well, so we can try altering that one as well.
3. Finally, if we have time we might try embedding a map into our static site.

#### Deep Dive Into Static Sites

If you are curious about static sites in different programming languages, here's an overview of how to setup a static site in a few different languages.

Pelican:

```bash
pip install pelican
```

Jekyll:

```bash
gem install jekyll
```

Hugo:

```bash
brew install hugo
```

Gatsby:

```bash
npm install -g gatsby-cli
```

The next step is to find a tutorial or look at the documentation for how to setup a project locally. This step will usually involve typing a command in your terminal shell that tells the static site generator to create a new project.

Pelican:

```bash
pelican-quickstart
```

Jekyll:

```bash
jekyll new-project
```

Hugo:

```bash
hugo new site quickstart
```

Gatsby:

```bash
gatsby new gatsby-site
```

You'll then see a bunch of activity in your terminal and when it's completed you'll have an entire project structure in what was once an empty directory.

Pelican:

```python3
yourproject/
├── content
│   └── (pages)
├── output
├── tasks.py
├── Makefile
├── pelicanconf.py       # Main settings file
└── publishconf.py       # Settings to use when ready to publish
```

Jekyll:

```bash
.
├── _config.yml
├── _data
|   └── members.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── on-simplicity-in-technology.md
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
|   ├── _base.scss
|   └── _layout.scss
├── _site
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid front matter
```

Gatsby:

```javascript
/
|-- /.cache
|-- /plugins
|-- /public
|-- /src
    |-- /pages
    |-- /templates
    |-- html.js
|-- /static
|-- gatsby-config.js
|-- gatsby-node.js
|-- gatsby-ssr.js
|-- gatsby-browser.js
```

Almost all of them have a configuration file with top level information about the project.

Pelican:

```bash
nano pelicanconf.py
```

Jekyll:

```bash
nano _config.yaml
```

Hugo:

```bash
nano config.toml
```

They have a folder(s) where you edit the content of your blog posts, pages, projects, etc... that is usually in the form of markdown files.

Pelican or Hugo

```bash
cd content
ls
```

Jekyll:

```bash
cd posts
```

They have folders where you store images, files, etc... as assets.

Pelican:

```python3
content
├── images
│   └── han.jpg
├── pdfs
│   └── menu.pdf
└── pages
    └── test.md
```

Hugo:

```go
.
└── content
    └── about
    |   └── index.md  // <- https://example.com/about/
    ├── posts
    |   ├── firstpost.md   // <- https://example.com/posts/firstpost/
    |   ├── happy
    |   |   └── ness.md  // <- https://example.com/posts/happy/ness/
    |   └── secondpost.md  // <- https://example.com/posts/secondpost/
    └── quote
        ├── first.md       // <- https://example.com/quote/first/
        └── second.md      // <- https://example.com/quote/second/
```

They have html files that you can edit to customize layouts of your web pages, and folders that contain CSS and JavaScript files.

Pelican:

```python3
├── static
│   ├── css
│   └── images
└── templates
    ├── archives.html         // to display archives
    ├── period_archives.html  // to display time-period archives
    ├── article.html          // processed for each article
    ├── author.html           // processed for each author
    ├── authors.html          // must list all the authors
    ├── categories.html       // must list all the categories
    ├── category.html         // processed for each category
    ├── index.html            // the index (list all the articles)
    ├── page.html             // processed for each page
    ├── tag.html              // processed for each tag
    └── tags.html             // must list all the tags. Can be a tag cloud.
```

Jekyll:

```bash
cd layouts #or includes
cd sass
```

They have themes that you can install to change the styling of your website.

Pelican:

```bash
pelican-themes --list
```

Hugo:

```bash
# Download the theme
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
# Note for non-git users:
#   - If you do not have git installed, you can download the archive of the latest
#     version of this theme from:
#       https://github.com/budparr/gohugo-theme-ananke/archive/master.zip
#   - Extract that .zip file to get a "gohugo-theme-ananke-master" directory.
#   - Rename that directory to "ananke", and move it into the "themes/" directory.
# End of note for non-git users.

# Edit your config.toml configuration file
# and add the Ananke theme.
echo 'theme = "ananke"' >> config.toml
```

And finally, they have commands that you can use to build the site:

```bash
pelican /path/to/your/content/ [-s path/to/your/settings.py]
```

Jekyll:

```bash
bundle exec jekyll build
```

Hugo:

```bash
hugo -D
```

Gatsby:

```build
gatsby build
```

And host the site locally:

Python:

```bash
pelican --listen
```

Jekyll:

```bash
bundle exec jekyll serve
```

Hugo:

```bash
hugo server -D
```

Gatsby:

```bash
gatsby develop #or serve
```

#### Hosting and Testing Static Sites

- Github
  - [Hosting your static site through Github Pages (this example is with jekyll)](https://help.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll)

  - [Configuring a custom domain with Github Pages and a static site](https://help.github.com/en/github/working-with-github-pages/configuring-a-custom-domain-for-your-github-pages-site)

- Netlify (Better for larger projects with a team)
  - [Netlify docs](https://docs.netlify.com/configure-builds/get-started/)
  - Provides continuous deployment while you're developing so that you can share URLs
  - [Github Pages vs Netlify](https://www.netlify.com/github-pages-vs-netlify/)

- Testing and TravisCI
  - Used for testing your code before you push your code to Github *and* for making sure your code is not broken when it's hosted
  - [Travis CI](https://travis-ci.org/) and [docs](https://docs.travis-ci.com/)
  
```bash
#!/usr/bin/env bash
set -e # halt script on error

# bundle exec jekyll build
# # bundle exec htmlproofer ./_site
# # to exclude external sites
# bundle exec htmlproofer ./_site --disable-external
bundle exec jekyll build && bundle exec htmlproofer ./_site \
  --assume-extension \
  --empty-alt-ignore \
  --disable-external \
  --alt-ignore '/.*/' \
  --allow-hash-href \
  --only-4xx \
  --http-status-ignore 429,403,404,410 \
  --file-ignore /.*\/node_modules\/.*/ \

  # --url-ignore '/http://www.gutenberg.org/*/','/https://github.com/programminghistorian/jekyll/(commits|blob)/*/','/\#/',"/espanol/","/deprecated/",'/collection.britishmuseum.org/','/analytics.hathitrust.org/'
```

#### Static Site Examples

Almost every programming language has a static site generator, if not multiple.

Check out the [list of top static site generators](https://www.staticgen.com/) and [curated list of static site resources](https://github.com/myles/awesome-static-generators) to find out about what's available.

The only way I've ever learned anything about coding is by coding (original I know!).

Today the goal is for you try and get at least one, but ideally two of these static site generators up and running on your local computer (alternatively depending on bandwidth we can talk more too!).

1. Jekyll and Ruby

Jekyll is the workhorse of DH, but has become less popular in recent years in the broader development community.

- [How to quickstart with Jekyll](https://jekyllrb.com/docs/installation/macos/) and [tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/)

- [Jekyll Github Repo](https://github.com/jekyll/jekyll)
  
- [Jekyll Themes](http://jekyllthemes.org/)

- [Jekyll style guide](https://ben.balter.com/jekyll-style-guide/)

- [Setting up a GitHub Pages site with Jekyll](https://help.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll)

- [Jekyll’s documentation on migrating existing websites](https://import.jekyllrb.com/docs/home/)

- [Ben Balter’s WordPress plugin for exporting data from WordPress into Jekyll](https://wordpress.org/plugins/jekyll-exporter/)

- [Exitwp, a Python script developed by Thomas Frössman](https://github.com/thomasf/exitwp)

- [Programming Historian's Jekyll Lesson](https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages) and [newly proposed lesson](https://programminghistorian.github.io/ph-submissions/lessons/collaborative-blog-with-jekyll-github)

Example sites with Jekyll

- [Scholars' Lab website](https://scholarslab.lib.virginia.edu/) and [github repo](https://github.com/scholarslab/scholarslab.org)

- [Programming Historian](https://programminghistorian.org/) and [github repo](https://github.com/programminghistorian/jekyll)
  
- [Wax a Jekyll version of Omeka](https://minicomp.github.io/wax/) and [Ed a Jekyll theme for minimal computing](http://elotroalex.github.io/ed/)
  
1. Pelican and Python

- [Pelican Github Repo](https://github.com/getpelican/pelican)

- [Pelican Quickstart docs](https://docs.getpelican.com/en/stable/quickstart.html)

- [Pelican Themes](https://docs.getpelican.com/en/stable/pelican-themes.html)

Example sites with Pelican:

- [Personal Website example](https://kevinyap.ca/) and [github repo](https://github.com/iKevinY/iKevinY.github.io)
- [Andrew Heiss website](https://www.andrewheiss.com/) and [github repo](https://github.com/andrewheiss/ath-pelican)

1. Gatsby and React

- [Gatsby tutorials](https://www.gatsbyjs.org/tutorial/)
- [Gatsby Github Repo](https://github.com/gatsbyjs/gatsby)
- [Gatsby with Github Pages](https://www.gatsbyjs.org/docs/how-gatsby-works-with-github-pages/)
- [Awesome Gatsby Resources](https://github.com/prayash/awesome-gatsby)
- [Gatsby Themes](https://www.gatsbyjs.org/docs/themes/)

Example sites with Gatsby

- [Gatsby demo site](https://cara.lekoarts.de/) and [github repo](https://github.com/LekoArts/gatsby-starter-portfolio-cara)
- [Tania Rascia's personal website](https://www.taniarascia.com/) and [github repo](https://github.com/taniarascia/taniarascia.com)

1. Hugo and Go

- [Hugo quick start](https://gohugo.io/getting-started/quick-start/)
- [Hugo documentation](https://gohugo.io/documentation/) and [github repo](https://github.com/gohugoio/hugo)
- [Hugo Themes](https://themes.gohugo.io/)
  
Example sites with Hugo

- [Jason Heppler's personal website](https://github.com/hepplerj/jasonheppler.org)
- [Grant Wythoff's personal website](https://wythoff.net/)
