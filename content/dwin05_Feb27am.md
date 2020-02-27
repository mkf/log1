---
title: "DWIN5: Looking for an online DTD/XML validator that accepts param entities in ATTLIST"
date: 2020-02-27T04:14:22+01:00
draft: false
---

So, I now have everything from the winter semester passed besides one thing — DWIN, or "Introduction to Computer Science".

Basically I haven't been doing homework most of the time from it and now I have to correct the grade by submitting all of them by March 11th.

One of the tasks, DWIN5, is about writing an XML DTD. The one i wrote does a lot of ATTLIST reuse, so i found a stackoverflow answer
https://stackoverflow.com/a/20310012/4240261
that is basically all about using parameter entities (like character entities but with percent instead of ampersand) as preprocessor-style macros.

My assigned tasks, and current state of the draft of my submissions, are copied here https://gist.github.com/mkf/5ad36fb17a5340c095c7d25fc7eed002

The tasks text advises me to use https://www.xmlvalidation.com for validation. Except, uh, see for yourself how badly it does.
It doesn't even support Unicode in tags or anywhere, just ends up with errors that look like it's been converting to latin1 or latin2 or something.
And as obvious from the title of this post, it doesn't do the parameterentitities in ATTLIST thingie.

So I don't exactly have anything to test against. Help.

UPDATE: Moments after this post I also published ["DWIN4: Generate BMP that will achieve best compression coefficient with JPEG"](/dwin04bmpnopal_feb27am/)
