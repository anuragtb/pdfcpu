---
layout: default
---

# Grid

The *grid* command rearranges the pages of a PDF file for enhanced reading experience.

```
usage: pdfcpu grid [-v(erbose)|vv] [-pages pageSelection] [description] outFile m n inFile|imageFiles...

verbose, v ... turn on logging
         vv ... verbose logging
      pages ... page selection for inFile only
description ... dimensions, format, orientation
    outFile ... output pdf file
          m ... grid columns
          n ... grid lines
     inFile ... input pdf file
 imageFiles ... input image file(s)

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

    m: margin for content: int >= 0
```

The page size of the output file is a grid of specified dimensions in original page units.
Pages may be big but that's ok since they are not supposed to be printed. One use case mentioned by the
community was to produce PDF files for source code listings eg. in the form of 1x10 grid pages. In the 
following example we use a 1x4 grid since this is easier to visualize:

```sh
pdfcpu grid 'b:off' out.pdf 1 4 in.pdf
```

rearranges pages of in.pdf into pages composed of 1x4 grids and writes the result to out.pdf using the default orientation.<br>
The output page size is the result of a 1(horizontal) x 4(vertical) grid using in.pdf's page size:
<p align="center">
  <img border="1" src="resources/gridpdf.png" height="200">
</p>

<br>
When applied to image files this command produces simple photo galleries of arbitrary dimensions in PDF form:

```sh
pdfcpu grid 'd:500 500, m:20, b:off' out.pdf 5 2 *.jpg
```

arranges imagefiles onto a 5x2 page grid and writes the result to out.pdf using a grid cell size of 500x500:
<p align="center">
  <img border="1" src="resources/gridimg.png" height="200">
</p>
<br>

```sh
pdfcpu grid 'LegalL' out.pdf 2 2 in.pdf
```
Rearranges pages of in.pdf into 2x2 grids and write result to out.pdf using the default orientation.<br>
The output page size is the result of a 2(hor)x2(vert) page grid using page size Legal in landscape mode.<br><br>

```sh
pdfcpu grid 'o:rd' out.pdf 3 2 in.pdf
```
Rearranges pages of in.pdf into 3x2 grids and write result to out.pdf using orientation 'right down'.<br>
The output page size is the result of a 3(hor)x2(vert) page grid using in.pdf's page size.

Please also refer to `pdfcpu help grid`.