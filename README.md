## Purpose

`new-static-lib` initializes a new static library project for Visual
Studio 2010. The project file is configured for static compilation
against standard library (and not its dll'd form) and includes few
other tweaks that I got tired of applying for every new project I
create.

## Usage

In a [msysgit](http://code.google.com/p/msysgit/) shell on Windows
navigate to a place where new project's directory is going to be
and run:
	  
	alex@boxen /n/Projects/coding
	$ new-static-lib foo
	creating directories...
	copying blank project files...
	initializing git repo...
	done

This will create the following directory structure, copy .vcxproj
into `./build`, patch it with unique guids and initialize the git
repo:

	alex@LENOWO /n/Projects/coding
	$ ls -l foo foo/build
	foo:
	total 0
	drwxr-xr-x    2 alex      0 May 30 11:07 build
	drwxr-xr-x    2 alex      0 May 30 11:07 inc
	drwxr-xr-x    2 alex      0 May 30 11:07 src

	foo/build:
	total 5
	-rw-r--r--    1 alex   8766 May 30 11:07 foo.vcxproj
	-rw-r--r--    1 alex    414 May 30 11:07 foo.vcxproj.filters


