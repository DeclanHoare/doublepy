doublepy is a Python module designed to get two instances of Python
communicating. It currently features two methods of use:

* Subscripts: Pass a string containing a Python script to runSubscript()
and the script will be run in a separate process, with anything on
stdout returned. dblEscape() will insert escape characters into a string
literal so that it can be inserted into a subscript correctly.
* RPyC: Doublepy features a simple wrapper for RPyC to run multiple
different Python interpreters on the same machine. RPyC is designed for
communication between Python on different machines and allows flexible
interaction with objects across environments. This is more powerful, but
has a larger overhead, is possibly buggier, and doesn't allow
communication between different major versions of Python.

This repository is also the home of a few modules built around doublepy:

* pygimp uses doublepy's RPyC wrapper to connect GIMP's Python
interpreter with a regular one. On import, it will launch GIMP and copy
the gimp module's namespace into its own. (It will fail horribly on
Python 3, because GIMP uses Python 2.)
* wkinter is an extended version of David Baird's WebKit GUI tutorial,
using doublepy subscripts to allow for regular GTK dialog boxes (which
would freeze the main application). This is also only compatible with
Python 2.

Everything in this repo is licensed under GPLv2+. (I usually use GPLv3+
but in this case I wanted to be able to use RSPiX, which uses GPLv2, in
the same program.)

## TODO
* Find a way to get RPyC to pick an open socket itself and then pass it
back to the client rather than having to use getOpenPort(). The current
way has a race condition and just sucks in general.
* Fix pygimp and wkinter on Python 3?
* Add setup.py
