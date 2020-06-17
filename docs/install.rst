.. _sect-requirements:

Installing
==========

The code has been tested with the following release of **Python**:

-  `Python - 3.8.2`_

These packages are required to run **ASteCA**:

-  `astropy`_
-  `sciPy`_
-  `matplotlib`_
-  `numpy`_

The package:

- `ptemcee 1.0.0`_

is required to run the Bayesian fundamental parameters estimation analysis.

The code also uses the packages:

- `emcee 3.0.2`_
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

     $ conda create --name asteca python=3.8.2 matplotlib=3.1.3 numpy=1.18.1 scipy=1.4.1 astropy=4.0

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


Running
-------

With the environment properly created (and activated) and the code downloaded,
you can run **ASteCA** with:

.. code-block:: bash

 (asteca) $ python asteca.py


.. _Python - 3.8.2: https://www.python.org/downloads/
.. _conda: https://conda.io/docs/index.html
.. _numpy: http://www.numpy.org/
.. _matplotlib: http://matplotlib.org/
.. _sciPy: http://www.scipy.org/
.. _astropy: http://www.astropy.org/
.. _from Github: https://github.com/Gabriel-p/asteca/releases
.. _git: http://git-scm.com/
.. _ptemcee 1.0.0: https://github.com/willvousden/ptemcee
.. _emcee 3.0.2: https://github.com/dfm/emcee/
.. _corner.py 2.0.0: https://corner.readthedocs.io/en/latest/