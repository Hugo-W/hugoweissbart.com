---
# Course title, summary, and position.
linktitle: A tutorial on Temporal Response Functions
summary: Learn how to use TRFs, along with some tips and tricks to go further, and faster.
weight: 1

# Page metadata.
title: TRF tutorial
date: "2018-09-09T00:00:00Z"
lastmod: "2018-09-09T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  example:
    name: Content
    weight: 2
---

# Linear models: recap

`Temporal response functions` or TRFs are a family of linear models. Specifically the term has been coined to forward encoding model in the context of convolutive linear model applied to electrophysiological data:

$$
y(t) = (x \star \beta) (t)
$$