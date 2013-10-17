``runipy``: run IPython as a script
=====================================

The IPython notebook provides an interactive interface to a Python interpreter.

- **Literate programming**: the IPython notebook is an ideal format for
  writing "literate" programs, in which the code is part of a larger multi-media
  document. ``runipy`` lets you run such programs directly, without first
  converting to a pure Python script.
- **Report generation**: ``runipy`` can run the notebook and convert it into HTML
  in one go, making it an easy way to automate reports when aesthetic control
  is not a priority.
- **Data pipeline**: if you use IPython notebooks to create a data pipeline,
  ``runipy`` lets you automate that pipeline without losing the notebook
  formatting.

Installation
------------

The easiest way to install ``runipy`` is with ``pip``::

    $ pip install runipy

Use
---

To run a ``.ipynb`` file as a script, run::

    $ runipy MyNotebook.ipynb

To save the output of each cell back to the notebook file, run::

    $ runipy -o MyNotebook.ipynb

To save the notebook output as a *new* notebook, run::

    $ runipy MyNotebook.ipynb OutputNotebook.ipynb

To run a ``.ipynb`` file and genereate an ``HTML`` report, run::

    $ runipy MyNotebook.ipynb --html report.html

IPython Notebook Templates
--------------------------

In some use cases, it is useful to have an "template" ``.ipynb`` file that expects
some variables to be filled out. For example, in the case you want to run reports
on many similar data sets using the same basic IPython notebook template. This 
can be accomplished by having a ``ReportTemplate.ipynb`` that uses (but does not
define) certain distinguishing variables, such as *source_data_file* or 
*data_directory*. Those variables can be filled out on the command line using the 
*--initvars* option::

    $ runipy ReportTemplate.ipynb --html report.html --initvars="var1=val1 var2=val2"
	
This will take the variables and values and execute them as the first cell in the
``ReportTemplate.ipynb`` file.

This option is targeted towards 'batch' scripts that will run on numerous data
sets and execute the template notebook for each data set, resulting in a fully
processed notebook or a report. In fact, the optimal way to use this option is to
bypass the ``runipy`` command line tool altogether and generate new wrapper scripts
around the core ``notebook_runner.py``. Using ``notebook_runner`` directly works 
almost the same, but the variable/value pairs are defined in a dictionary vs a string.

Credit
------

Portions of the code are based on code by `Min RK <https://github.com/minrk>`_

