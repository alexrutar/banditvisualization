# Bandit Visualization Documentation
_IN PROGRESS_

This Bandit Visualization module provides an easy-to-use library for implementing and visualizing various Bandit algorithms and environments in machine learning. If you are looking for the following, this library is not for you:
- You want something fast and efficient,
- You want a tool to run very large simulations
It is good to use if you want to
- Visualize your algorithms in various ways
- Easily add new algorithms to the existing ones (fully in python and numpy)
-


## Usage
This library is dependent on the following modules:
- yaml
- numpy
- matplotlib
- scipy


## Minilanguage Syntax

## Further Details

### Build File Structure
(note: the current file structure is temporary and bound to change)
The *Build* folder countains five sub-folders:
- Core: Files relevant to the underlying Bandit algorithms and environment
- Parse: Files used to take an user-input file

### Notes
The critical importance of core_dict
    everything is stored here; during run.py, it is made by calling Parse on some input file
    once the core_dict is made, you NEVER change it; if you need a local version make a deepcopy
    also, you can't add anything to it; all additions etc. should be done during Parse or dictCheck
        since all information is stored here, this is sufficient to do anything desired, in theory
    after the core_dict is made, you can pass it around to various functions
        DataGen functions use the core dict to make data files
        Plot functions use the core dict and data files to make plots
            Animate functions use the core dict to make animations
    the efficiency of this paradigm is that it allows various functions to operate completely independently of each other!
        this makes process management trivial; very few checks are needed (only using join() to make sure data is done before making a plot, etc)
    all communication between DataGen and Plot functions is done by reading and writing to text files; this is described in more detail under Data generation / saving procedure

sub_dict notation:  // explain notation used in general
    sub_dict is some sub dictionary of core_dict

Processes, opening subprocesses, mac limitations, etc.
    all graphical processes must be in main
    all code data generation must be a subprocess
    static graphic generation must wait until all data subprocesses are done
    no writing can be done in a BuildData file; opened in different process and islated

Data generation / saving procedure
    file system / data saving (timestamped)
    file creation rules
    file writing rules
        only open when writing
        always use append
        writing with newlines

Output file procedure

interface.py and run.py
Outline general code structure