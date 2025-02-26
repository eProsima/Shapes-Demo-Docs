# eProsima Shapes Demo Documentation

[![Releases](https://img.shields.io/github/release/eProsima/ShapesDemo.svg)](https://github.com/eProsima/ShapesDemo/releases)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Linux Build Status](http://jenkins.eprosima.com:8080/job/nightly_shapes-demo-docs_master/badge/icon)](http://jenkins.eprosima.com:8080/job/nightly_shapes-demo-docs_master)

<a href="http://www.eprosima.com"><img src="https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcSd0PDlVz1U_7MgdTe0FRIWD0Jc9_YH-gGi0ZpLkr-qgCI6ZEoJZ5GBqQ" align="left" hspace="8" vspace="2" width="100" height="100" ></a>


eProsima Shapes Demo is an application in which Publishers and Subscribers are shapes of different colors and sizes moving on a board. Each shape refers to its own topic: Square, Triangle or Circle. A single instance of the eProsima Shapes Demo can publish on or subscribe to several topics at a time.

<br/>

## Commercial support

Looking for commercial support? Write us to info@eprosima.com

Find more about us at [eProsima’s webpage](https://eprosima.com/).

## Overview

eProsima Shapes Demo can be used to demonstrate the capabilities of eProsima Fast DDS or as a proof of interoperability with other RTPS-compliant implementations.

For more information about the application, check out the [eProsima Shapes Demo documentation](https://eprosima-shapes-demo.readthedocs.io/en/latest/).
You can find all the application's source code on our [GitHub repository](https://github.com/eProsima/ShapesDemo).

1. [Installation Guide](#installation-guide)
1. [Getting Started](#getting-started)
1. [Generating documentation in other formats](#generating-documentation-in-other-formats)
1. [Running documentation tests](#running-documentation-tests)

## Installation Guide

1. In order to build and test the documentation, some dependencies must be installed beforehand:

    ```bash
    sudo apt update
    sudo apt install -y \
        git \
        python3 \
        python3-pip \
        python3-venv \
        python3-sphinxcontrib.spelling \
    ```

1. Clone the repository

    ```bash
    cd ~
    git clone https://github.com/eProsima/Shapes-Demo-Docs shapes-demo-docs
    ```

1. Create a virtual environment and install python3 dependencies

    ```bash
    cd ~/shapes-demo-docs
    python3 -m venv shapes-demo-docs-venv
    source shapes-demo-docs-venv/bin/activate
    pip3 install -r docs/requirements.txt
    ```

## Getting Started

To generate the documentation in a HTML format for a specific branch of eProsima Shapes Demo run:

```bash
cd ~/shapes-demo-docs
source shapes-demo-docs-venv/bin/activate
make html
```

## Generating documentation in other formats

The documentation can be generated in several formats such as HTML, PDF, LaTex, etc. For a complete list of targets run:

```bash
cd ~/shapes-demo-docs
make help
```

Once you have selected a format, generate the documentation with:

```bash
cd ~/shapes-demo-docs
source shapes-demo-docs-venv/bin/activate
make <output_format>
```

## Running documentation tests

This repository provides a set of tests that verify that:

1. The RST follows the style guidelines
1. There are no spelling errors
1. The HTML is built correctly

Run the tests by:

```bash
cd ~/shapes-demo-docs
source shapes-demo-docs-venv/bin/activate
make test
```

## Contributing

If you are interested in making some contributions, either in the form of an issue or a pull request, please refer to
our [Contribution Guidelines](https://github.com/eProsima/all-docs/blob/master/CONTRIBUTING.md).
