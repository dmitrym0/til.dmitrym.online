+++
title = "Managing Bibliography with Emacs, Citar and Zotero"
author = ["Dmitry Markushevich"]
date = 2024-08-08
lastmod = 2024-08-09T09:09:01+07:00
tags = ["learning", "reading"]
draft = false
+++

## Introduction {#introduction}

When doing any sort of research, it becomes a real chore managing sources. Sources are web sites, books, articles or anything else that you need to reference in your research. It answers the question of "where did I read this?".


## Setup {#setup}

[Zotero](https://www.zotero.org) is a document and bibliography manager. It's able to extract and snapshot webpages and generate bibliography like so:

```shell
@inreference{BigDig2024,
    title = {Big {{Dig}}},
    booktitle = {Wikipedia},
    date = {2024-07-28T04:33:34Z},
    url = {https://en.wikipedia.org/w/index.php?title=Big_Dig&oldid=1237102624},
    urldate = {2024-08-02},
    abstract = {The Big Dig was a megaproject in Boston that rerouted the then elevated Central Artery of Interstate 93 that cut across Boston into the O'Neill Tunnel and built the Ted Williams Tunnel to e>
    langid = {english},
    keywords = {estimation construction},
    annotation = {Page Version ID: 1237102624},
    file = {/Users/dmitry/Zotero/storage/5A8ADMJ7/2024 - Big Dig.pdf;/Users/dmitry/Zotero/storage/K4CTZQTC/Big_Dig.html}
}
```

[citar](https://github.com/emacs-citar/citar) is the emacs package that referenses the bibliography data produced by Zotero to make citations simpler.


## Workflow for reading long articles {#workflow-for-reading-long-articles}

1.  Find a long read article.
2.  Use a [zotero extension](https://www.zotero.org/download/connectors) to take a snapshot of it.
3.  Generate a "reader view" PDF of the page and import it into zotero.
4.  Use `M-x citar-open` to open the document in [org-noter](https://github.com/org-noter/org-noter) and start incrementally reading it.
5.  While summarizing notes (see [how to process reading notes](https://notes.andymatuschak.org/About_these_notes?stackedNotes=zEr7kCcH6zUUroDJBwDj2n5)) use `M-x citar-insert-citation` to reference the source material.


## References {#references}

Really good introduction here: [Citations in org-mode: Org-cite and Citar](https://kristofferbalintona.me/posts/202206141852/).
