---
layout: default
---

# Split

Generate a set of PDF files for the `inFile` in `outDir` according to given `span` value.

## Usage

```
pdfcpu split [-v(erbose)|vv] [-upw userpw] [-opw ownerpw] inFile outDir [span]
```

| flag      | description         | required | default
|:----------|:--------------------|:---------|--------
| v(erbose) | turn on logging     | no       |
| vv        | verbose logging     | no       |
| upw       | user password       | no       |
| opw       | owner password      | no       |
| inFile    | PDF input file      | yes      |
| outDir    | output directory    | yes      |
| span      | split span in pages | no       | 1

<br>

## Examples

Split up a PDF input file into single page PDF output files:
```sh
pdfcpu split test.pdf out
``` 

<br>
Split up a PDF input file into individual PDF output files for every sheet of paper. Every PDF output file spans 2 pages of the original:

```sh
pdfcpu split test.pdf . 2
```
