---
layout: default
---

# N-up

```
usage: pdfcpu nup [-v(erbose)|vv] [-pages pageSelection] [description] outFile n inFile|imageFiles...

This reduces the number of pages and therefore the required print time.
If the input is one imageFile a single page n-up PDF gets generated.

 verbose, v ... turn on logging
         vv ... verbose logging
      pages ... page selection for inFile only
description ... dimensions, format, orientation
    outFile ... output pdf file
          n ... the n-Up value (see below for details)
     inFile ... input pdf file
 imageFiles ... input image file(s)

                             portrait landscape
 Possible values for n: 2 ...  1x2       2x1
                        3 ...  1x3       3x1
                        4 ...  2x2
                        8 ...  2x4       4x2
                        9 ...  3x3
                       12 ...  3x4       4x3
                       16 ...  4x4

    <description> is a comma separated configuration string containing:

    optional entries:

        (defaults: d:595 842, f:A4, o:rd, b:on, m:3)

    d: dimensions (width,height) in user units eg. '400 200'

    f: form/paper size, eg. A4, Letter, Legal...
                           Please refer to "pdfcpu help paper" for a comprehensive list of defined paper sizes.
                           Appended 'L' enforces landscape mode. (eg. A3L)
                           Appended 'P' enforces portrait mode. (eg. TabloidP)
                           Only one of dimensions or format is allowed.

    o: orientation, one of rd ... right down (=default)
                           dr ... down right
                           ld ... left down
                           dl ... down left
                           Orientation applies to PDF input files only.

    b: draw border ... on/off true/false

    m: margin for n-up content: int >= 0
```

The `nup` (`n-up`) command rearranges the pages of a PDF file in order to reduce its page count.
This is achieved by rendering the input pages onto a grid which dimensions are defined by the supplied [N-up](https://en.wikipedia.org/wiki/N-up) value. It is also possible to process one or more image files with this command (see below).

Defined values for `n`: 2, 3, 4, 6, 8, 9, 12, 16.

Defined values for `orientation`:
* **rd** (right, down) = default
* dr (down, right)
* ld (left, down)
* dl (down, left)<br>

Proper rotation based on involved aspect ratios will be applied during the process. 

```sh
pdfcpu nup out.pdf 4 in.pdf
```

 produces a PDF-file where each page fits 4 original pages into a 2x2 grid:<br>

<p align="center">
  <img border="2" src="resources/nup4pdf.png" height="200">
</p>

The output file will use the page size of the input file unless explicitly declared by a description string like so:<br>

```sh
pdfcpu nup 'f:A4' out.pdf 9 in.pdf
```

<p align="center">
  <img border="2" src="resources/nup9pdf.png" width="145">
</p>

Please refer to [pdfcpu paper](../paper.md) for a list of supported paper formats.
Most well known paper size standards are supported.

`nup` also accepts a list of image files with the result of rendering all images
in N-up fashion into a PDF file using the specified paper size (default=A4):<br>

```sh
pdfcpu nup 'f:A4L' out.pdf 4 *.jpg *.png *.tif
````

generates a PDF file using *A4 Landscape* where each page fits 4 images onto a 2x2 grid.
Grid border lines are rendered by default:
<p align="center">
  <img border="2" src="resources/nup4img.png" height="200">
</p>

A single image input file will produce a single page PDF with the image N-up'ed accordingly, eg.:

```sh
pdfcpu nup 'f:Ledger, b:off, m:0' out.pdf 16 logo.jpg
```

Both grid borders and margins are suppressed in this example and the output format is *Ledger*:
<p align="center">
  <img border="2" src="resources/nup16img.png" height="200">
</p>
<br>