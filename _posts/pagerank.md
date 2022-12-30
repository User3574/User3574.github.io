---
title: PageRank
date: 2022-12-30
categories: [Recommendation systems]
tags: [pagerank, linear algebra]
math: true
---

PageRank is the core of Google's recommendation systems, and after reading the book PageRank and Beyond
I wanted to summarize the core ideas of this interesting algorithm.

### TODO: Original paper description

# Idea
Imagine that you want to sort the infinite quanta of webpages based on some criterion in
order to find some useful information.

There are some questions that we may ask ourselves, such as: How do we represent webpages and
how to quantify their importance?

Every web developer knows that HTML is the most basic language which is used to create simple webpages.
Simplest example may look like this:
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Webpage title</title>
  </head>

  <body>
    <h1>This is a simple webpage</h1>
    <p>This is a paragraph.</p>

    <h2>Links</h2>
    <a href="https://www.google.com">Link 1</a>
  </body>
</html>
```
Imagine that we want to find some information in the web, for this we create a query.
Let's restrict ourselves to the simplest, one-word queries like: ```car```.

Now we want to retrieve pages that contain information related to the query.
We can imagine this as a simple boolean search, where we may use ```<title>``` HTML page to determine if page contains specified keyword.

Our main interest here is the command that links to other webpages ```<a href="{url}">{name}</a>```.
Pages that are being linked to by other pages should be recognized as more popular and therefore displayed earlier
than the pages that receive little to no links.

As the representation of the web goes, if we use terminology from Graph theory, we can imagine webpages as nodes and the links as
respective edges between them.

Of course in reality this is complicated, for example we may use information from the ```<body>```
where most of the content of page lies. Also, one-word queries are naive, since most users use sentences as queries.

# Formulation
