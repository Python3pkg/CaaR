## Synopsis

The primary objective of this project is to convert recorded observations about thermostat ON/OFF cycles in cooling or heating modes into indexed time series (in pandas and NumPy).

The primary data is expected to be from these main sources of time-stamped data (but is not limited to them):
 
* cooling and heating cycles within buildings
* indoor temperature data, and
* local outdoor temperature data

Although they may be recorded independently, data can be matched based on devices, locations and time, in order to form multi-dimensional time series.

In order to maximize the utility of the package, it is possible to git clone the project, modify the configuration file, config.ini, and modify the values specified there that indicate the column headings (labels) and their positions (index) within a set of delimited text files. The example data files within the data folder are consistent with the current mapping in config.ini, and therefore provide a starting reference.

Note the need for metadata files for both thermostats and zip codes. Example files are also in the data folder.

## Motivation

This project is intended to accelerate analysis of timestamped data including thermostat operations at the device level and temperature data (indoor or outdoor) by putting them in an indexed form that is suitable for analysis in aggregated form and at the device level. It contains higher-level functions that support analysis of the data in various domains, further summarizing and helping to visualize the observations from a time series perspective easily. The ultimate intent is to support further analysis, either through forward or inverse modeling related to HVAC control, power systems or energy efficiency research.

## Installation and How to Start Using

### Dependencies

* Python 3.4+
* NumPy
* SciPy
* pandas
* click

[![Anaconda-Server Badge](https://anaconda.org/nickpowersys/caar/badges/version.svg)](https://anaconda.org/nickpowersys/caar)


[![Anaconda-Server Badge](https://anaconda.org/nickpowersys/caar/badges/installer/pypi.svg)](https://pypi.anaconda.org/nickpowersys)

    pip install -i https://pypi.anaconda.org/nickpowersys/simple caar

Documentation is at  http://caar.readthedocs.io/en/latest/

Begin by reviewing the sample input files in the data directory at https://github.com/nickpowersys/CaaR, within the data folder.

Functions in the **histsummary** and **timeseries** modules build on output from the first two modules, **cleanthermostat** and **history**.

**Cleanthermostat module**: In addition to using functions in the cleanthermostat module to create a dict or pickle file, it is also possible to run the script in picklert.py (seen in the caar folder) from the command line in order to create a pickle file based on a delimited text file. Instructions are given in the source code comments of picklert.py itself. A binary output file with a .pickle extension will be created.

**History module**: Once a pickle file or dict is created with the **cleanthermostat** module, the file name or dict can be used as an argument in order to easily create a pandas DataFrame using the DataFrame creation functions in the history module. The DataFrame will have a multi-field index, or pandas MultiIndex (using IDs and time stamps).

**Histsummary module**: This module can be used to summarize observations across thermostats or locations, as well as summarize observations for individual devices. This module uses the pandas DataFrames created by the **history** module.

**Timeseries module**: The functions in this module convert the observations from the **history** module into time series in NumPy arrays, for plotting/visualization and deeper data analysis.

## Contributors

I would welcome any feedback on features that would be useful. The project is a work in progress.

## License

This project is licensed under the terms of the BSD 3-Clause License.

[![Anaconda-Server Badge](https://anaconda.org/nickpowersys/caar/badges/license.svg)](https://anaconda.org/nickpowersys/caar)