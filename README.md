# bibSanitizer
Python script to strip specified fields out of a .bib file

# Requirements: 
Tested with: 
- [Python 3.11.1](https://www.python.org/downloads/release/python-3111/)
- [bibtexparser 1.4.0](https://pypi.org/project/bibtexparser/)

# Setup
Create a virtual environment: 

    python -m venv bib_env

activate it: 

    source bib_env/bin/activate

install dependencies: 

    pip install -r  requirements.txt

# Usage: 
## Command line args: 

    -b, --bibFile = the fileName of the bib file you want to sanitize
  
    -f, --fields  = the fields you want sanitized (optional with default values of: comment, file and groups)
  
## Example		
given a target file of *test.bib* and a list of field names *file, comment, groups*

    sanitizeBib.py -b test.bib -f file comment groups
 
We could also use

    sanitizeBib.py --bibFile test.bib --fields file comment groups

The -f / --fields argument is optional, if not used the script defaults to redacting the *file, comment* and *groups* fields. Would look like: 

    sanitizeBib.py --bibFile test.bib
  
The -b / --bibFile can also be a fully qualified file path if th .bib file is not in the same directory


## Output
The script replaces the contents of the fields with empty strings. The decision to use empty strings rather than deleting the fields entirely is deliberate and allows you to see which fields have been redacted.

The script will over-write the input .bib file with the updated .bib file. 

It will output a report with a summary of what was redacted. If the field name doesn't appear, it wasn't redacted. Example: 

    Sanitized:
      comment 6
      file 3
      groups 4
