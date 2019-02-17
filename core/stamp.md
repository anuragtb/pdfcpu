---
layout: default
---

# Stamp / Watermark

Add stamps or watermarks to selected pages of `inFile`.<br>
A stamp is centered on the page and you can configure various aspects like rotation, scaling
and fontname, fontsize and color for text based stamps.

There are 3 types:

1. Text based
2. Image based
3. PDF based

Conceptually a watermark is a stamp with proper `opacity` applied.
The command `watermark` is therefore deprecated.<br>
Instead use `stamp` with a proper `o`pacity value in the command `description`.<br>
See also the examples below.


## Usage

```
pdfcpu stamp [-v(erbose)|vv] [-pages pageSelection] description inFile [outFile]
```

| flag         | description          | required
|:-------------|:---------------------|:-
| v(erbose)    | turn on logging      | no
| vv           | verbose logging      | no
| pages        | page selection       | no
| description  | configuration string | yes
| inFile       | PDF input file       | yes
| outFile      | PDF output file      | no

<br>

### Description

A configuration string to specify the details of the stamp/watermark.

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

* You only have to specify any parameter diverging from the default.

* The standard configuration for watermarks/stamps is the location at the center of the page with a positive rotation along the diagonale from the lower left to the upper right page corner.

<br>

## Examples

e.g. 'Draft'                                                  'logo.png'
     'Draft, d:2'                                             'logo.tif, o:0.5, s:0.5 abs, r:0'
     'Intentionally left blank, s:.75 abs, p:48'              'some.pdf, r:45'
     'Confidental, f:Courier, s:0.75, c: 0.5 0.0 0.0, r:20'   'some.pdf:3, r:-90, s:0.75'


<p align="center">
  <img border="1" src="resources/wmTextSample.png" height="400">
</p>

<p align="center">
  <img border="1" src="resources/wmText2Sample.png" height="400">
</p>

<p align="center">
  <img border="1" src="resources/wmImageSample.png" height="400">
</p>

<p align="center">
  <img border="1" src="resources/wmPDFSample.jpg" height="400">
</p>