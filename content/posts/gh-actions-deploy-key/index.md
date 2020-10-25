---
title: "Github Actions Deploy Key"
date: 2020-10-23T09:47:04-06:00
---

### ... and how to use it to deploy a static website.

Well, I ran out of patience with my own static website generator. While I _do_
plan to finish it, in the meantime I won't be using it to generate this
website. So, for now it's [hugo][1]. Nowthen, how to get it deployed? I've been
wanting to try it with Github Actions for a while and this seemed like a
nice fit.

#### Mental outline

There are two primary repositories I'm using to make this website. First is
the [project source repository][5] containing markdown files, static assets,
submodule refs to [my fork][3] of the [hugo-xmin][2] theme, and so on. Second is
the main [Github Pages repository](https://github.com/kmaris/kmaris.github.io)
that is used as the root resource for [https://kmaris.net](https://kmaris.net).

So, what do we need to do? The goal is to get the content from the
main project source repository, render it through hugo, and published into the
github pages repository. In pseudo-workflow the steps, at first glance, are
essentially:

  - Clone the main project source
  - Render the source to the github pages repository
  - Commit and publish to the pages repository

Generally speaking that's the idea, but some tricks come up during
implementation that the steps above don't cover. For instance, rendering the
project source _to_ the pages repository usually implies the destination
repository is already checked out. So in the workflow it will be cloned before
the build step happens.

###### ... with a pinch of implementation details

Knowing that we're going to be deploying content into a repository, a deploy
key is what we'll need. A deploy key is an ssh key with the private key
stored in the source repository as a secret (alongside the code) and the public
part is in the destination repository. This is better than using a personal
access token because you're keeping permissions to your repository very low;
namely just to deploying.

#### So lets do it

Generate your new deploy key:

```bash
ssh-keygen -C pagesdeploy@github -f ./pages_key -N ""
```

You'll have two files now, a private key named `pages_key` and the public part
`pages_key.pub`.

Then create a Deploy key in your pages repo from the public key:

![Deploy key](<deploykey.png>)

and a Secret in the source repo from the private key:

![Secret](<secrets.png>)

By using the deploy key to do the checkout, the action runner will have the
permissions to do the push and we don't have to tinker with tokens. In your
source repo make a workflow (I call mine gh-pages.yml) at
`.github/webhooks/gh-pages.yml` and in it you'll have the following:

{{< readfile file="/content/posts/gh-actions-deploy-key/gh-pages.yml" highlight="yaml" >}}

By doing a `git add -N .` before `git diff` we can have diff pay attention to
any new, untracked files. And if there are diffs, commit and push the new
content!

[1]: https://gohugo.io
[2]: https://github.com/yihui/hugo-xmin
[3]: https://github.com/kmaris/hugo-xmin
[4]: https://watercss.netlify.app/
[5]: https://github.com/kmaris/kmaris.net
[6]: https://github.com/kmaris/kmaris.github.io
