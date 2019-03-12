---
layout: default
---

# Extract Attachments

This command extracts attachments from a PDF document. 
If you want to remove an extracted document you can do this using [attach remove](attach_remove.md). Have a look at some [examples](#examples).

## Usage

```
pdfcpu attach extract [-v(erbose)|vv] [-upw userpw] [-opw ownerpw] inFile outDir [file...]
```

<br>

### Flags

| name                             | description       | required
|:---------------------------------|:------------------|:--------
| [verbose](../getting_started.md) | turn on logging   | no
| [vv](../getting_started.md)      | verbose logging   | no
| [upw](../getting_started.md)     | user password     | no
| [opw](../getting_started.md)     | owner password    | no

<br>

### Arguments

| name         | description         | required
|:-------------|:--------------------|:--------
| inFile       | PDF input file      | yes
| outDir       | output directory    | yes
| file...      | one or more attachments to be extracted | yes

<br>

## Examples

Extract a specific attachment from `ledger.pdf` into `out`:

```sh
pdfcpu attach extract ledger.pdf out invoice1.pdf
extracting attachments from ledger.pdf into out ...
```

<br>

Extract all attachments of `ledger.pdf` into `out`:

```sh
pdfcpu attach extract ledger.pdf out *
extracting attachments from ledger.pdf into out ...
```
