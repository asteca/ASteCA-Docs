Download
========

The latest packaged release (zip or tarball) can be downloaded from:

-  **ASteCA** `.zip`_
-  **ASteCA** `.tar.gz`_

After downloading, extract the compressed file wherever you want
the code to exist.
No further installation is necessary with the exception of the
requirements listed below.


Requirements
------------

The code has been tested with the July 2014 release of **python**:

-  `Python - 2.7.8`_

It should also work on older versions, if you encounter any problems
please contact me or `open a new issue`_.

To check the version of **python** installed in your system simply run in
a terminal the command:

.. code-block:: bash

   $ python --version

The output will resemble this:

.. code-block:: bash

  Python 2.7.3

If your version is ``2.7.x`` you are probably good to go. If you are using
the new ``3.x`` version of **python** I assume you know what you are doing
and can figure out how to run the code in a ``2.7.x`` environment.


Python dependencies
...................

The packages listed below are required to run **ASteCA**.

-  `numpy >= 1.8.2`_
-  `matplotlib >= 1.3.1`_ 
-  `sciPy >= 0.14.0`_
-  `astroML >= 0.2`_
-  `scikit-learn >= 0.14.1`_

These versions are the ones I used, the code could work with older
versions of the packages but I can't guarantee it.
The recommended way to install each of the above packages is to
use `pip`_ (see `the docs`_ for more information on this tool):

.. code-block:: bash

  $ pip install numpy
  $ pip install matplotlib
  $ pip install scipy
  $ pip install astroml
  $ pip install scikit-learn

If you get a *Permission denied* error, append `sudo` before
the above commands.

If **pip** is not installed in your system, you can install it
(assuming **python** is) via:

.. code-block:: bash

  $ python get-pip.py

after downloading the ``get-pip.py`` file from `here`_.

If when attempting to install `matplotlib` the system returns the error:

.. code-block:: bash

  * The following required packages can not be built:

  * freetype, png

this means you need to install the following package first:

.. code-block:: bash

  $ sudo apt-get install libfreetype6-dev

If you're also getting the error:

.. code-block:: bash

  error: command 'x86_64-linux-gnu-gcc' failed with exit status 1

you'll need to install **python's** development headers with:

.. code-block:: bash

  sudo apt-get install python-dev 


Extra packages
..............

If you want to use the `function`_ that obtains the cluster probability
of being a true cluster, the following software is needed:

-  `R - 3.0.1`_

which can be installed with:

.. code-block:: bash

 $ sudo apt-get install r-base

After **R** is installed, open with sudo privileges (``sudo R``) and
install, *in order*, the packages (installation commands to the right):

-  rgl – ``install.packages("rgl")``
-  mvtnorm – ``install.packages("mvtnorm")``
-  misc3d – ``install.packages("misc3d")``
-  ks – ``install.packages("ks")``

The package that allows **python** and **R** to communicate is also
needed:

-  `rpy2 -2.4.3`_

which you can install via:

.. code-block:: bash

  $ pip install rpy2

These extra packages are *not mandatory* and **ASteCA** will still run without
them, just not the particular function mentioned above.

.. important::

  All the dependencies can be installed at once via the included
  ``requirements.txt`` file. To do this, first move into the main **ASteCA**
  directory (the one that contains this file) and run:

  .. code-block:: bash

    $ pip install --download=/tmp -r requirements.txt
    $ pip install --no-index --find-links=/tmp -r requirements.txt

  The first command downloads all packages and the second one installs them.
  We split the installation like this so that if something fails, the packages
  won't have to be downloaded all over again.

.. warning::

  Be aware that **R** *should already be installed* before attempting to
  install all packages using the ``requirements.txt`` file, otherwise
  the installation for the ``rpy2`` package will fail.

  If you want to use this file to install all packages *except* ``rpy2``,
  simply open the ``requirements.txt`` file and comment this package out (or
  delete its line) before running the command shown above.


Python distributions
--------------------

An alternative to installing packages separately is to download a **python**
distribution which comes with many packages already installed:

-  `Anaconda`_
-  `Canopy`_

The best and easiest way to install and manage several versions of
**python** and its packages without affecting your system is `pyenv`_.


Cloning the repository
----------------------

The entire project can be cloned via `git`_. Simply
locate yourself in the folder you want the code to be downloaded and
run the following command in a terminal:

.. code-block:: bash

    $ git clone https://github.com/Gabriel-p/asteca.git

This will create a new sub-folder named ``/asteca`` with all the necessary
files and code stored inside.


.. _.zip: https://github.com/Gabriel-p/asteca/releases
.. _.tar.gz: https://github.com/Gabriel-p/asteca/releases
.. _git: http://git-scm.com/
.. _Python - 2.7.8: https://www.python.org/download/releases/2.7.8/
.. _open a new issue: https://github.com/Gabriel-p/asteca/issues/new
.. _pip: https://pypi.python.org/pypi/pip/
.. _the docs: https://pip.pypa.io/en/latest/index.html
.. _numpy >= 1.8.2: http://www.numpy.org/
.. _matplotlib >= 1.3.1: http://matplotlib.org/
.. _sciPy >= 0.14.0: http://www.scipy.org/
.. _astroML >= 0.2: http://www.astroml.org/
.. _scikit-learn >= 0.14.1: http://scikit-learn.org/
.. _Anaconda: https://store.continuum.io/cshop/anaconda/
.. _Canopy: https://www.enthought.com/products/canopy/
.. _pyenv: https://github.com/yyuu/pyenv
.. _function: https://github.com/Gabriel-p/asteca/blob/master/functions/get_p_value.py
.. _R - 3.0.1: http://www.r-project.org/
.. _rpy2 -2.4.3: http://rpy.sourceforge.net/
.. _here: https://pip.pypa.io/en/latest/installing.html