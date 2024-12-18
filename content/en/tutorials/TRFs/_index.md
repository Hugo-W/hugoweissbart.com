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

_Temporal Response Functions_ (TRFs) are, within the framework of electrophysiology and neuroscience, a type of data-driven approximate for a neural response to a stimulus.
A first analogy of the method can be made with neural receptive-fields, where one would estimate the type of filter kernel (neural response) that a given impulse in stimulus feature space would elicit.
However, digging further outside the fields of neurosciences, one can quickly compare the methodology to the like of generalised linear modelling or [Wiener filtering](https://en.wikipedia.org/wiki/wiener_filter).

> In other words, there is absolutely **nothing** special about TRFs: they are probably the most rudimentary method one could think to etxract and interpret neural response to stimulus, when given a time-series

### Naming issue

ERP is as bad as a name as TRF, if you want to call erp "trial-averages", why not? then one would get the method but not the interpreted resulting signals. Same wiht TRF...

This simply means that the term "TRF" is redundant to its predecessor. New to neuroscience, yet old. It could be a misnomer, as to make justice to the methodology employed one could leave the name "linear modelling" but that withdraw the temporal aspect included
in the framework, or then Wiener filter (which it is exactly), but than blur the definition to other than signal processing engineers, "time-lagged regression" maybe? But that would sound like we are only trying to please statistician. Maybe it's indeed a name per field.
An important difference between TRF and all other method names out there (albeit them being the same underlying maths), is that in the case of the TRFs, we, as neuroscientist, directrly _interpret_ and _analyse_ the resulting regression coefficients **as if they were neural signals.**

The techniques or algorithms used to estimate the temporal response functions are

# Linear models: recap

_Temporal response functions_ basically belongs to the family of linear models. Specifically to convolutive linear model, in our case, applied to electrophysiological data:

$$
y(t) = (x \star \beta) (t)
$$

In the context of finite computation the convolution is both discrete and finite. In other words, our convolution is simply a linear combination of the input signal $x$ with the filter/TRF coefficients $\beta$ at different lags:

$$
y[n] = \sum_{k=\tau_{min}}^{\tau_{max}} x[n-k] \beta[k]
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

## TRF: a signal processing perspective?

In signal processing, it is well known that "a multiplication in Fourier domain, is a convolution in time domain" and vice-versa.
So if we were to filter a signal (removing some of its frequency content), one could imagine directly multiplying **spectra** of two kind:
- the signal's spectrum
- some window over the frequency we want, such that we would zero out unwanted frequencies from the signal spectrum

Thus, in the time domain, filtering a signal would merely correspond to a temporal convolution.
Exactly. I'll pass the details concerning aliasing, time discrete formulation, and finite vs infinite impulse response, but in short, yes filtering a signal boils down to convolving it with another signal (the filter _kernel_).

Now the TRF formulation directly involves a convolution and can be treated, in fact, as a filter. In that sense, we would interpret the **brain as a linear, time-invariant system which transforms the input signals (stimulus features) into neural responses through a transfer function**.
The transfer function thus corresponds to the filter kernel, aka the TRFs.

> A TRF is a linear filter that is applied to a stimulus to predict the response of a system. In the context of electrophysiology, the stimulus is the input to the system (e.g. the sound wave) and the response is the output of the system (e.g. the neural activity).

# Forward encoding model

tbc

