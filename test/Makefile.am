DEJATOOL = completion install unit
AM_RUNTESTFLAGS = --outdir log --ignore $(PACKAGE).log

EXTRA_DIST = completion \
	     config \
	     fixtures \
	     lib \
	     unit

all:
	$(mkdir_p) log tmp

distclean-local:
	rm -rf log tmp

AUTOMAKE_OPTIONS = dejagnu
