<!--
SPDX-FileCopyrightText: 2022 Stephan Lachnit <stephanlachnit@debian.org>

SPDX-License-Identifier: CC-BY-4.0
-->

# Update copyright years for files in a git repository

[![Lint](https://github.com/stephanlachnit/update_copyright_years/actions/workflows/lint.yml/badge.svg)](https://github.com/stephanlachnit/update_copyright_years/actions/workflows/lint.yml)
[![REUSE status](https://api.reuse.software/badge/github.com/stephanlachnit/update_copyright_years)](https://api.reuse.software/info/github.com/stephanlachnit/update_copyright_years)

This Python script can automatically update the copyright year range for files in a git repository.
The initial year is determined via `git log --follow --format=%ad <file>`, meaning it takes the year when the first commit for a particular file - following renames - was authored. All times are taken in UTC.
You can check the commits on a particular file yourself using `git log --follow --reverse <file>`.

To aviod replacing random number that happen to match the pattern, you can specify an appendix and prependix to the regex pattern, or provide your own regex pattern.

You can also specify to only run the script on certain paths and specify paths to exclude.

The interace is given below:
```
usage: update_copyright_years.py [-h] [-v] [-a APPENDIX] [-p PREPENDIX] [-y YEARS] [-x EXCLUDE [EXCLUDE ...]] [-f FILES [FILES ...]]

Update copyright years for files in a git repo.

optional arguments:
  -h, --help            show this help message and exit
  -v, --verbose         enable verbose output
  -a APPENDIX, --appendix APPENDIX
                        pattern to append to year matching, i.e. <years> <pattern>
  -p PREPENDIX, --prependix PREPENDIX
                        pattern to prepend to year matching, i.e. <pattern> <years>
  -y YEARS, --years YEARS
                        regex pattern to match years
  -x EXCLUDE [EXCLUDE ...], --exclude EXCLUDE [EXCLUDE ...]
                        files to exclude
  -f FILES [FILES ...], --files FILES [FILES ...]
                        only run on specified files
```
