# *sh script collection

All credit for the repo name goes to [maxestorr](https://github.com/maxestorr)

### Upload file or string of text to 0x0.st

Credit: [viz](https://github.com/vizs)

```sh
#!/bin/sh
[ -f "${1}" ] && op=cat
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

Instead of typing `cd dir` you can just type `dir`.
If a command exists with the name `dir` it will run that instead of cd.
You can force it to go into the dir by typing `dir/`.

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

### Select a pixel & get its hex

Select a pixel, display a notification of the hex with a preview, and copy
it to clipboard

Credit: Me

[colorpicker is from here](https://github.com/ym1234/colorpicker)

```sh
#!/bin/sh

h="$(colorpicker -doq | tr -d '#\n')"; \
echo -n "$h" | xclip -sel clip;        \
notify-send "$h" "<span background=\"#$h\">      </span>"
```

Select a pixel and output the hex with a preview to the term

Credit: [turquoise-hexagon](https://github.com/turquoise-hexagon)

```sh
#!/usr/bin/env bash

while read -r line; do
    IFS=', ' read -r r g b hex <<< $line

    printf '%s\n\e[48;2;%s;%s;%sm       \e[m\n' \
        "$hex" "$r" "$g" "$b"
done < <(stdbuf -oL colorpicker -oq)
```

### Take screenshot and extract text

Credit: [MCotocel](https://www.github.com/Mcotocel)

```
#!/bin/bash
 
res=$(echo "Screen|Selection" | rofi -sep "|" -dmenu -i -p 'Image to text')
 
if [ $res = "Screen" ]; then
    maim ~/Pictures/Screenshots/imgtext.png; tesseract ~/Pictures/Screenshots/imgtext.png ~/imgtext; xclip -sel c < ~/imgtext.txt; rm ~/imgtext.txt ~/Pictures/Screenshots/imgtext/png
fi
if [ $res = "Selection" ]; then
    maim -s ~/Pictures/Screenshots/imgtext.png; tesseract ~/Pictures/Screenshots/imgtext.png ~/imgtext; xclip -sel c < ~/imgtext.txt; rm ~/imgtext.txt ~/Pictures/Screenshots/imgtext/png
fi
exit 0
```

### Fuzzy search through zsh history

Credit: [MCotocel](https://www.github.com/Mcotocel)

```
fzf-history () {
    $(cat ~/.zsh_history | fzf --height=20% --prompt="❯ " --pointer=❯ --color=fg:4,bg:-1,bg+:-1,info:7,prompt:10,pointer:10 --preview="echo {}")
}

zle -N fzf-history
bindkey '^R' fzf-history
```
