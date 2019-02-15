---
layout: default
---

# Validate

This command checks PDF files for compliance with the specification [PDF 32000-1:2008](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) (PDF 1.7). Any PDF you would like to process with `pdfcpu` needs to pass validation.

## Usage

```
pdfcpu validate [-v(erbose)|vv] [-mode strict|relaxed] [-upw userpw] [-opw ownerpw] inFile
```

| flag         | description       | value
|:-------------|:------------------|:-----
| v(erbose)    | turn on logging   |
| vv           | verbose logging   |
| mode         | validation mode   | strict, relaxed
| upw          | user password     |  
| opw          | owner password    |

<br>

## Mode

### Strict

This mode validates against the specification [PDF 32000-1:2008](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) covering all PDF versions up to 1.7.

### Relaxed

This mode behaves like strict but does not complain about common seen violations of the specification by PDF writers.