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
---------------------------

In some use cases, it is useful to have an "template" ``.ipynb`` file that expects
some variables to be filled out. For example, in the case you want to run reports
on many similar data sets using the same core IPython notebook. This can be 
accomplished by having a "Report Template" ``.ipynb`` that uses uses template
variables in code or non-code cells. Standard python template string formats 
are used. For example::

	$variable
	${variable}
	
To set the values for the template variables, specify the variable name and value 
on the command line using the syntax ``-T[var]=[val]``. For example::

    $ runipy ReportTemplate.ipynb OutputNotebook.ipynb -Tvar1=1 -Tvar2='Val 2'

This templated processing is targeted towards batch scripts that will iterate
over numerous data sets and execute the template notebook for each data set,
resulting in a fully processed notebook or a report. The command line interface
for runipy can be bypassed altogether and new "wrapper" scripts can be generated
around the core ``notebook_runner.py`` module. To use ``notebook_runner``, just
pass the variable/value pairs as a dictionary to the NotebookRunner constructor.

Credit
------

Portions of the code are based on code by `Min RK <https://github.com/minrk>`_

