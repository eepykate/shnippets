# *sh script collection

All credit for the repo name goes to [maxestorr](https://github.com/maxestorr)

### Upload file or string of text to 0x0.st

Credit: [viz](https://github.com/vizs)

    #!/bin/sh
    [ -f ${1} ] && op=cat
    ${op:-echo} "${1:-`cat -`}" | curl -F file='@-' 'http://0x0.st'
