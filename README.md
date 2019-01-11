# pbs-torque

This profile configures Snakemake to run on the [Torque Scheduler](http://www.adaptivecomputing.com/products/open-source/torque/).

## Setup

### Deploy profile

To deploy this profile, run

    mkdir -p ~/.config/snakemake
    cd ~/.config/snakemake
    cookiecutter https://github.com/Snakemake-Profiles/pbs-torque.git

    # In some cases it has been required to set the python scripts as executables
    cd pbs-torque
    chmod +x pbs-{status,submit}.py


Then, you can run Snakemake with

    snakemake --profile pbs-torque # add here any additional arguments


### Parameters

The following resources are supported by on a per-rule basis:

**node** - set the ppn resource request (defaults to the thread declaration).  
**mem** - set the memory resource request (bytes).  
**walltime** - set the walltime resource (secs).  

These can be specified in the `Snakefile` like so:

  ...
  rule all:
      resoures:
          node=1,
          mem=50000,
          walltime=300
      input:
  ...
