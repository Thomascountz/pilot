# Git Autocorrect

If you incorrectly type a Git command, you get something like this:

```text
$ git checkou master
git: 'checkou' is not a git command. See 'git --help'.

The most similar command is
        checkout
```

Git helps you be telling you the command that you might have meant. If you sent `help.autocorrect`, Git will not only tell you, it will execute it for you as well!

```text
$ git checkou master
WARNING: You called a Git command named 'checkou', which does not exist.
Continuing in 0.2 seconds, assuming that you meant 'checkout'.
Already on 'master'
Your branch is up to date with 'origin/master'.
```

To set the config globally, use the following command:

```text
git config --global help.autocorrect 2
```

The `2` in this command represents the how many tenths of a second you'd like Git to wait until it executes the command. For example, setting it to `50`, will tell Git to wait 5 seconds and give you a chance to cancel the execution.

