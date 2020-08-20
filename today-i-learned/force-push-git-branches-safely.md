---
description: >-
  git push --force-with-lease will prevent you from overriding any work on the
  remote branch that you might not know about.
---

# Force Push Git Branches Safely

Usually `git push` will fail if your git history is different than the remote you're pushing to. This can happen when you amend a commit or rebase.

To circumvent this, you can specify that you want your version of history to _override_ the remote's history. You can do this by passing the `--force` flag.

However, if someone else has pushed up changes to the branch you're trying to override, you'll lose their changes. This can happen inadvertently. For example, you and Peggy are both working on the same branch. She pushes up a commit that adds to the existing history and then you rebase then then `--force` push your changes. We've now lost Peggy's contribution on remote!

If, however, you attempted to push with `--force-with-lease` git will prevent your changes from overriding Peggy's. You'll have to talk to Peggy about how to reconcile this.

[Git - git-push Documentation](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease)

