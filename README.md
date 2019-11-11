# *sh script collection

All credit for the repo name goes to [maxestorr](https://github.com/maxestorr)

### Upload file or string of text to 0x0.st

Credit: [viz](https://github.com/vizs)

    #!/bin/sh
    [ -f ${1} ] && op=cat
    ${op:-echo} "${1:-`cat -`}" | curl -F file='@-' 'http://0x0.st'

### Generate a tileable wallpaper with static using imagemagick

Credit: Me

($1 = base hex value)

    #!/bin/sh
    convert -size 128x128 canvas:"$1" -separate -attenuate 0.13 \
      +noise gaussian -combine -colorspace sRGB static.png
