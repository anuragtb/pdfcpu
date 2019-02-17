---
layout: default
---

# Optimize

Optimize `inFile` by getting rid of redundant page resources like embedded fonts and images and write the result to `outFile` maxing out compression.

## Usage

```
pdfcpu optimize [-v(erbose)|vv] [-stats csvFile] [-upw userpw] [-opw ownerpw] inFile [outFile]
```

| flag         | description         | required | default
|:-------------|:--------------------|:---------|:-
| v(erbose)    | turn on logging     | no       | off
| vv           | verbose logging     | no       | off
| stats        | generate stats file | no       | off
| upw          | user password       | no
| opw          | owner password      | no
| inFile       | PDF input file      | yes
| outFile      | PDF output file     | no       | inFile-new.pdf

### Stats

Append stats to a csv file.<br>
filename?<br>
Stats contains information useful for debugging.

## Example

Optimize `test.pdf` and write the result to `test-new.pdf`.

```sh
pdfcpu optimize test.pdf
```