---
layout: default
---

# Encrypt

This command encrypts `inFile` using the standard security handler as defined in [PDF 32000-1:2008](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf). If provided the encrypted PDF will be written to `outFile` and `inFile` remains untouched. Have a look at some [examples](#examples).

## Usage

```
usage: pdfcpu encrypt [-v(erbose)|vv] [-mode rc4|aes] [-key 40|128] [perm none|all] [-upw userpw] [-opw ownerpw] inFile [outFile]
```

<br>

### Flags

| name                             | description     | required | values         |default
|:---------------------------------|:----------------|:---------|:---------------|:------
| [verbose](../getting_started.md) | turn on logging | no       |
| [vv](../getting_started.md)      | verbose logging | no       |
| mode                             | encryption      | no       | rc4, aes       | aes
| key                              | key length      | no       | 40,128         | 128
| perm                             | permissions     | no       | none, all      | none
| [upw](../getting_started.md)     | user password   | no
| [opw](../getting_started.md)     | owner password  | no

<br>

### Arguments

| name         | description               | required
|:-------------|:--------------------------|:--------
| inFile       | PDF input file            | yes
| outFile      | encrypted PDF output file | no

<br>

#### mode

The [symmetric encryption algorithm](https://en.wikipedia.org/wiki/Symmetric-key_algorithm) to be used for encrypting and decrypting a document. The PDF standard security handler defines two algorithms to be used: 

* [RC4](https://en.wikipedia.org/wiki/RC4)
* [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

NOTE: RC4 is considered to be insecure!

The default mode for `pdfcpu` is AES.<br>
As of 2019 AES is still considered secure and an effective federal US government standard.

NOTE: As AES/128 is the most recent algorithm the PDF 1.7 specification defines, more secure algorithms will be needed and provided in a future release.

#### key

The length of the [cryptographic key](https://en.wikipedia.org/wiki/Key_(cryptography)) used for encryption and decryption.

Possible values:

* 40
* 128

#### perm

The set of [permissions](perm_list.md) that apply once a document has been opened.

Possible values:
* `none` clears all permission bits. This is the most restrictive way of presenting an open document to a user.

* `all` sets all permission bits allowing full access to all operations that may be applied to an open document.

NOTE: These quick primitives will be followed up by finer grained control over the permission bits in a future release.

<br>

## Examples

Encrypt `test.pdf` using the default encryption AES with a 128-bit key and the [default permissions]().
Set the owner password to `opw`. This password also known as the *master password* or the *set permissions password* may be used to change the [permissions](). Since there is no user password set any PDF Reader may open this document:

```sh
pdfcpu encrypt -opw opw test.pdf
writing test.pdf ...
```

<br>

Encrypt `test.pdf` using the default encryption AES with a 128-bit key and the [default permissions]().
Set the user password to `upw`. This password must be used to open the decrypted file. It is also known as the *open doc password*:

```sh
pdfcpu encrypt -upw upw test.pdf
writing test.pdf ...
```

<br>

Encrypt `test.pdf` using the default encryption AES with a 128-bit key and the [default permissions]().
Set the owner password to `opw` and the user password to `upw`:

```sh
pdfcpu encrypt -opw opw -upw upw test.pdf
writing test.pdf ...
```

<br>

Encrypt `test.pdf` and write the encrypted output file to `test_enc.pdf`. Use AES with a 40-bit key and [default permissions]().
Set the owner password to `opw` which will be needed to change the permissions of `test_enc.pdf`:

```sh
pdfcpu encrypt -opw opw -mode aes -key 40 test.pdf test_enc.pdf
writing test_enc.pdf ...
```

<br>

Encrypt `test.pdf` and write the encrypted output file to `test_enc.pdf`. Use RC4 with a 128-bit key and set all permissions for full access.
Set the user password to `upw` which will be needed to open `test_enc.pdf`:

```sh
pdfcpu encrypt -upw upw -mode rc4 -key 128 -perm all test.pdf test_enc.pdf
writing test_enc.pdf ...
```
