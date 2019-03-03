---
layout: default
---

# Encrypt

This command encrypts `inFile` using the standard security handler as defined in [PDF 32000-1:2008](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf). If provided the encrypted PDF will be written to `outFile` and `inFile` remains untouched in this case.

## Usage

```
usage: pdfcpu encrypt [-v(erbose)|vv] [-mode rc4|aes] [-key 40|128] [perm none|all] [-upw userpw] [-opw ownerpw] inFile [outFile]
```

