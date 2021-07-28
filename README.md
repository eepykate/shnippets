# collection of small snippets

previously this was just shell (hence the name), didn't want another repo for snippets

All credit for the repo name goes to [maxestorr](https://github.com/maxestorr)

# css

### [[discord] code blocks](css/discord-code-blocks.css)
Displays language if declared (& gives them a cleaner look)  
Credit: [gk](https://github.com/6gk)


### [[discord] role backgrounds](css/discord-roles.css)
Replaces the role outlines with a background  
Credit: [gk](https://github.com/6gk)


### [[discord] fix copying messages in firefox](css/discord-fix-copying.css)
Credit: [gk](https://github.com/6gk)


--------------------------------

# shell


### [Upload file or string of text to 0x0.st](sh/0x0)
Credit: [viz](https://github.com/vizs)


### [Generate a tileable wallpaper with static using imagemagick](sh/genwp)
Credit: [gk](https://github.com/6gk)


### [Surround text with string](sh/surround)
Credit: [BanchouBoo](https://github.com/BanchouBoo)


### [Select a pixel & copy its hex with a notification preview](sh/col-notify)
[requires colorpicker](https://github.com/ym1234/colorpicker) & for your notification daemon to support pango markup  
Credit: [gk](https://github.com/6gk)


### [Select a pixel and output the hex with a preview to the term](sh/col-term)
Credit: [turquoise-hexagon](https://github.com/turquoise-hexagon)


### [Take screenshot and extract text](sh/ocr)
Credit: [MCotocel](https://www.github.com/Mcotocel)


### [Fuzzy search through zsh history](sh/zsh-fuzzy-history)
Credit: [MCotocel](https://www.github.com/Mcotocel)


### Open random manpage
Credit: [Mcotocel](https://www.github.com/Mcotocel)

    man -k . | awk '{print $1}' | shuf -n 1 | xargs man


### Grab a random image from Unsplash
Credit: [paradox](https://www.github.com/safinsingh)

    curl -Ls https://source.unsplash.com/random/3840x2160 -o image.jpg


### cd without typing cd
Instead of typing `cd dir` you can just type `dir`.
If a command exists with the name `dir` it will run that instead of cd.
You can force it to go into the dir by typing `dir/`.

bash:

    shopt -s autocd

zsh:

    setopt auto_cd


### Record the screen with ffmpeg
**[Option 1](https://github.com/MitchWeaver/bin/blob/master/util/record)**
Credit: [MitchWeaver](https://github.com/MitchWeaver)

**Note:** Remeber to add `-pix_fmt yuv420p` after `-i ${DISPLAY:=:0.0}+${1},${2}` to have videos work on all platforms correctly.

**[Option 2](https://github.com/6gk/scr)**
Credit: [gk](https://github.com/6gk)
