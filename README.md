# plots

A repository of visualizations for policy reforms.

### What is a plot?

Plots are single html files which contain visual elements (e.g. images, charts, graphs) to communicate an insight regarding some facet of economic policy.

### Installation

Install the plots package using the following commmand:

```bash
python setup.py install
```

TODO: Add conda recipe

### Create A Plot
#### info.yml
The `info.yml` file contains metadata for the plot and is required to contain the following key-value pairs:

```yml
plot_name: Tax Reform Explorer
plot_id: tax_reform_explorer
content: tax-reform-explorer.html
thumbnail: thumbnail.png
short_description: This plot shows a short amount of stuff
long_description: This plot shows a long amount of stuff
Concept_credit: Citation for concept
Development_credit: Citation for development
OSS_credit: Citation for open source software projects
best_width: recommended width when embedding
best_height: recommended height when embedding
build_cmd: shell command used to build the plot
version: version number
```

#### resources directory
Any supporting files (e.g. `.js`, `.css`, `.png`) should be placed in a `resources` directory within the plot directory. 

**Note:** All files placed in the `resources` will be uploaded/made-public to taxplots.

#### environment.yml

`Conda` `environment.yml` files allow for reproducible environments for building plots.  The `plots` tools as a whole have an `environment.yml` file located in the root of the code repository.  Each plot in `contrib` is also required to have an `environment.yml` file.  When building a plot, that plot's environment file should be active. 

To create an `environment.yml` file from an existing conda environment, browse to the plot's directory in your preferred shell, and run `conda env export > environment.yml`.

Example Output:
```yml
name: my_viz_env
dependencies:
- pytest
- setuptools
- python
- numpy
- pandas <=0.16.2
- numba
- toolz
- six
- ipython
- ipython-notebook
- bokeh
- pip:
  - pytest-pep8
```


To recreate the environment specified in the plot's `environment.yml` file, browse to the plot's directory in your preferred shell, and run `conda env create`. Then activate the environment with `source activate <env-name>`

### Plot Command-line Tools
Install with the taxplots python package is a command-line interface (cli) which provides the following utilites:

#### List Plots
```bash
list-plots
```

The `list-plots` commnad will display information about plots available in the `contrib` directory.


#### Upload Plots

The `upload-plots` cli tool will upload plots to an s3 bucket and including a `web_manifest.json` file which can be used to discover available plots from a 3rd Party applications.

```bash
upload-plots
```

To use the upload utility, you must have the following environment variables set:

```bash
    export AWS_KEY_ID=<my_aws_access_key>
    export AWS_SECRET_ID=<my_aws_secret_key>
    export TAXPLOT_S3_BUCKET=taxplots
```

TODO: Add content

### Contributing a Plot
- fork this repository
- add a new plot directory to the `contrib` directory whose name should contain **no spaces**, or invalid url characters.
- to your new directory, add the `html file` which represents your plot
- submit a Pull Request to `taxplots`
