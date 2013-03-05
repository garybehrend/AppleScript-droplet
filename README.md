![AppleScript icon](http://i.imgur.com/tnVUAtM.png)
AppleScript-droplet
===================

A template for creating Droplets for Mac OS X that will pass dropped files to an embedded script

How to use
==========

1. Replace the script.sh file in "Show Package Contents" Contents/Resources/Scripts with the script you want run
2. There is no step 2

Making git binary friendly
==========================

Because AppleScript stores its code in a binary format, it is difficult to use with version control. The included `.gitconfig` can be added to your .git/config to allow text conversion before diffing. It complements the included .gitattributes file

Add it to your .git/config like so:

    cat .gitconfig >> .git/config

Alternatively, you can use a git 1.7.10+ style include by adding these lines to your .git/config

    [include]
        path = .gitconfig

Sample scripts
==============

file.sh
-------
Just uses the BSD command "file" to return info about each of the dropped files.
A copy of this is used as the default script.sh in AppleScript-droplet.app/Contents/Resources/Scripts/

dropbox.sh
----------
Uploads each of the dropped files to a configurable folder in Dropbox and returns (and copies) the public URL (assuming you have configured it to use a public folder).
Requires [Dropbox-Uploader] be installed and configured in advance.

imgur.sh
--------
Uploads each of the dropped files to imgur and returns (and copies) the public URL.
Currently these are anonymous. (patches welcome)

Using the sample Scripts
========================

Dropbox
-------
Create a new Dropbox Droplet like so:

    cp -r AppleScript-droplet.app Dropbox-droplet.app
    cp scripts/dropbox.sh Dropbox-droplet.app/Contents/Resources/Scripts/script.sh

Imgur
-----
Create a new Imgur Droplet like so:

    cp -r AppleScript-droplet.app Imgur-droplet.app
    cp scripts/imgur.sh Imgur-droplet.app/Contents/Resources/Scripts/script.sh

[Dropbox-Uploader]: https://github.com/andreafabrizi/Dropbox-Uploader
