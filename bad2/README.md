## Bad linkage

**Requires**:
- Files `[A-Z].txt` in dir `attachments/`

**Steps**:
- Open Compose
- `:source bad2.rc`

Before the last call to `<group-alternatives>` the linkage looks OK.

![before](https://raw.githubusercontent.com/neomutt/test-compose/main/bad2/18%3A03%3A07-email.svg)

Afterwards, there's `Body` that's mislinked.  
Second row, fourth `Body` is linked from the left and above.

![after](https://raw.githubusercontent.com/neomutt/test-compose/main/bad2/18%3A03%3A13-email.svg)

