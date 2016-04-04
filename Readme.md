This is the source repository for [my Github-hosted blog](http://traveller42.github.io/).

In has the source files used to build the site using [Hugo](http://gohugo.io/).

Eventually, this will include the script I use to deploy the site.  After that, I
intend to look into using a CI environment to autobuild the site whenever I
push a new commit to this branch.

The **source** branch (the current branch) only has my content.  It has a directory
for the theme I am currently using, [blackburn](http://themes.gohugo.io/blackburn/),
which will have to be copied, or cloned, into any build environment.

The **master** branch has the built files.  This allows the Github magic to make
the site work.
