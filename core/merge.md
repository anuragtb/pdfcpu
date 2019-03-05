---
layout: default
---

# Merge

Merge 2 or more PDF files into `outFile`.

## Usage

```
pdfcpu merge [-v(erbose)|vv] outFile inFile...
```

<br>

### Flags

| name         | description       | required | default
|:-------------|:------------------|:---------|:-
| [verbose](../getting_started.md) | turn on logging     | no       | off
| [vv](../getting_started.md)      | verbose logging     | no       | off

<br>

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

pdfcpu respects the order of the provided input files and merges accordingly. Merge three input files into `out.pdf` by concatenating `in3.pdf` to `in2.pdf` and the result to `in1.pdf`:

```sh
pdfcpu merge out.pdf in1.pdf in2.pdf in3.pdf
```

<br>

Merge all PDF Files in the current directory into `out.pdf`:

```sh
pdfcpu merge out.pdf *.pdf
```