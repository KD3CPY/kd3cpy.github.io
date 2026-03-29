+++
date = '2026-03-20'
draft = false
title = 'Argh'
tags = ['github','neocities','CLI','hugo','submodules']
author = 'KD3CPY'
+++
When [last I posted](/posts/hugo/), I was discussing the upcoming---and doubtless straightforward---process of getting this site actually online. The local copy worked, everything looked good, there existed documentation to move things from point A to point B, where point B is GitHub.

Suffice to say that this has been more of a learning experience than I hoped. I established that the Neocities [CLI push option](https://neocities.org/cli) was good for nothing but generating errors and having issues with Ruby (and `ruby -v` and Homebrew have different ideas of which version is installed...) Third party Neocities options also weren't working, and I'm not in a position to tell if it's user error or something actually broken. So I went back to my maybe-just-do-GitHub-Pages plan.

I got repositories created and struggled with passwords and tokens, and adding workflow to tokens. And mistyping tokens because my default font is sans serif and I, l, and 1 look *much* different if you switch to Times New Roman. And updating repository URLs to one that could be used for Pages. I did a lot of flipping from one documentation window to another (there is a strong argument to be made that I should, perhaps, have RTFM *before* starting this process) and googling error messages and doing things to address those error messages.

(Somewhere during this process, I began to feel great nostalgia for FTP. There is something beautiful about dragging-and-dropping in an FTP client.)

Now I seem to be able to `commit` and `push`. (I'm okay forcing it, because this isn't actually a proper repository for version control; it's a one-way process to update a website.) I am happy with how the site looks...*except* for the bouncing image. That introduced me to the implications of submodules (should've RTFM). My local changes to `hero.css` are being ignored; it looks like the `assets/css` are being pulled from the [theme-maker's repository](https://github.com/Livour). I...think I'm just going to let the image bounce for now.

Anyway: learning experience. New skills acquired. Happy to be done with this for the time being.