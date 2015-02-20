<<<<<<< HEAD
#Bash Completion for OS X
=======
DESCRIPTION
===========

This project is for bash-completion for osx

INSTALLATION
============

	./configure
	make
	make check # optional, requires dejagnu and tcllib
	make install # as root

You may still need to source it from either /etc/bashrc or ~/.bash_profile
(or any other file sourcing those). You can do this by simply add the
following code to ~/.bash_profile:

	if [ -f /etc/bash_completion ]; then
  		. /etc/bash_completion
	fi

CHANGELOG
=========

Version 1.3
-----------

clone from http://bash-completion.alioth.debian.org/files/bash-completion-1.3.tar.bz2

Version 1.4
-----------

remove unused completion:
	apt apt-build aptitude
	dpkg rpm
	update-alternatives
	freerdp freeciv
	dvd+rw-tools
	_yum _yum-utils
	rpmcheck
	yum-arch
>>>>>>> origin/master
