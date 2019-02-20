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
| verbose      | turn on logging     | no       | off
| vv           | verbose logging     | no       | off
| stats        | CSV output file     | no       | off
| upw          | user password       | no
| opw          | owner password      | no

<br>

| parameter    | description         | required | default
|:-------------|:--------------------|:---------|:-
| inFile       | PDF input file      | yes
| outFile      | PDF output file     | no       | inFile_new.pdf

### Stats

The name of a CSV file name.<br>
This command appends one CSV line with stats about memory usage before and after optimization, PDF object usage and other useful information for debugging.
Optimize a group of PDF input files and consolidate stats into the same CSV file for comparison.

## Example

Optimize `test.pdf` and write the result to `test_new.pdf`:

```sh
pdfcpu optimize test.pdf
writing test_new.pdf ...
```

Optimize `test.pdf` and write the result to `test_opt.pdf`:

```sh
pdfcpu optimize test.pdf test_opt.pdf
writing test_opt.pdf ...
```

Optimize `test.pdf`, write the result to `test_opt.pdf`, append stats to `stats.csv` and produce logging on standard out:

```sh
pdfcpu optimize -verbose -stats stats.csv test.pdf test_opt.pdf
stats will be appended to stats.csv
 INFO: 2019/02/20 22:30:08 reading test.pdf..
 INFO: 2019/02/20 22:30:08 PDF Version 1.5 conforming reader
 INFO: 2019/02/20 22:30:08 validating
 INFO: 2019/02/20 22:30:08 optimizing fonts & images
STATS: 2019/02/20 22:30:08 XRefTable:
*************************************************************************************************
HeaderVersion: 1.2
has 2 pages
XRefTable:
                     Size: 13
              Root object: (11 0 R)
              Info object: (12 0 R)
                ID object: [<81C4A57DF6A1E411BD62885083B053CD> <81C4A57DF6A1E411BD62885083B053CD>]
XRefTable with 13 entres:
    0: f   next=       0 generation=65535
    1:   offset=      16 generation=0 pdfcpu.Dict type=Page
<<
	<Contents, (2 0 R)>
	<Parent, (3 0 R)>
	<Resources, (4 0 R)>
	<Type, Page>
>>
    2:   offset=     102 generation=0 pdfcpu.StreamDict
<<
	<Filter, LZWDecode>
	<Length, 2652>
>>
    3:   offset=    5117 generation=0 pdfcpu.Dict type=Pages
<<
	<Count, 2>
	<Kids, [(1 0 R) (8 0 R)]>
	<MediaBox, [0 0 595.27 841.89]>
	<Type, Pages>
>>
```