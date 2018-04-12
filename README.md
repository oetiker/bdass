Big Data Archive System Service
===============================
Version: #VERSION#
Date: #DATE#

Handle Migration of Big Data Archives from one system to another

You are looking at a sample CallBackery application. It comes complete
with a classic "configure - make - install" setup.

Prerequisite
------------

Get a copy of the Qooxdoo SDK from www.qooxdoo.org.

 mkdir ~/src
 cd ~/src
 wget https://github.com/qooxdoo/qooxdoo/archive/master.zip
 unzip master.zip

Setup
-----
Now get back to your app source directory and start building.
If you come from installing callbackery make sure to do the following
in a new terminal or unset $PERL5LIB

 ./configure --prefix=$HOME/opt/bdass --with-qooxdoo-sdk-dir=$HOME/src/qooxdoo-master
 make

Configure will check if all requirements are met and give
hints on how to fix the situation if something is missing.

Any mising perl modules will be downloaded and built.

Development
-----------

While developing the application it is convenient to NOT have to install it
before runnning. You can actually serve the Qooxdoo source directly
using the built-in Mojo webserver.

  cd frontend
  make source
  cd ../bin
  ./bdass-source-mode.sh

You can now connect to the CallBackery app with your web browser.

If you need any additional perl modules, write their names into the PERL_MODULES
file and run ./bootstrap.

Installation
------------

To install the application, just run

   make install

You can now run bdass.pl in reverse proxy mode.

   cd $HOME/opt/bdass/bin
   ./bdass.pl prefork

Packaging
---------

Before releasing, make sure to update CHANGES, VERSION and run ./bootstrap

You can also package the application as a nice tar.gz file, it will contain
a mini copy of cpan, so that all perl modules can be rebuilt at the
destination.  If you want to make sure that your project builds with perl
5.10.1, make sure to set the PERL environment variable to a perl 5.10.1 interpreter,
make sure to delete any PERL5LIB environment variable, remove the thirdparty
directory from your source tree and configure again.  Now all modules to build your
project with any perl from 5.10.1 on upward will be included in the distribution.

   make dist

Enjoy!

Tobias Oetiker <tobi@oetiker.ch>
