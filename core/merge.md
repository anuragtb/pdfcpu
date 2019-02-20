---
layout: default
---

# Merge

Merge 2 or more PDF files into `outFile`.

## Usage

```
pdfcpu merge [-v(erbose)|vv] outFile inFile...
```

### Flags

| name         | description       | required | default
|:-------------|:------------------|:---------|:-
| [verbose](../getting_started.md) | turn on logging     | no       | off
| [vv](../getting_started.md)      | verbose logging     | no       | off

### Arguments

| name         | description         | required
|:-------------|:--------------------|:--------
| outFile      | PDF output file     | yes  
| inFile...    | at least 2 PDF input files subject to concatenation | yes

<br>

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
