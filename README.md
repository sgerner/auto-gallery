# auto-gallery
Bash script to automatically generate thumbnails and gallery HTML on file system changes.

View [demo](https://StevenGerner.com/Photos)

# Overview
A little script to help automate the process of creating a flat single page photo gallery. This was originally designed for [Ghost Blog](https://ghost.org/), but could easily be modified for a standalone gallery page or integration into another content management system. The generated HTML is designed for use with [fancybox3](https://fancyapps.com/fancybox/3/) as a lightbox gallery. This implementation of the script assumes [incron, the inotify cron system](http://inotify.aiken.cz/?section=incron&page=about&lang=en) initaites the script upon file system changes in a monitored directory; however, the script can be called by any means (e.g. cron, command line) as long as the expected arguments are passed.

When images are added to a monitored directory, incron will call the script to generate a thumbnail and append the relavent HTML to the end of the gallery file.

When images are deleted from a monitored directory, incron will call the script to delete the associated thumbnail and HTML.

# Dependencies
1. Linux Distro for basic commands (e.g. sed, rm, echo)
2. [Imagemagick](http://imagemagick.org/script/index.php) for thumbnail generation.

# Arguments
The script accepts three arguments
1. Path to base directory
1. File initiating event, e.g. image that needs to be added or removed from the gallery)
1. Event. May be either IN_CREATE, adding an image to the gallery, or IN_DELETE, removing an image from the gallery.

# Assumed File Structure
Please modify your file structure 
- / : monitored directory
- /core : generated HTML
- /t : Thumbnails
- Script may be located anywhere as long as the path argument that is passed when script is invoked refers to / (directory base)

# Example Gallery in a Ghost Blog
[Example Gallery](https://stevengerner.com/photos/)

# Instructions for Integrating Into Ghost
Documentation for one method of integrating this script with Ghost and setting up an automated photo gallery may be found at: https://stevengerner.com/automatic-photo-gallery-with-ghost-blog/
