.. _sect-requirements:

Installing
==========

The code has been tested with the December 2016 release of **Python**:

-  `Python - 2.7.13`_

The packages listed below are required to run **ASteCA**.

-  `astropy`_
-  `sciPy`_
-  `matplotlib`_
-  `numpy`_ (installed along with matplotlib)
-  (optional) `R`_, `ks`_,  and `rpy2`_

.. important::

  If you want to use the function that obtains the cluster probability
  of being a true cluster (see Sect. :ref:`sect-clust-prob`), the
  **ks** statistical package is needed. This package needs ``R`` and ``rpy2``.
  These are *not mandatory* and **ASteCA** will still run without them, except
  of course the above mentioned function.


.. _sect-anaconda:

Working environment
-------------------

We use the `conda`_ package and environment manager to install all the necessary
dependencies to run **ASteCA** in an isolated **Python** environment. To install
it:

1. Go to https://conda.io/miniconda.html and download the appropriate version
   for your system. I recommend using the **Python 3.6** version and will assume
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

     $ conda create --name asteca27 python=2.7.13 matplotlib scipy astropy

5. Activate the environment

   .. code-block:: bash

    $ source activate asteca27

   (for Windows users the command is ``$ activate asteca27``)

   .. important::

     You can tell that the environment is activated because its name is now
     shown in the terminal before the ``$`` symbol as:

     .. code-block:: bash

      (asteca27) $

     You need to activate this environment each time **before** attempting to
     run **ASteCA**, otherwise no installed packages will be detected.

6. Finally (optionally), you can install the dependencies needed for the
   **ks** package with:

   .. code-block:: bash

     $ conda install -c bioconda r-ks
     $ conda install rpy2

Currently the ``r-ks`` package is not available for Windows systems.

If you are a Fedora user, you'll probably need to install a few extra libraries
for the ``rpy2`` package to work. In the case of Fedora 26, I had to install
the following libraries:

.. code-block:: bash

 $ dnf install mesa-libGLU-9.0.0-11.fc26.x86_64
 $ dnf install ncurses-compat-libs-6.0-8.20170212.fc26.x86_64

but these can change for different Fedora versions. No extra libraries where
needed in any of the Ubuntu-based systems I tested.


Download
--------

The latest packaged release (zip or tarball) can be downloaded from:

-  **ASteCA** `.zip`_
-  **ASteCA** `.tar.gz`_

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

 (asteca27) $ python asteca.py


.. _Python - 2.7.13: https://www.python.org/downloads/release/python-2713/
.. _conda: https://conda.io/docs/index.html
.. _R: http://www.r-project.org/
.. _ks: https://cran.r-project.org/web/packages/ks/index.html
.. _rpy2: http://rpy.sourceforge.net/
.. _numpy: http://www.numpy.org/
.. _matplotlib: http://matplotlib.org/
.. _sciPy: http://www.scipy.org/
.. _astropy: http://www.astropy.org/
.. _.zip: https://github.com/Gabriel-p/asteca/releases
.. _.tar.gz: https://github.com/Gabriel-p/asteca/releases
.. _git: http://git-scm.com/
