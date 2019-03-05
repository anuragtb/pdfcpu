---
layout: default
---

# Decrypt

This command decrypts `inFile` and removes password protection. If provided the decrypted PDF will be written to `outFile` and `ìnFile` remains untouched.

## Usage

```
usage: pdfcpu decrypt [-v(erbose)|vv] [-upw userpw] [-opw ownerpw] inFile [outFile]
```

### Flags

| name                             | description     | required | values
|:---------------------------------|:----------------|:---------|:------
| [verbose](../getting_started.md) | turn on logging | no       | off
| [vv](../getting_started.md)      | verbose logging | no       | off
| [upw](../getting_started.md)     | user password   | no
| [opw](../getting_started.md)     | owner password  | no

<br>

### Arguments

| name         | description         | required
|:-------------|:--------------------|:--------
| inFile       | encrypted PDF input file      | yes
| outFile      | decrypted PDF output file     | no

<br>

## Examples

Decrypt and remove password protection from `test.pdf` using the provided user password:
```sh
pdfcpu decrypt -upw upw test.pdf
writing test.pdf ...
```
<br>

Decrypt and remove password protection from `test_enc.pdf` using the provided user password and write the output file to `test.pdf`:
```sh
pdfcpu decrypt -upw upw test_enc .pdf test.pdf
writing test.pdf ...
```

<br>

Even for files protected by both passwords for decryption all you need to know  is the *user password*:

```sh
pdfcpu encrypt -opw opw -upw upw test.pdf
writing test.pdf ...

pdfcpu decrypt test.pdf
Please provide the correct password

pdfcpu decrypt -opw opw test.pdf
writing test.pdf ...
```

<br>

In fact for decryption you don't need to know the *owner password* of an encrypted file that is not protected from unauthorized opening with a *user password* :
```sh
pdfcpu encrypt -opw opw test.pdf
writing test.pdf ...

pdfcpu decrypt test.pdf 
writing test.pdf ...
```