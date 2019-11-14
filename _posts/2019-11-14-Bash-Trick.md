---
layout: post
title: Make bash and markdown play nice
---

Bash and github README.md files don't always play nice.  

In theory, you can cut-and-paste bash commands right
into your command prompt. But if you double-click the
README.md line, you select not only the command, but
also that `$` too.

So the following incredibly helpful README.md line

    $ yarn add count-interval

becomes this

    > $ yarn add count-interval
    bash: $: command not found

Who needs this hassle? Just put an executable file named `$` somewhere in your path, with the contents `$@`.  On a mac you can try this in `/usr/local/bin/` like this:

    echo '$@' > /usr/local/bin/$; chmod a+x /usr/local/bin/$

(To make it easier, I left off the obligatory `$` this time.)

Now you can leave that annoying `$` in!

    > $ yarn add first-interval
    yarn add ...

Why a file? Why not just an alias? Because bash says you can't.

    > alias '$=$@'
    bash: alias: `$': invalid alias name
