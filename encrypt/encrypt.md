---
layout: default
---

# Encrypt

This command encrypts `inFile` using the standard security handler as defined in [PDF 32000-1:2008](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf). If provided the encrypted PDF will be written to `outFile` and `inFile` remains untouched in this case.

## Usage

```
usage: pdfcpu encrypt [-v(erbose)|vv] [-mode rc4|aes] [-key 40|128] [perm none|all] [-upw userpw] [-opw ownerpw] inFile [outFile]
```

### Flags

| name                             | description     | required | values         |default
|:---------------------------------|:----------------|:---------|:---------------|:------
| [verbose](../getting_started.md) | turn on logging | no       | off
| [vv](../getting_started.md)      | verbose logging | no       | off
| mode                             | encryption      | no       | rc4, aes       | aes
| key                              | key length      | no       | 40,128         | 128
| perm                             | permissions     | no       | none, all      | none
| [upw](../getting_started.md)     | user password   | no
| [opw](../getting_started.md)     | owner password  | no

#### mode

#### key

#### perm

### Arguments

| name         | description         | required
|:-------------|:--------------------|:--------
| inFile       | PDF input file      | yes
| outFile      | PDF output file     | no

<br>

## Examples