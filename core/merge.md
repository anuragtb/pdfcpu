---
layout: default
---

# Merge

Merge 2 or more PDF files into `outFile`.

## Usage

```
pdfcpu merge [-v(erbose)|vv] outFile inFile...
```

| flag         | description     |
|:-------------|:----------------|
| v(erbose)    | turn on logging |
| vv           | verbose logging |
| outFile      | PDF output file |  
| inFile...    | a list of at least 2 PDF input files subject to concatenation |

## Restrictions

The following PDF features are not carried over into the merged document:

* Annotations
* Struct Trees
* Forms ?
* ...

## Example

Merge all PDF Files in the current directory into `out.pdf`:

```sh
pdfcpu merge out.pdf *.pdf
```
