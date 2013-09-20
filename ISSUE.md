TROUBLESHOOTING
---------------

If you find that a given function is producing errors under certain
circumstances when you attempt completion, try running 'set -v' or
'set -x' prior to attempting the completion again. This will produce
useful debugging output that will aid us in fixing the problem if you
are unable to do so yourself. Turn off the trace output by running
either 'set +v' or 'set +x'.


KNOWN PROBLEMS
--------------

I.

There seems to be some issue with using the bash built-in cd within
Makefiles. When invoked as /bin/sh within Makefiles, bash seems to
have a problem changing directory via the cd command. A work-around
for this is to define SHELL=/bin/bash within your Makefile. This is
believed to be a bug in bash.

II.

The have() function is used to conserve memory by only installing
completion functions for those programs that are actually present on
your system. The current method of determining whether or not a given
binary is present is whether or not it can be found along a certain
path of directories. The path that is currently searched is:

	$PATH:/sbin:/usr/sbin:/usr/local/sbin

where $PATH is your user path at the time the bash completion file is
sourced.

III.

Many of the completion functions assume GNU versions of the various
text utilities that they call (e.g. grep, sed and awk). Your mileage
may vary.

IV.

If you are seeing 'unbound variable' warnings from bash when hitting
<Tab>, this is because you have either 'set -u' or 'set -o nounset'
somewhere in your start-up files. This causes bash to flag the use of
any uninitialised shell variables as an error.

Whilst we try to avoid references to uninitialised variables in the
code, there seem to be at least some cases where bash issues this
warning even though the variable in question has been initialised.

One place this appears to occur is within the _muttconffiles() helper
function used by mutt completion, where the function calls itself
recursively. This seems to confuse bash and it issues spurious
warnings if 'nounset' is set.
