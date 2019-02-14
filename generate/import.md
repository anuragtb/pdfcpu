---
layout: default
---

# Import

This command converts images to PDF.

* Every image file will be rendered onto a separate page.
* If you pass in a single image file name a single page PDF will be created.
* If you pass in a list of image files a picture gallery gets created which is the result of the concatenation of pages containing a single image each.
* By supplying a configuration string you can specify layout details like position, dimensions, scaling and the paper size to be used.
* The command will create the output file if it does not exist otherwise it will append to it. This feature comes in handy when you have a cover page and want to append a gallery to it.

<br>

```
usage: pdfcpu import [-v(erbose)|vv] [description] outFile imageFile...
```

| flag         | description
|:-------------|:---------------
| v(erbose)    | turn on logging
| vv           | verbose logging
| description  | configuration string
| outFile      | output PDF file
| imageFile    | image file list

<br>

## Description

A configuration string that allows you to specify the details of the image layout.

| parameter | description     | value | default
|:----------|:----------------|:------|:-----------------------------------------------------------------
| d         | dimensions      | (width,height) in user units eg. '400 200'                    | d: 595 842
| f         | form/paper size | a defined [paper size](../paper.md). Append L or P to enforce landscape/portrait mode| f: A4
| p         | position        | one of 'full' or the anchors: tl, tc, tr, l, c, r, bl, bc, br | p: full
| o         | offset          | (dx,dy) in user units eg. '15 20'                             | o: 0 0
| s         | scale factor    | 0.0 <= s <= 1.0 followed by optional 'abs' or 'rel'           | s: 0.5 rel

<br>

### Position Anchors

|||||
|-|-|-|-|
|       | left | center |right
|top    | tl   | tc     | tr
|       | l    | c      |  r
|bottom | bl   | bc     | br

<br>

The default description is:
```sh
'f:A4, d:595 842, p:full, o:0 0, s:0.5 rel'
```

* You only have to specify any parameter diverging from the default.
* Only one of dimensions or format is allowed.
* position: 'full' enforces image dimensions equal to page dimensions.

<br>

Render the image centered on A5 in landscape mode with relative scaling 0.5:
```sh
pdfcpu import 'f:A5L, p:c' out.pdf in.jpg
```
<br>

Render the image with dimensions (300, 600) anchored to the bottom left corner with offset (20, 20) and absolute scaling 1.0:
```sh
pdfcpu import 'd:300 600, p:bl, o:20 20, s:1.0 abs' out.pdf in.jpg
```
<br>

Create a single page PDF containing one image.
By using the implied default positioning parameter `p:full` the page size is going to be equal to the image size:

```sh
pdfcpu import photo.pdf photo.png
```
<br>

Generate a PDF gallery of image files assuming `pics/` contains image files (jpg, png, tif):

```sh
pdfcpu import album.pdf pics/*
```
<br>

Generate a PDF gallery of image files each of them centered on the page with a default relative scaling of 0.5 by using a description string:

```sh
pdfcpu import 'p:c' album.pdf pics/*
```
<br>

The following command also generates a PDF gallery but additionally configures paper size *Letter* and positioning anchored to the bottom left corner with a horizontal offset of 10 points and a vertical offset of 20 points in PDF user space with a scaling of 0.3 relative to page dimensions:

```sh
pdfcpu import 'f:Letter, p:bl, o:10 20, s:0.3' album.pdf *.jpg *.png
```
<br>

If a gallery created by *Import* ends up having some pages with images not in upright position the [Rotate](../core/rotate.md) command comes to the rescue. Let's say we just have created a gallery and the images on page 3 and 4 need to be rotated counter clockwise by 90 degrees. We can fix this situation with:

```sh
pdfcpu rotate -pages 3-4 album.pdf -90
```
<br>

Please also refer to `pdfcpu help import` for details about this command.