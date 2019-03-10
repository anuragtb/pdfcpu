---
layout: default
---

# Watermark

NOTE

In the Adobe world a watermark is text or an image that appears either in front of or behind existing document content, like a stamp comment aka stamp annotation that anybody reading the PDF can open, edit, move around and delete. The difference here is that a watermark is integrated into a PDF page as a fixed element. Within `pdfcpu` the meaning of these terms is slightly different:

* `stamp` is any *content* that appears in front of the existing page content - sitting on top of everything else on a page

* `watermark` is any *content* that appears behind the existing page content - residing in the page background

where *content* may be text, an image or a PDF page.


---
<br>

Add watermarks to selected pages of `inFile`.<br>
A watermark is centered on the page and you can configure various aspects like rotation, scaling, opacity
and fontname, fontsize, fill color and render mode for text based watermarks.

## Usage

```
pdfcpu stamp [-v(erbose)|vv] [-pages pageSelection] [-upw userpw] [-opw ownerpw] description inFile [outFile]
```

<br>

### Flags

| flag                             | description          | required
|:---------------------------------|:---------------------|:--------
| [verbose](../getting_started.md) | turn on logging      | no
| [vv](../getting_started.md)      | verbose logging      | no
| [pages](../getting_started/page_selection) | page selection  | no
| [upw](../getting_started.md)     | user password        | no
| [opw](../getting_started.md)     | owner password       | no

<br>

### Arguments

| name         | description          | required | default
|:-------------|:---------------------|:---------|:-
| description  | configuration string | yes
| inFile       | PDF input file       | yes
| outFile      | PDF output file      | no       | inFile_new.pdf

<br>

### Description

A configuration string to specify watermark parameters.

The first entry of the description configures the type. It is one of the following:

* text string
* image file name
* PDF file name followed by an optional page number

| parameter | description                     | values                                              | default
|:----------|:--------------------------------|:----------------------------------------------------|:-
| f         | fontname, a basefont            | Helvetica, Times-Roman, Courier                     | Helvetica
| p         | fontsize in points              | in combination with absolute scaling only           | 24
| s         | scale factor                    | 0.0 < i <= 1.0 followed by optional `abs` or `rel`  | 0.5 rel
| c         | color, 3 fill color intensities | 0.0 <= r,g,b <= 1.0, eg. 1.0, 0.0 0.0 = red         | 0.5 0.5 0.5 = gray
| r         | rotation angle                  | -180.0 <= i <= 180.0                                | 0.0
| d         | render along diagonal           | 1 .. lower left to upper right                      | 1
|           |                                 | 2 .. upper left to lower right                      |
| o         | opacity                         | 0.0 <= i <= 1.0                                     | 1
| m         | render mode                     | 0 .. fill                                           | 0
|           |                                 | 1 .. stroke                                         |
|           |                                 | 2 .. fill & stroke                                  |

Only one of rotation and diagonal is allowed.

The following description parameters are for text based stamps/watermarks only:

* fontname
* color
* render mode

<br>

#### Default description

```sh
'f:Helvetica, p:24, s:0.5 rel, c:0.5 0.5 0.5, r:0, d:1, o:1, m:0'
```

* You only have to specify parameters diverging from the default.

* The standard watermark configuration is the location at the center of the page with a positive rotation along the diagonale from the lower left to the upper right page corner.

<br>

## Examples

Create a text based watermark:

<br>

Create a text based stamp:

<br>

Create an image based watermark:

<br>

Create an image based stamp:
<p align="center">
  <img style="border-color:silver" border="1" src="resources/wmImageSample.png" height="300">
</p>

<br>

Create a PDF based watermark:

<br>

Create a PDF based stamp:
<p align="center">
  <img style="border-color:silver" border="1" src="resources/wmPDFSample.jpg" height="300">
</p>




e.g. 'Draft'                                                  'logo.png'
     'Draft, d:2'                                             'logo.tif, o:0.5, s:0.5 abs, r:0'
     'Intentionally left blank, s:.75 abs, p:48'              'some.pdf, r:45'
     'Confidental, f:Courier, s:0.75, c: 0.5 0.0 0.0, r:20'   'some.pdf:3, r:-90, s:0.75'


<p align="center">
  <img style="border-color:silver" border="1" src="resources/wmTextSample.png" height="300">
</p>

<p align="center">
  <img style="border-color:silver" border="1" src="resources/wmText2Sample.png" height="300">
</p>



