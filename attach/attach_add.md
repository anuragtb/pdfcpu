---
layout: default
---

# Add Attachments

This command embeds one or more files by attaching them to a PDF input file. Have a look at some [examples](#examples).

## Usage

```
pdfcpu attach add [-v(erbose)|vv] [-upw userpw] [-opw ownerpw] inFile file...
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
| file...      | one or more files to be attached | yes

<br>

## Examples

Attach pictures to a coverpage PDF for easy content delivery:

```sh
pdfcpu attach add album.pdf *.jpg
adding 8 attachments to album.pdf ...
writing album.pdf ...
```
