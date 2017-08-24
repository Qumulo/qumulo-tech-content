# Qumulo Tech Content Repo

This repo contains article content that is automatically imported by the production site.

## Markdown with YAML frontmatter

All the markdown files contain a YAML front matter block that will be processed by our import as a special file. The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines. It's also a required feature in every markdown file. Here is an example of an article markdown file:

```
---
title: What We Believe
url: what-we-believe
---

# We have become a digital species

More and more of our lives are spent producing, consuming, and analyzing digital content. Ever more of our creations, discoveries, and experiences come from, and take the form of, data.

Through the very act of living, year by year, we are relentlessly creating exponentially more data objects. And we never, ever, throw anything away.

Today’s enterprise storage systems can’t keep up with storing all this data – let alone with managing it.

To support our digital existence, the future’s storage will be software that knits low-cost commodity hardware together to provide a scalable, fast and reliable data storage system.

That system will cease to be a passive, ever-growing dumpster for digital waste. Instead, it will become an intelligent collaborator in the storage, retrieval, management and curation of trillions of data objects.

That system is Qumulo Core.
```

Both the article pages and category pages are structured similarly but support different frontmatter tags.

The category.md file supports the following metadata keys:

```
---
title: My category title
---
```

The article.md files support the following frontmatter keys:

```
---
title: My article title
url: my-article-url
tags:
  - tag1
  - tag2
  - tag3 with spaces
---
```

## The file structure

Each category is expected to have a file structure like this:

```
/source/my-category/
  category.md
  an-article/
    article.md
    images/
  another-article/
    article.md
    images/
```

Tips for a successful import:

* Make sure you have a category.md file.  It's a special frontmatter markdown file describing the category title and other associated metadata for the category.
* Create a different subdirectory for each article
* Markdown files for articles must be inside those article subdirectories
* Images for articles must be inside a subdirectory of the article directory named "images"


## Deploying content to production

Any git push to the master branch triggers an import on the production site.

