# Automated tests for composing multipart emails in Neomutt

## Set up

- Configure *Neomutt* with `--asan --debug-graphviz --debug-window`.
- set the `NEOMUTT` environment variable to the `neomutt` executable.

## Usage

- `make` in the top level directory runs the tests.
- `make clean` cleans the test output files.
- `make save` runs all the tests and updates all reference output files

## Adding tests

Add files to the `rc.d` directory. They should all source `rc.d/setup.rc` and
then include the keystrokes to set up the email (can use several `push`
commands in reverse order) as well as the keystrokes to source
`rc.d/run-test.rc`, e.g., `tests/02-single-group-01.rc` is:

```
source "../rc.d/setup.rc"

push "<enter-command>source rc.d/run-test.rc<enter>"
push "<tag-entry>1<enter><tag-entry><group-alternatives>"
push "<enter-command>source rc.d/attach-one.rc<enter>"
push "<enter-command>source rc.d/start-compose.rc<enter>"

# A group of two attachments as the fundamental part
#
#   I     1 <no description>
# - I     2 ├─>/tmp/neomutt-hostname-XXXX-XXXXXX-XXXXXXXXX
#   A     3 └─>attachments/A.txt

# vim: syn=neomuttrc
```

