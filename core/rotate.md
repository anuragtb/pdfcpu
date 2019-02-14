---
layout: default
---

# Rotate

Rotate selected pages clockwise by a multiple of 90 degrees.

## Usage

```
pdfcpu rotate [-v(erbose)|vv] [-pages pageSelection] inFile rotation
```

| flag         | description       | value
|:-------------|:------------------|:-----
| v(erbose)    | turn on logging   |
| vv           | verbose logging   |
| pages        | page selection    | see [here]()
| inFile       | input PDF file    |
| rotation     | rotation angle    | -270, -180, -90, 90, 180, 270

## Examples

Rotate all pages clockwise by 90 degrees:

```sh
pdfcpu rotate test.pdf 90
```

<br>
Rotate the first two pages counter clockwise by 90 degrees:

```sh
pdfcpu rotate -pages 1-2 test.pdf -90
```