---
description: Make the current window part of the diff windows.
---

# Use 'diffthis' to Compare Vim Buffers

The [`:diffthis`](http://vimdoc.sourceforge.net/htmldoc/diff.html#:diffthis) command allows us to compare two \(or more\) buffers that are open in an existing Vim session. If we have two split windows containing buffers that we want to compare, then we can diff them by running:

```text
:windo diffthis
```

We can turn diff mode off just as easily, by running:

```text
:windo diffoff
```

The nice thing about this technique is that we can use an unnamed buffer. There’s no need to write the text to a temporary file. This technique would work just as well if neither buffer had been saved to disk, which makes it pretty flexible.

Source: [http://vimcasts.org/episodes/comparing-buffers-with-vimdiff/](http://vimcasts.org/episodes/comparing-buffers-with-vimdiff/)

