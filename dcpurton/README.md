# Automated tests for composing multipart emails in Neomutt

## Set up

- Configure *Neomutt* with `--asan --debug-graphviz --debug-window`.
- set the `NEOMUTT` environment variable to the `neomutt` executable.

## Usage

- `make` in the top level directory runs the tests.
- `make clean` cleans the test output files.

## Adding tests

Add files to the `rc.d` directory. They should all source `rc.d/setup.rc` and
then include the keystrokes to set up the email as well as the keystrokes to
source `rc.d/run-test.rc`, e.g., `tests/001-single-group.rc` is:

```
source "../rc.d/setup.rc"
push "<enter-command>source rc.d/start-compose.rc<enter><enter-command>source rc.d/attach-one.rc<enter><enter-command>source rc.d/run-test.rc<enter>"

# vim: syn=neomuttrc
```

