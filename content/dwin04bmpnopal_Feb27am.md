---
title: "DWIN4: Generate BMP that will achieve best compression coefficient with JPEG"
date: 2020-02-27T04:40:36+01:00
draft: false
---

So, as i wrote in [the post about DWIN5 from moments ago](/dwin05_feb27am/), I now have everything from the winter semester passed besides one thing — DWIN, or “Introduction to Computer Science”; basically I haven’t been doing homework most of the time from it and now I have to correct the grade by submitting all of them by March 11th.

One of the tasks from the DWIN4 set is about generating a BMP file that will achieve best compression coeffiient with JPEG.

And idk if im perfectionist, but idk how should i do that

### Considerations

 * As few as possible of different values of pixels, or aberrations such that will fall under JPEG's thresholds
 * If of the different pixel values there will be less than 256, then the size of BMP will be almost precisely three times less (size of header unchanged, added the size of the palette with will be, in bytes, pallette color count × 3 (channel count), rounded up to 4 bytes), unless pallette will be disabled
   * Pallette can be disabled by generating the file with an own program. <br> The `ppmtobmp` utility does not have an option to force disabling the pallette.

### Methods

#### One color, no pallette

1. Writing a program for generating binary files from descriptions consisting of data in hexadecimal format and instruction / description language constructs:
   * repeating sequences
   * inserting integers in binary format (byte-wise little-endian)
   * evaluation of arithmetic expressions on integers for the purpose of parametrisation of the two above instructions
     * on both integer literals as well as command line provided values
One such program is [t2b](https://thosakwe.github.io/t2b/index.html) which I might just end up using.
2. Performing the task using it, by creating a BMP file of all pixels in one color with no pallette by [the method described on my wiki1 here](https://wiki1.mikf.pl/gencertainkindsoffiles/nopaletteone24bitcolorbmp.html)

#### 257 colors in stripes

Generating an image consisting of 257 horizontal stripes. It can be considered to have the colors differ only so slightly (while not creating a gradient) that they maybe could get grouped by JPEG (thresholded) — for that purpose it should be helpful to make the abberances mostly about differences on the chrominance channels (in YCbCr).

#### 256 scarce pixels in colors that could get thresholded

On a one-color background place 256 scarcely scattered pixels in different colors, of values only so slightly differing from the background colors that JPEG could maybe threshold them. Better to try having them mostly differing in the chrominance channels in YCbCr.

#### One color, with palletting

Create a bitmap with all the pixels in one color, with it being palletted. The naive solution.