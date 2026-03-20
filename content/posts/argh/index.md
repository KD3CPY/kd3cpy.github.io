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