---
layout: default
---

# Change User Password

This command changes the *user password* which is also known as the *open doc password*.

# Usage

```
usage: pdfcpu changeupw [-v(erbose)|vv] [-opw ownerpw] inFile upwOld upwNew
````

<br>

### Flags

| name                             | description     | required
|:---------------------------------|:----------------|:--------
| [verbose](../getting_started.md) | turn on logging | no
| [vv](../getting_started.md)      | verbose logging | no
| [opw](../getting_started.md)     | owner password  | if set

<br>

### Arguments

| name         | description            | required
|:-------------|:-----------------------|:--------
| inFile       | PDF input file         | yes
| upwOld       | current user password  | yes
| upwNew       | new user password      | yes

<br>

## Examples