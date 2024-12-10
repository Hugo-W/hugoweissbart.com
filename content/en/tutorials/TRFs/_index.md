---
# Course title, summary, and position.
linktitle: A tutorial on Temporal Response Functions
summary: Learn how to use TRFs, along with some tips and tricks to go further, and faster.
weight: 1

# Page metadata.
title: TRF tutorial
date: "2018-09-09T00:00:00Z"
lastmod: "2024-09-09T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  TRFs:
    name: TRF tutorial
    weight: 1
---

# Linear models: recap

_Temporal response functions_ or TRFs are a family of linear models. Specifically the term has been coined to forward encoding model in the context of convolutive linear model applied to electrophysiological data:

$$
y(t) = (x \star \beta) (t)
$$

In the context of finite computation the convolution is both discrete and finite. In other words, our convolution is simply a linear combination of the input signal $x$ with the filter/TRF coefficients $\beta$ at different lags:

$$
y[n] &= \sum_{k=\tau_{min}}^{\tau_{max}} x[n-k] \beta[k]
$$

where $n$ is the time index, $k$ is the lag index, and $\tau_{min}$ and $\tau_{max}$ are the minimum and maximum lags, respectively.

This last equation can be written in matrix form as:

$$
\mathbf{y} = \mathbf{X} \mathbf{\beta}
$$

where $y$ is the response vector, $X$ is the design matrix, and $\beta$ is the vector of coefficients. Here we finally recover the general form of a [linear model](https://en.wikipedia.org/wiki/Linear_model) $y = X \beta$.

In our case, we generally have acces to a large number of samples compared to the number of features. That is, X has more rows than columns. We can retrieve the pseudo-inverse, and least squares solution of our model by solving the normal equation. To do so, we first left-multiply both sides of the equation by $X^T$:

$$
X^T y = X^T X \beta
$$

Then we solve for $\beta$:

$$
\beta = (X^T X)^{-1} X^T y
$$

This is the least squares solution of our linear model. In particular, the pseudo-inverse of $X$ is given by: $(X^T X)^{-1} X^T$. This is a simple linear multiplication, in matrix form, of our signal $y$, a sort of projection of $y$ onto the space spanned by the columns of $X$.

## What is a TRF?

A TRF is a linear filter that is applied to a stimulus to predict the response of a system. In the context of electrophysiology, the stimulus is the input to the system (e.g. the sound wave) and the response is the output of the system (e.g. the neural activity). The TRF is a linear filter that is applied to the stimulus to predict the response of the system.

## How to estimate a TRF?

# Forward encoding model

tbc

<iframe src='https://hugow.pythonanywhere.com/'></iframe>
