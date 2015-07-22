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

The code has been tested with the July 2014 release of **Python**:

-  `Python - 2.7.8`_

It should also work on older versions, if you encounter any problems
please contact me or `open a new issue`_.

To check the version of **Python** installed in your system simply run in
a terminal the command:

.. code-block:: bash

   $ python --version

The output will resemble this:

.. code-block:: bash

  Python 2.7.3

If your version is ``2.7.x`` you are probably good to go. If you are using
the new ``3.x`` version of **Python** I assume you know what you are doing
and can figure out how to run the code in a ``2.7.x`` environment.


.. _sect-extra-pack:

R software
..........

If you want to use the `function`_ that obtains the cluster probability
of being a true cluster, the `R statistical software`_ is needed. It
can be installed with:

.. code-block:: bash

 $ sudo apt-get install r-base

After **R** is installed, open with sudo privileges (``sudo R``) and
install, *in order*, the following packages (installation commands to the
right):

-  rgl – ``install.packages("rgl")``
-  mvtnorm – ``install.packages("mvtnorm")``
-  misc3d – ``install.packages("misc3d")``
-  ks – ``install.packages("ks")``

The package `rpy2`_, that allows **Python** and **R** to communicate, is also
needed. To install it see Sect. :ref:`sect-pyth-depen`.

.. important::

  These two extra packages are *not mandatory* and **ASteCA** will still run
  without them, just not the particular function mentioned above.


Python-pip
...................

The `pip`_ tool for installing **Python** packages (see `the docs`_ for more
information) should be included by default for **Python** versions 2.7.7 and
above. To check if it is installed in your system run:

.. code-block:: bash

  $ pip list

If **pip** is installed, it should return a list of the packages available
in your system. If **pip** is not installed, you can get it via:

.. code-block:: bash

  $ sudo apt-get install python-pip

or manually with:

.. code-block:: bash

  $ python get-pip.py

after downloading the ``get-pip.py`` file from `here`_.


.. _sect-pyth-depen:

Python dependencies
...................

The packages listed below are required to run **ASteCA**.

-  `numpy >= 1.8.2`_
-  `matplotlib >= 1.3.1`_ 
-  `sciPy >= 0.14.0`_
-  `astroML >= 0.2`_
-  `scikit-learn >= 0.14.1`_
-  `rpy2 >= 2.4.3`_ (optional)

These versions are the ones I used, the code could work with older
versions of the packages but I can't guarantee it.

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
  the installation for the ``rpy2`` package will fail. See Sect.
  :ref:`sect-extra-pack` on how to install **R**.

  If you want to use this file to install all packages *except* ``rpy2``,
  simply open the ``requirements.txt`` file and comment this package out (or
  delete its line) before running the command shown above.

The manual way to install each of the above packages is to use **pip**:

.. code-block:: bash

  $ pip install numpy
  $ pip install matplotlib
  $ pip install scipy
  $ pip install astroml
  $ pip install scikit-learn
  $ pip install rpy2

If you get a *Permission denied* error, append ``sudo`` before the above
commands.


Possible errors
...............

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

you'll need to install **Python's** development headers with:

.. code-block:: bash

  $ sudo apt-get install python-dev libevent-dev

If you have issues installing ``rgl`` within **R**, you probably have unmet
dependencies. These can be fixed by running in a terminal:

.. code-block:: bash

  $ sudo apt-get build-dep r-cran-rgl

and then installing ``rgl`` from within **R**.


Python distributions
--------------------

An alternative to installing packages separately is to download a **Python**
distribution which comes with many packages already installed:

-  `Anaconda`_
-  `Canopy`_

The best and easiest way to install and manage several versions of
**Python** and its packages without affecting your system is `pyenv`_.


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
.. _rpy2 >= 2.4.3: http://rpy.sourceforge.net/
.. _Anaconda: https://store.continuum.io/cshop/anaconda/
.. _Canopy: https://www.enthought.com/products/canopy/
.. _pyenv: https://github.com/yyuu/pyenv
.. _function: https://github.com/Gabriel-p/asteca/blob/master/functions/get_p_value.py
.. _R statistical software: http://www.r-project.org/
.. _rpy2: http://rpy.sourceforge.net/
.. _here: https://pip.pypa.io/en/latest/installing.html