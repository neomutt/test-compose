# needs:
#   export NEOMUTT=/path/to/neomutt
ifeq ($(NEOMUTT),)
  $(error NEOMUTT environment variable not set)
endif


NEOMUTT_ARGS=-n

TESTDIR=tests
TESTS  := $(wildcard $(TESTDIR)/*.rc)
BODIES := $(patsubst $(TESTDIR)/%.rc,$(TESTDIR)/%.body,$(TESTS))

PASS='\e[1;32m[PASS]\e[0m'
FAIL='\e[1;31m[FAIL]\e[0m'

test: $(BODIES) $(NEOMUTT)

$(TESTDIR)/%.body: $(TESTDIR)/%.rc
	@$(NEOMUTT) $(NEOMUTT_ARGS) -l $@ -F $<
	@grep "Body.layout" $@0 | sed 's/^.*layout:.//' > $@
	@rm $@0
	@echo -n "Test "
	@basename $< .rc | tr -d '\n'
	@echo -n " "
	@cmp -s $@ $@.ref; \
	RETVAL=$$?; \
	if [ $$RETVAL -eq 0 ]; then \
          echo $(PASS); \
        else \
          echo $(FAIL); \
        fi

save: test
	@echo Saving reference files
	@for i in $(TESTDIR)/*.body; do \
	  cp $$i $$i.ref; \
	done

clean:
	@echo Cleaning up.
	@rm -f $(TESTDIR)/*.body
