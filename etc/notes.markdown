These are notes from this Markdown investigation.

First are the known issues. Then are notes with links.

# Known Issues #

1. Image inluded but appears in the wrong spot in the generated PDF.
2. Font not available on all OSs

# Starting point #

Based on  <https://github.com/progit>

# Font #

Font Helvetica wasn't available on my Ubuntu environment -- switched to a font available in Ubuntu, but I bet that means it won't work on other OSs.

# Handling of Images #

## Understanding the Pro Git example ##

It look like Pro Git's inclusion of images is handled via undefined proprietary post-processing. 

[This page about PanDoc Markdown support](http://johnmacfarlane.net/pandoc/epub.html) describes how to translate from those proprietary post-processing include instructions to DocBook style includes.


## Making images appear in GitHub-rendered previews of Markdown ##

Unclear how those image inclusion Markdown syntax are supported, if at all on GitHub's preview rendering of the Markdown.

Here's an example of using an <img> tag referencing a raw image. <https://raw.github.com/imatix/gitdown/master/README.md>

[Looks like](https://groups.google.com/forum/#!topic/github/T3X1iadPH14) one can reference raw images as hosted by GitHub.  Not clear that it's a good move or even within terms of service at scale, but should be acceptable to at least mess with this.


# Hosting of static documentation site #

Looks like Github can host website in a magic gh-site folder.  Process to build from Markdown documentation source to static HTML and sync into a gh-site directory so that Github itself hosts the built CAS documentation?

# Helpful #

[Daring Fireball Markdown syntax guide]



[Daring Fireball Markdown syntax guide]: http://daringfireball.net/projects/markdown/syntax



