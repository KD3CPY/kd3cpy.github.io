+++
date = '2026-03-20'
draft = true
title = 'Argh'
tags = ['neocities','github']
+++
When [last I posted](/posts/hugo/), I was discussing the upcoming---and doubtless straightforward---process of getting this site actually online. The local copy works, everything looks good, there exists documentation to move things from point A to point B, where point B is GitHub.

Yet...argh, I am having difficulty proving that I have permission to do anything with my Git project. Password, key, token...argh.

I noticed Neocities does indeed have a [CLI push option](https://neocities.org/cli). Awesome! (How did I miss noticing that before?) Problem solved! Except...I'm getting errors installing `neocities`. Issues with needing older gems and newer Ruby. `ruby -v` reports a 2.6 version (which would've come pre-installed on the Mac), despite Homebrew claiming that 4.2 is installed...

What about [async-neocities](https://github.com/bcomnes/async-neocities/tree/master)? That looks promising. It installs. Except...I can't run any commands, not even see the version. What about [Neocities Node](https://github.com/neocities/neocities-node)? I'm not able to initialize.

(At this point, I began to feel great nostalgia for FTP. There is something beautiful about dragging-and-dropping in an FTP client.)

I went back to GitHub [documentation](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository) and successfully added this site's files to my repository. GitHub Pages really seems to want to use Jekyll and does not recognize my `public` directory. (Rather than making me wish I had opted for Jekyll, this makes me feel defensive on Hugo's behalf.) So now it looks like I'm creating an [Actions workflow](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site). 

I basically followed the [Hugo documentation](https://gohugo.io/host-and-deploy/host-on-github-pages/) for GitHub Pages. And...it's not taking my token. TSOR indicates I need a token with workflow enabled. Back to Developer settings in GitHub. And...I'm not seeing the promised ticky box for workflow for a new token... Ah! But I can *edit* my existing token and click the ticky box.

It looks like the site has successfully been pushed to GitHub Pages and the workflows all show as green. But then when I try re-pushing from the command line, it asks for my GitHub password but says, again, that it's invalid.

Still, the site looks fine. Oh, wait, the hero logo is moving. So the `hero.css` is okay locally but not in the repository...even though I didn't push until after I'd made changes...? And an image is broken on the previous post. Okay, this means more rounds of troubleshooting. (Why can't it just let me push the `public` directory!) 

Trying `git config` to set username and password. What about setting the token? Setting `token` didn't work, but `user.token` did (or at least it let me set it). I also set `user.password` and when I try a `git push` it...asks for username and password, then throws the password-authentication-is-not-supported error.

Hm, doing `git config list` shows a reference to the Mana theme on the GitHub. But I don't know why the `hero.css` would be coming from there but not `layouts\partials\footer.html` (the file I edited to fix the copyright display, which is displaying correctly on GitHub Pages). 

Do I need to reset the repository URL? Nope, that's correct. Trying `brew install --cask git-credential-manager`. No, it's not taking the password there. Trying to do a `sudo git push`. Nope: another "sorry, try again" message. Didn't take the token, either. Oh, wait, is this a *font issue*? Resetting to TNR, it looks like I misread a couple upper-case *I*s as lower-case *l*s. But...nope, even entering modified password and token, it doesn't work from the command line.

Oh, no, *wait*, it is repository address. Now I've reset it for `https://github.com/KD3CPY/kd3cpy.github.io` (instead of `kd3cpy.git`, because it's set for use on Pages). 

Tried:
```
git add .
git commit -m "Comment"
git push -f -u origin main
```

This time, it accepted the token (have I just been *mistyping* it every. Single. Time?) and began enumerating, counting, compressing, and writing objects. But the remote was rejected because the token can't update the workflow `.yaml` without "workflow" scope (which I could've sworn I did when I ticked the workflow ticky box and generated a new token.) When I just try `git push origin main`, it tells me I have to fetch first. (No! No, I don't! This is strictly a one-way operation!)

Okay, I went in *again* to tick the workflow ticky box, and this time it appears to've worked. So I am able to do a `git commit` and then `git push --force` (forced because I don't want to fetch anything from the repository to reconcile with what I have locally: this is strictly a one-woman, one-way operation).

I cheated and made some manual changes to deal with the broken image (I don't know why making the image name lower case worked, but it did, so huzzah!) Now, the only issue is the bouncing logo. Why are submodules a thing? Why is it not just taking *my* modified `.css` from local?

This is driving me completely batty. I'm using a static site generator so I can *generate a static site*. I just want whatever is in *my* public directory to show up on the interwebs.

This is all clearly a learning experience for me.