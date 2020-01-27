# *sh script collection

All credit for the repo name goes to [maxestorr](https://github.com/maxestorr)

### Upload file or string of text to 0x0.st

Credit: [viz](https://github.com/vizs)

```sh
#!/bin/sh
[ -f ${1} ] && op=cat
${op:-echo} "${1:-`cat -`}" | curl -F file='@-' 'http://0x0.st'
```

### Generate a tileable wallpaper with static using imagemagick

Credit: Me

($1 = base hex value)

```sh
#!/bin/sh
convert -size 128x128 canvas:"$1" -separate -attenuate 0.13 \
  +noise gaussian -combine -colorspace sRGB static.png
```

### Record the screen with ffmpeg

**Option 1:**

Credit: [MitchWeaver](https://github.com/MitchWeaver)

Note: Remeber to add `-pix_fmt yuv420p` after `-i ${DISPLAY:=:0.0}+${1},${2}` to have videos work on all platforms correctly.

https://github.com/MitchWeaver/bin/blob/master/util/record

**Option 2:**

Credit: Me

https://github.com/GaugeK/blaze

### Cd without typing cd

Instead of typing `cd dir` you can just type `dir`. If a command exists with the name `dir` it will run that instead of cd. You can force it to go into the dir by typing `dir/`.

bash:

    shopt -s autocd

zsh:

    setopt auto_cd

### Surround text with string

Credit: [BanchouBoo](https://github.com/BanchouBoo)

[surround](surround)

```
>> surround test \"
"test"
>> surround test "(([<{"
(([<{test}>]))
>> surround test "<a href=\"https://github.com\">"
<a href="https://github.com">test</a>
```
