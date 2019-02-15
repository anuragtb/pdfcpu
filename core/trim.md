---
layout: default
---

# Trim

Generate a trimmed version of inFile for selected pages.

## Usage

```
pdfcpu trim [-v(erbose)|vv] -pages pageSelection [-upw userpw] [-opw ownerpw] inFile [outFile]
```

| flag         | description     | required | default
|:-------------|:----------------|:---------|--------
| v(erbose)    | turn on logging | no       |
| vv           | verbose logging | no       |
| pages        | page selection  | yes      |
| upw          | user password   | no       |
| opw          | owner password  | no       |
| inFile       | PDF input file  | yes      |
| outFile      | PDF output file | no       | inFile_new.pdf

<br>

## Examples

Get rid of unwanted blank pages:

```sh
pdfcpu trim -pages even test.pdf test_trimmed.pdf
```

<br>
Create a single page PDF file for a specific page number:

```sh
pdfcpu trim -pages 1 test.pdf firstPage.pdf
```

<br>
Get rid of the catalog and trailing index:

```sh
pdfcpu trim pages '!2-4,!12-' book.pdf essence.pdf
```