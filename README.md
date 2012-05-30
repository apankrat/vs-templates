## Purpose

`new-static-lib` initializes a new static library project for Visual
Studio 2010. The project file is configured for static compilation
against standard library (and not its DLL form) and includes few
other tweaks that I got tired of applying manully to every new project 
I create.

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

This will create the following directory structure, copy `.vcxproj`
into `./build`, patch it with unique guids and initialize the git
repo:

	alex@LENOWO /n/Projects/coding
	$ find foo
	foo
	foo/.git
	...
	foo/build
	foo/build/foo.vcxproj
	foo/build/foo.vcxproj.filters
	foo/inc
	foo/src

Public headers are to go into `inc` and the sources -
into `src`. 

Additionally, the project is configured to put all temporary build 
files into `./build/tmp` and the actual `.lib` - into `./build/out`, 
sorting them into the platform/config subdirectories as follows:

	alex@LENOWO /n/Projects/coding
	$ find foo/build -type d
	...
	foo/build/out/foo/win32-debug
	foo/build/out/foo/win32-release
	foo/build/out/foo/x64-debug
	foo/build/out/foo/x64-release
	...
	foo/build/tmp/foo/win32-debug
	foo/build/tmp/foo/win32-release
	foo/build/tmp/foo/x64-debug
	foo/build/tmp/foo/x64-release

