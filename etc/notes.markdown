These are notes from this Markdown investigation.

First are the known issues. Then are notes with links.

# Known Issues #

1. Image inluded but appears in the wrong spot in the generated PDF.
2. Font not available on all OSs
3. The unpaired header indicator format *doesn't work* for h4 and h5 in the PDF generation.  That is

     #### This heading will render properly in PDF ####

works, whereas

     #### This heading looks bad in PDF

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

# Fighting with Latex #

When the makepdfs script fails, then I run the makepdf script in the latex directory, as in

    makepdf en -d

With that debug flag, usually get worthwhile debug output as to what the problem is.

## Backslashes ##

So far, the problem has been unescaped backslashes, as in documentation of setting paths in Windows.  Again, backslashes as path delimiter in Windows was an incredibly bad idea.  (Does Windows now accept forward-slash delimited paths sufficiently well that the documentation could simply use that and avoid the pain?)

Note that these are problems in the makepdfs build (in Latex) rather than in Markdown itself -- Markdown and Github seem perfectly happy to cope with backslashes in the content.



# Helpful #

[Daring Fireball Markdown syntax guide]



[Daring Fireball Markdown syntax guide]: http://daringfireball.net/projects/markdown/syntax



