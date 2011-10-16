Pony Mode - a Django mode for emacs
===================================

New Django mode for emacs. This project is a fork of David Miller's pony mode.
For further details on David's project refer to this page on github.

https://github.com/davidmiller/pony-mode

Motivation
----------

For my current job as a Django Web Developer, I need to be able to switch among a 
whole set of different configuration/environment variables settings. Moreover, working on the Mac,
I find it not very comfortable to launch long management commands from the command line, 
often with a lot of different settings involved, this requires *lots* of typing. 
So I thought that could be the perfect occasion to learn Elisp and build something 
that could prove useful as a result :)

Features (mostly derived from David Miller's pony mode)
-------------------------------------------------------

Multiple configuration
======================

* Configureable multiple environment for running, testing, shell
  (probably more to come)

Running
=======
* Run dev server in an emacs buffer [C-c C-p r]
* Checks to see if runserver_plus is available
* If not uses in-built runserver
* If server is already running switch to buffer

* Jump to current project in browser (start server if required) [C-c C-p b]

Shell
=====
* Run django shell in buffer [C-c C-p s]
* Checks for shell_plus
* If not defaults to shell
* If shell process already available switch to buffer

Testing
=======
* Run test case at point in buffer [C-c C-p t]
* Run tests for current app in buffer [C-c C-p t]


Deployment
==========
* Fabric integration [C-c C-p f]


* Run Syncdb on current project
* Management commands for current project in interactive buffer
* South integration - run south convert, schemamigration, migrate
* Startapp and dumpdata on current project within emacs
* Database integration with Emacs sql-mode interactive buffer [C-c C-c d
* Django Template minor mode with syntax highlighting for django template tags
* Snippet collection for django
* generate tags table for project
* run manage commands in interactive buffer
* Buildout integration
* Generate TAGS table for project to enable quick navigation
* Jump to template at point or from editing view [C-c C-p g t]
* Virtualenv integration

Fabric Integration
------------------

Pony mode will interact with fabric for your current project, building a list of functions to auto-complete, and running commands within a \*fabric\* buffer.

Tags
----

Generate a TAGS table for your project with M-x django-tags
The exact command used is customisable through django-etags-command in
M-x customize-group RET django

Tests
-----

Run tests in in an interactive buffer, allowing you to drop out into ipdb/pdb
as required.

Tests will default to --failfast, but you can turn that off with the variable django-test-failfast or set it in
M-x customize-group django

in a test run buffer, C-c C-g will jump to the last file and line indicated by the traceback.

Virtualenv
----------

The file should look something like this:

::

  ;; This file contains configuration parameters for a Django project.
  ;; ================================================================
  (make-pony-project

  ;; Project name (mandatory)
  :project "my-project"

  ;; Main interpreter (mandatory)
  :python "/Users/markus/Documents/work/my-project/bin/python"

  ;; Default environment (optional)
  :default-env "DJANGO_CONF=default"

  ;; Shell environment and options (optional)
  :shell-env "DJANGO_CONF=default"
  ;; :shell-opts ""

  ;; Run environment and options (optional)
  :run-env "DJANGO_CONF=dev"
  ;; :run-opts ""

  ;; Test environment and options (optional)
  :test-env "DJANGO_CONF=test"
  ;; :test-opts ""

  ;; Server host (optional)
  :host "localhost"

  ;; Server port (optional)
  :port "8000"
  )


Installation
------------

1. clone this repo somewhere 

::

  $ git clone http://github.com/mwolf76/pony-mode

2. Byte-compile the file (recommended, optional)

::

  M-x byte-compile-file

3. Add the path to your load-path::

::

  (add-to-list 'load-path "path/to/pony-mode")

4. Add to your .emacs

::

  (require 'pony-mode)

5. Enjoy

Bugs
----

Pony-mode is under active development, so please report any bugs on the github issue tracker

Licence
-------

Totally GPL
