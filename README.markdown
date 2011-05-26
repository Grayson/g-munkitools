# What are g-munkitools?

I've recently started using [munki](http://code.google.com/p/munki/) as a managed software distribution tool.  Although I'm generally very fond of munki and the tools that are provided, I kept feeling like there were a few things that it was missing out on.  I'd love to be able to run arbitrary scripts using munki as the script distribution platform.  I'd also like to install arbitrary files, not just applications and packages.  Sure, I could bundle them into a package, but munki can do it, so why shouldn't it?

These tools are small shell script hacks that I've put together to expand on what munki already does.

## munkiitem

`munkiitem` is a shell script designed to allow munki to install files and folders to arbitrary locations.  In a nutshell, it creates a disk image for the given item in the current working directory and then generates an appropriate pkginfo file that instructs munki how to place the file.

	munkiitem -f /path/to/file [-d /path/to/destination] [-n Name]
	-f -- A path, relative or absolute, to the file that you'd like to install with munki.
	-d -- An absolute path to where the file should be installed.  
		  If not provided, the path of the file is provided.
	-n -- The name used by munki, useful if different than the filename.

## munkiscript

`munkiscript` allows you to distribute and run a shell script (or group of scripts) using munki.  It creates a disk image from the script as well as an associated pkginfo file.  The shell script is installed into a unique folder inside of /Library/Managed Installs/Scripts.  The pkginfo file has an associated post install script that runs the script.  `munkiscript` only takes one argument, a path to a script for folder of scripts.  At present, Shell (*.sh), Python (*.py), Ruby (*.rb), and Perl (*.pl) scripts can be run using this technique.

	munkiscript /path/to/script

## Installation

To install, simply download these script and place them into your $PATH.

## Contact information

[Grayson Hansard](mailto:info@fromconcentratesoftware.com)  
[From Concentrate Software](http://www.fromconcentratesoftware.com)  
[http://github.com/Grayson](http://github.com/Grayson)