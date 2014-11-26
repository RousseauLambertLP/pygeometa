# pygeometa

pygeometa is a Python package to generate metadata for geospatial datasets.

## Table of Contents
* [Overview](#overview)
* [Installation](#installation)
  * [Requirements](#requirements)
  * [Dependencies](#depedencies)
  * [Installing the Package](installing-the-package)
* [Running](#running)
  * [From the command line](#from-the-command-line)
  * [Using the API from Python](#using-the-api-from-python)
* [Development](#development)
  * [Setting up a Development Environment](#setting-up-a-development-environment)
  * [Adding Another Metadata Format](#adding-another-metadata-format)
  * [Running Tests](#running-tests)
  * [Code Conventions](#code-conventions)
  * [Bugs and Issues](#bugs-and-issues)
  * [To do](#to-do)
* [Contact](#contact)

## Overview

pygeometa is a Python package to generate metadata for geospatial datasets.

Workflow to generate metadata XML:
1. Install pygeometa
2. Create a .mcf file that contains metadata information 
  1. Refer to the [sample.mcf](/ec-msc/pygeometa/blob/master/sample.mcf) example
3. Run pygeometa for the .mcf file with a specified target metadata format


## Installation

pygeometa is best installed and used within a Python virtualenv.

### Requirements

Python 2.6 and above.  Works with Python 3.

### Dependencies

See `requirements.txt`

### Installing the Package

```bash
virtualenv my-env
cd my-env
. bin/activate
git clone http://gitlab-omnibus.ssc.etg.gc.ca/ec-msc/pygeometa.git
cd pygeometa
pip install -r requirements.txt
python setup.py build
python setup.py install
```

## Running

### From the command line

```bash
generate_metadata.py path/to/file.mcf iso19139  # to stdout
generate_metadata.py path/to/file.mcf iso19139 > some_file.xml  # to file
```

### Using the API from Python

```python
from pygeometa import render_template
xml_string = render_template('/path/to/file.mcf', 'iso19139')
with open('output.xml', 'w') as ff:
    ff.write(xml_string)
```

## Development

### Setting up a Development Environment

Same as installing a package.  Use a virtualenv.  Also install developer requirements:

```bash
pip install -r requirements-dev.txt
```

### Adding Another Metadata Format

List of supported metadata formats in `pygeometa/templates/`

To add support to new metadata formats:
```bash
cp -r pygeometa/templates/iso19139 pygeometa/templates/new-format
```
Then modify `*.j2` files in the new `pygeometa/templates/new-format` directory to comply to new metadata format.

### Running Tests

TODO

### Code Conventions

* [PEP8](https://www.python.org/dev/peps/pep-0008)

### Bugs and Issues

All bugs, enhancements and issues can be logged on SSC GitLab at
http://gitlab-omnibus.ssc.etg.gc.ca/ec-msc/pygeometa/issues

### To do

* Support local metadata format, in addition to the formats provided in `pygeometa/templates/`

## Contact

* [Tom Kralidis](http://geds20-sage20.ssc-spc.gc.ca/en/GEDS20/?pgid=015&dn=cn%3DKralidis\\%2C+Tom%2Cou%3DDAT-GES%2Cou%3DMON-STR%2Cou%3DMON-DIR%2Cou%3DMSCB-DGSMC%2COU%3DDMO-CSM%2COU%3DEC-EC%2CO%3Dgc%2CC%3Dca)
* [Alexandre Leroux](http://geds20-sage20.ssc-spc.gc.ca/en/GEDS20/?pgid=015&dn=cn%3DLeroux\\%2C+Alexandre%2Cou%3DDPS-DPS%2Cou%3DCAN-OPE%2Cou%3DCAN-CEN%2Cou%3DMSCB-DGSMC%2COU%3DDMO-CSM%2COU%3DEC-EC%2CO%3Dgc%2CC%3Dca)