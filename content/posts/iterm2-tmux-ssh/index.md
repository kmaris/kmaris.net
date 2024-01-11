---
title: "iTerm2, ssh, and remote tmux session integration for vim"
date: 2023-10-05T10:12:32-06:00
categories:
  - tech
  - macos
  - tmux
  - ssh
---

If you often use vim, especially while working on remote servers, you know how
annoying getting mouse integration to work is. Here is what I have found works
best for me. What I wanted was:

  - Functional ⌘-C and ⌘-V for copy/paste into and out of the terminal.
  - Copy/paste needs to work with tmux running on the remote host.
  - Mouse scrolling still works in some form.

Mouse scroll is the thing that suffers here, for me. If you do `set mouse=a`
you get the best vim scrolling behavior as in this video: As in this video:

[![asciicast](https://asciinema.org/a/KjgXrD7LdhwmDBpY4zPl5wtO7.svg)](https://asciinema.org/a/KjgXrD7LdhwmDBpY4zPl5wtO7)

But then to copy/paste you must hold Option(⌥) when selecting text with the
mouse. I always forget this, so I settle for worse scrolling by keeping the
mouse setting unset: `set mouse=` which is the vim default. You also lose the
ability to click a position to locate the cursor at the click. See the
difference:

<script async id="asciicast-vxl2uqpexwATnt13yUTEzYkqO" src="https://asciinema.org/a/vxl2uqpexwATnt13yUTEzYkqO.js"></script>

I also like to use iTerm2's native support for tmux because I can never
remember the default keys. One of the first things I did upon learning tmux was
to use personalized keys for actions like splitting windows. That might have
been a mistake. Now when I go to a remote server, my custom settings and theme
and vim integrations are all useless there.

Here's a nifty function I found [on stackoverflow][1]. I also *highly*
recommend that you enable completion for the function. My preferred completion
is to behave like ssh so I can tab-complete for hostnames. The `compdef`
command might be specific to `zsh` so it might take a little tweaking between
OS'es, distros, and shells.

You'll notice I use autossh, if you want to use plain ssh replace `autossh -M
8888` with `ssh` and you're good. You will also want to change the `kmaris`
session name to something else 🙂. Using `new -A -s` will ensure that tmux will
use an existing session with that name, _or_ create a new session with that
name.

```bash
# tmux+ssh helper function with iterm integration
function tmssh () {
  if [[ -z "$1" ]]; then
    me="${FUNCNAME[0]}${funcstack[1]}"
    echo "usage: $me [ssh-args] hostname"
    return 1
  fi

  autossh -M 8888 "$@" -t 'tmux -CC new -A -s kmaris'
}
compdef tmssh=ssh
```



[1]: https://superuser.com/questions/741769/remote-server-iterm2-and-tmux-integration
