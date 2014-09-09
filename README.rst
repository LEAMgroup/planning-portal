Plone 4.3 site buildout
=======================

**ALERT - this is currently non-functional for development mode.**

A basic Plone 4.3 buildout. I'll update this
when I can to keep up with the latest releases of 4.3.

All the standard Plone stuff applies. I/m building against Python 2.7.x.
Make sure you have all the system environment stuff you need,
and run this from a virtualenv.

System environment
===================
These are things I install on my Ubuntu development system::

  apt-get install build-essential libxslt1-dev wget \
  libxml2-dev libxml2-utils zlib1g-dev libjpeg-dev libfreetype6-dev \
  poppler-utils wv python2.7-dev python-distribute


Install the latest virtualenv::

  sudo pip install virtualenv


Setup your virtual environment and get the buildout
(substitute your project's name for *PROJECT*)::

  cd /install/dir/
  virtualenv venv-*PROJECT*
  source venv-*PROJECT*/bin/activate
  mkdir -p ../buildout-cache/{eggs,downloads}
  git clone https://github.com/LEAMgroup/planning-portal.git *PROJECT*


Change the name of the **site-id** assignment variable in buildout.cfg
(it is currently set to *leam*), then run the buildout::

  ./bin/buildout -c develop.cfg


What the heck? Running "./bin/buildout" doesn't work!
--------------------------------------------------------
I run my builds as either develop.cfg or production.cfg
so there's no guessing.

*Originally implemented by the original author but I like the idea!*

On my dev boxes, I do a::

  ./bin/buildout -c develop.cfg

On production, I do::

  ./bin/buildout -c production.cfg

If you have several development environments, just
cp the develop.cfg and edit away. One for Bob, one for Judy, etc.
Since these should be unobtrusive, you can even check them in.


Because I'm lazy, I have an alias on my devel boxes to do the build:
alias plb=./bin/buildout -c develop.cfg

There's also a bash shell script that does some checks.
You can ask me for it if you want.

**Change the *admin* password!**


Staging and user acceptance
------------------------------------
If you have, say, staging and user acceptance
environments, cp production.cfg and tweak to
your hearts content. Then, just

  ./bin/buildout -c yourthing.cfg

for whatever your thing happens to be.
