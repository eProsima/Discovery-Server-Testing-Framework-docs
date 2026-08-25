# eProsima Discovery Server Testing Framework Documentation

This repository contains the sources of the documentation of the **Discovery Server testing framework**, the tool
suite used to validate the Discovery Server discovery mechanism of
[eProsima Fast DDS](https://fast-dds.docs.eprosima.com/en/latest/).

Discovery Server is a discovery mechanism built into *Fast DDS*, not a separate product.
Its description, configuration and usage are documented in the
[Fast DDS documentation](https://fast-dds.docs.eprosima.com/en/latest/fastdds/discovery/discovery.html).
The documentation built from this repository only covers how to build, configure and run the testing framework that
exercises that mechanism.

The framework's source code is hosted in the
[Discovery-Server GitHub repository](https://github.com/eProsima/Discovery-Server-Testing-Framework).

The documentation is built using [Sphinx](https://www.sphinx-doc.org), and it is hosted at
[Read the Docs](https://readthedocs.org).
The online documentation generated with this project can be found in
[Discovery Server testing framework documentation](https://eprosima-discovery-server.readthedocs.io).

1. [Project structure](#project-structure)
1. [Installation Guide](#installation-guide)
1. [Getting Started](#getting-started)
1. [Generating documentation in other formats](#generating-documentation-in-other-formats)
1. [Running documentation tests](#running-documentation-tests)
1. [Contributing](#contributing)

## Project structure

The project is structured as follows:

1. The root directory contains global scope files, such as this one.
1. The [docs directory](docs) contains all documentation source code.

## Installation Guide

1. In order to build and test the documentation, some dependencies must be installed beforehand:

    ```bash
    sudo apt update
    sudo apt install -y \
        git \
        gcc \
        g++ \
        cmake \
        curl \
        wget \
        libasio-dev \
        libtinyxml2-dev \
        doxygen \
        python3 \
        python3-pip \
        python3-venv \
        python3-sphinxcontrib.spelling \
        imagemagick
    ```

1. Clone the repository

    ```bash
    cd ~
    git clone https://github.com/eProsima/Discovery-Server-Testing-Framework-docs discovery-server-docs
    ```

1. Create a virtual environment and install python3 dependencies.

    ```bash
    cd ~/discovery-server-docs
    python3 -m venv discovery-server-docs-venv
    source discovery-server-docs-venv/bin/activate
    pip3 install -r docs/requirements.txt
    cd discovery-server-docs-venv/lib/<python-version>/site-packages
    curl https://patch-diff.githubusercontent.com/raw/sphinx-doc/sphinx/pull/7851.diff | git apply
    cd -
    ```

    The version of python3 used in the virtual environment can be seen by running the following command within the
    virtual environment:

    ```bash
    python3 -V
    ```

## Getting Started

To generate the documentation in a HTML format run:

```bash
cd ~/discovery-server-docs
source discovery-server-docs-venv/bin/activate
make html
```

## Generating documentation in other formats

The documentation can be generated in several formats such as HTML, PDF, LaTex, etc. For a complete list of targets run:

```bash
cd ~/discovery-server-docs
make help
```

Once you have selected a format, generate the documentation with:

```bash
cd ~/discovery-server-docs
source discovery-server-docs-venv/bin/activate
make <output_format>
```

## Running documentation tests

DISCLAIMER: In order to run documentation tests, access to eProsima's intranet is required.

This repository provides a set of tests that verify that:

1. The RST follows the style guidelines
1. The HTML is built correctly
1. There are no spelling errors

Run the tests by:

```bash
cd ~/discovery-server-docs
source discovery-server-docs-venv/bin/activate
make test
```

## Contributing

If you are interested in making some contributions, either in the form of an issue or a pull request, please refer to
our [Contribution Guidelines](https://github.com/eProsima/all-docs/blob/master/CONTRIBUTING.md).
