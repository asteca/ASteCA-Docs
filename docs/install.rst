.. _sect-requirements:

Installing
==========

The code has been tested with the following release of **Python**:

-  `Python - 3.9.4`_

These packages are required to run **ASteCA**:

-  `astropy`_
-  `sciPy`_
-  `matplotlib`_
-  `numpy`_
-  `emcee`_

The package:

- `ptemcee 1.0.0`_

is required to run the Bayesian fundamental parameters estimation analysis.

The code also uses the package:

- `corner.py 2.0.0`_

Both `ptemcee` and `corner.py` are included in the **ASteCA** download.


.. _sect-anaconda:

Working environment
-------------------

We use the `conda`_ package and environment manager to install all the necessary
dependencies to run **ASteCA** in an isolated **Python** environment. To install
it:

1. Go to https://conda.io/miniconda.html and download the appropriate version
   for your system. I recommend using the **Python 3.x** version and will assume
   in what follows that you are running a 64 bit Linux system.
2. Install with 

   .. code-block:: bash

     $ bash Miniconda3-latest-Linux-x86_64.sh

   Select yes when asked: *Do you whish the installer to prepend the Miniconda3
   install location to PATH in your ~/path?*
3. Close and re-open your terminal window for the changes to take effect. Move
   inside the directory where you extracted the **ASteCA** package.
4. Create a virtual environment with

   .. code-block:: bash

     $ conda create --name asteca python=3.9.4 matplotlib=3.3.4 numpy=1.20.1 scipy=1.6.2 astropy=4.2.1

5. Activate the environment

   .. code-block:: bash

    $ conda activate asteca

   (for Windows users the command is ``$ activate asteca``)

   .. important::

     You can tell that the environment is activated because its name is now
     shown in the terminal before the ``$`` symbol as:

     .. code-block:: bash

      (asteca) $

     You need to activate this environment each time **before** attempting to
     run **ASteCA**, otherwise no installed packages will be detected.

6. Install the `emcee` package with:

   .. code-block:: bash

     $ conda install -c conda-forge emcee


Download
--------

The latest packaged release (zip or tarball) can be downloaded `from Github`_.
After downloading, extract the compressed file wherever you want
the code to exist. Alternatively the entire project can be cloned via `git`_
with (Linux command):

.. code-block:: bash

    $ git clone https://github.com/asteca/ASteCA.git

which will create a sub-folder named ``/ASteCA``.


First run
---------

With the environment activated and the code uncompressed into its folder,
you can run **ASteCA** with:

.. code-block:: bash

 (asteca) $ python asteca.py

This will produce a first run of the code that should finish successfully in
a few minutes.


.. _Python - 3.9.4: https://www.python.org/downloads/
.. _conda: https://conda.io/docs/index.html
.. _numpy: http://www.numpy.org/
.. _matplotlib: http://matplotlib.org/
.. _sciPy: http://www.scipy.org/
.. _astropy: http://www.astropy.org/
.. _emcee: https://github.com/dfm/emcee/
.. _from Github: https://github.com/Gabriel-p/asteca/releases
.. _git: http://git-scm.com/
.. _ptemcee 1.0.0: https://github.com/willvousden/ptemcee
.. _corner.py 2.0.0: https://corner.readthedocs.io/en/latest/