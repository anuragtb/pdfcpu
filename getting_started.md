---
layout: default
---

# Getting Started

## Common Flags

The following flags are used by most commands. Please refer to `pdfcpu help` + *command* for specific usage information.

### verbose

Enables logging on the standard output.

### vv

*Very verbose*.
Enables verbose logging on the standard output.

### pages

A comma separated list of expressions that defines selected pages of a PDF input file.

### mode

Used by various commands.
Please refer to [validate](core/validate.md) and [extract](extract/extract.md) for more information. 

### opw

*Owner password*<br>
Allows full access to an encrypted document including the ability to change the document’s passwords and access permissions.

### upw - the user password

Opens an encrypted document and gives access corresponding to any configured user access permissions.