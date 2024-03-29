# Emacs Source
## root
### doc/
#### emacs/
- holds the source code for the Emcas Manual.
#### lispintro
- holds the source code for the Introduction to Programming in Emacs Lisp manual
#### lispref
- holds the source code for the Emacs Lisp reference manual.
### etc/
- holds miscellaneous architecture-independent data files Emacs uses, like the tutorial text and tool bar images.
- several other files, named in capital letters, which you might consider looking at when installing GNU Emcas.
  
#### PROBLEMS
- information on many common problems that occur in building, installing and running Emacs.
#### NEWS
- information on new features and other user-visible changes in recent versions of Emacs
### src/
- holds the C code for Emacs.
  it contains the Emacs Lisp interpreter and its primitives, the redisplay code, and some basic editing functions.
- contains the source files for the C component of GNU Emacs.
  Nothing is needed in this directory once it is built and instaled.

#### emacs.c
### leim/
- holds the original source files for the generated files required to type international characters that can't be directly produced by your keyboard.
### lib/
- holds source codes for libraries used by Emacs and its utilities
### lib-src/
- holsds the source code for some utility programs for use by or with Emacs, like movemail and etags.
### lisp/
- holsd the Emacs Lisp code for Emacs (most everything else)
### ?info/
### msdos/
- holds configuration files for compiling Emacs under MS-DOS.
### nextstep/
- for compiling the Nextstep port of Emacs, GNUstep and Mac OS X Cocoa.
### nt/
- holds various command files and documentation files to building and running Emacs on Windows 9X/ME/NT/2000/XP.
### test/
- holds tests for various aspects of Emacs's functionality.
### autogen.sh
- it generates 'configure' and other files by runnnig the GNU build tools autoconf and automake, which in turn use GNU m4 and Perl.
  This should be needed only if you edit files liske 'configure.ac' that specify Emacs's autobuild procedure.
### configure
- a shell script to acclimate Emacs to the oddities of your processor and operating system.
### configure.ac
- input used by the autoconf program to construct the 'configure' script.
### config.bat
### CONTRIBUTE
- information on contributing to Emacs as a developer
### make-dist
- 
### Makefile.in
- a template used by 'configure' to create 'Makefile'
### INSTALL
- describing how to build and install GNU Emacs on various system.
### README
- sending bug-report:
  bug-gnu-emacs@gnu.org
