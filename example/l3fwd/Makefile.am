include $(top_srcdir)/example/Makefile.inc

bin_PROGRAMS = odp_l3fwd

odp_l3fwd_SOURCES = \
		    odp_l3fwd.c \
		    odp_l3fwd_db.c \
		    odp_l3fwd_lpm.c \
		    odp_l3fwd_db.h \
		    odp_l3fwd_lpm.h

if test_example
if ODP_PKTIO_PCAP
TESTS = odp_l3fwd_run.sh
endif
endif
EXTRA_DIST = odp_l3fwd_run.sh udp64.pcap

# If building out-of-tree, make check will not copy the scripts and data to the
# $(builddir) assuming that all commands are run locally. However this prevents
# running tests on a remote target using LOG_COMPILER.
# So copy all script and data files explicitly here.
all-local:
	if [ "x$(srcdir)" != "x$(builddir)" ]; then \
		for f in $(EXTRA_DIST); do \
			if [ -e $(srcdir)/$$f ]; then \
				mkdir -p $(builddir)/$$(dirname $$f); \
				cp $(srcdir)/$$f $(builddir)/$$f; \
			fi \
		done \
	fi
clean-local:
	if [ "x$(srcdir)" != "x$(builddir)" ]; then \
		for f in $(EXTRA_DIST); do \
			rm -f $(builddir)/$$f; \
		done \
	fi
