---
layout: default
---

# Rotate

This command rotates selected pages clockwise by a multiple of 90 degrees.

```
usage: pdfcpu rotate [-v(erbose)|vv] [-pages pageSelection] inFile rotation
```

| flag         | description       | value
|:-------------|:------------------|:-----
| v(erbose)    | turn on logging   |
| vv           | verbose logging   |
| pages        | page selection    | see [here]()
| rotation     | rotation angle    | -270, -180, -90, 90, 180, 270

<br>

Rotate all pages clockwise by 90 degrees:<br>
```sh
pdfcpu rotate test.pdf 90
```
<br>
Rotate the first two pages counter clockwise by 90 degrees:

```sh
pdfcpu rotate -pages 1-2 -90
```