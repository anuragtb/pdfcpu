---
layout: default
---

# Getting Started

## Common Flags

The following flags are used by most commands.<br>
Please refer to `pdfcpu help` + *command* for specific usage information.

### verbose, v

Enables logging on the standard output.

### vv

*Very verbose*.<br>
Enables verbose logging on the standard output.

### pages, p

A comma separated list of expressions defining the selected pages of a PDF input file.

### mode, m

Used by various commands.<br>
Please refer to [validate](core/validate.md), [extract](extract/extract.md) and [encrypt](encrypt/encryptPDF.md) for more information. 

### opw

*Owner password*<br>
Allows full access to an encrypted document including the ability to change the document’s passwords and access permissions.

### upw

*User password*<br>
Opens an encrypted document and gives access corresponding to any configured user access permissions.