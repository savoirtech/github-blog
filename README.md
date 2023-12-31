# Setting up Blogs on Github

Blogging on technical topics? Having trouble getting code snippets
formatted correctly?

How about putting your articles on GitHub and sharing the sources with
the article? Better yet - deliver working code with the article, in the
same repository, and really drive the point home with your readers.

Let’s get started.

## Overview of the Process

- Create a Repository for the Article

- Write the Article in Ascii Doctor

- Convert to GitHub Markdown

- Commit and Push

## Create a Repository for the Article

Use GitHub’s UI to create the repository. Nothing special is needed
here.

Note a major benefit to using a GitHub repository is the ease with which
your readers will be able to try out your code. And if they want to
build on it, they can easily fork the repository as well!

Add the discussions section, pull requests, and more - collaboration and
building community is built-in.

## Write the Article in Ascii Doctor

Asciidoctor is a convenient format as it can easiy be converted into
PDF, HTML, DOCX, and even GitHub Markdown.

We chose it before deciding to use GitHub to host the articles. Finding
the conversion from Ascii Doctor to GitHub Markdown was a welcome find,
eliminating the concerns with attempting to embed HTML in GitHub
Markdown pages.

**WARNING** when converting to GitHub markdown, the title (top-level
heading - `=`) is dropped by the `pandoc` conversion. To work-around
this issue, I recommend avoiding the top-level heading and starting with
a second-level heading `==`.

## Convert to GitHub Markdown

Here is a Makefile that is included in this article’s repository; feel
free to copy it if you like:

``` text
.PHONY: all

all: README.md

README.md: article.adoc
    asciidoctor -b docbook article.adoc
    pandoc -f docbook -t gfm article.xml -o README.md
```

**NOTE** tabs are meaningful in Makefiles - make sure to retain the tab
characters when copying the file (all of the indented lines in the
example above use tabs).

## Commit and Push

``` shell
# Clone via SSH
$ git clone git@github.com:savoirtech/github-blog.git
# OR HTTPS
$ git clone https://github.com/savoirtech/github-blog.git
$ cd github-blog
# Use the "main" branch
$ git branch checkout -b main

# Add Source Files...

$ make
$ git add Makefile article.adoc README.md
$ git commit
$ git push --set-upstream origin main
```

## Congratulations!

The repository is now ready for your readers!

Wrap-up idea(s):

- Enable discussions for the repository (Settings →
  Features:Discussions)

# About the Authors

[Arthur
Naseef](https://github.com/savoirtech/blogs/blob/main/authors/ArthurNaseef.md)

\(c\) 2023 Savoir Technologies
