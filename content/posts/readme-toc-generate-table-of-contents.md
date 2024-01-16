+++
title = "readme-toc - generate a table of contents in markdown documents"
author = ["Dmitry Markushevich"]
date = 2024-01-16T00:00:00-08:00
lastmod = 2024-01-16T09:22:31-08:00
tags = ["seedling", "github", "documentation"]
draft = false
+++

[readme-toc](https://www.npmjs.com/package/readme-toc) is a utility that creates a table of contents in markdown documents.

You create a placeholder for where you want the TOC to go and the utility creates the rest:

Starting with this `README.md`:

````md
# README.md

  <!-- toc -->
  <!-- toc stop -->

# Installation instructions

```shell
npx readme-toc
```

# Another Heading

# Final heading
````

then running:

````shell
npx readme-toc
````

results in the following new \`README.md\`. This makes reading github docs so much easier.

````md
# README.md

  <!-- toc -->
  * [Installation instructions](#installation-instructions)
  * [Another Heading](#another-heading)
  * [Final heading](#final-heading)

  <!-- toc stop -->

  # Installation instructions

  ```shell
  npx readme-toc
  ```

  # Another Heading

  # Final heading
````
