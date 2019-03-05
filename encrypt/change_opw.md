---
layout: default
---

# Change Owner Password

This command changes the *owner password* which is also known as the *set permissions password* or the *master password*.

## Usage

```
usage: pdfcpu changeopw [-v(erbose)|vv] [-upw userpw] inFile opwOld opwNew
```

<br>

### Flags

| name                             | description     | required
|:---------------------------------|:----------------|:--------
| [verbose](../getting_started.md) | turn on logging | no
| [vv](../getting_started.md)      | verbose logging | no
| [upw](../getting_started.md)     | user password   | if set

<br>

### Arguments

| name         | description            | required
|:-------------|:-----------------------|:--------
| inFile       | PDF input file         | yes
| opwOld       | current owner password | yes
| opwNew       | new owner password     | yes

<br>

opwOld ... old owner password (provide user password on initial changeopw)

<br>

## Examples