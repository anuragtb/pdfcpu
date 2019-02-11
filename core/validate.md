---
layout: default
---

# Validate

This command checks PDF files for compliance with the specification [PDF 32000-1:2008](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) (PDF 1.7).

```
usage: pdfcpu validate [-v(erbose)|vv] [-mode strict|relaxed] [-upw userpw] [-opw ownerpw] inFile
```
| flag         | description       | value
|:-------------|:------------------|:-----
| v(erbose)    | turn on logging   |
| vv           | verbose logging   |
| mode         | validation mode   | strict: (default) validates against PDF 32000-1:2008 (PDF 1.7)
|              |                   | relaxed: like strict but doesn't complain about common seen spec violations.
| upw          | user password     |  
| opw          | owner password    |

Any PDF you would like to process with `pdfcpu` needs to pass validation.

