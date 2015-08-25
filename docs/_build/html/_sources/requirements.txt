.. _sect-requirements:

Requirements
============

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
----------

If you want to use the `function`_ that obtains the cluster probability
of being a true cluster, the `R statistical software`_ is needed. It
can be installed with:

.. code-block:: bash

 $ sudo apt-get install r-base

If you get **R** version 3.0.2 (you can check this by typing ``$ R`` in a
command line) you'll need to follow the steps outlined below in order to obtain
a newer version, since that one has issues with the ``rpy2`` package.

  1. Uninstall previous r-base installation

  .. code-block:: bash

   $ sudo apt-get remove r-base-core

  2. Add the following entry to your sources (for **Ubuntu 14.04** and
  derivatives, for other distributions change the name from *trusty* to the
  correct one):

  .. code-block:: bash

   $ echo 'deb http://cran.rstudio.com/bin/linux/ubuntu trusty/' | sudo tee \
   -a /etc/apt/sources.list.d/r.list

  3. Add the Public Keys

  .. code-block:: bash

   $ gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
   $ gpg -a --export E084DAB9 | sudo apt-key add -
   $ sudo apt-get update

  4. Install **R**

  .. code-block:: bash

   $ sudo apt-get install r-base

After **R** is installed, open with sudo privileges (``$ sudo R``) and
install, *in order*, the following packages (installation commands to the
right):

-  rgl – ``install.packages("rgl")``
-  mvtnorm – ``install.packages("mvtnorm")``
-  misc3d – ``install.packages("misc3d")``
-  ks – ``install.packages("ks")``

The package `rpy2`_, that allows **Python** and **R** to communicate, is also
needed. To install it see Sect. :ref:`sect-pyth-depen`.

.. important::

  These two extra packages (**R** and ``rpy2``) are *not mandatory* and
  **ASteCA** will still run without them, just not the particular function
  mentioned above.


Python-pip
----------

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

after downloading the ``get-pip.py`` file from
`here <https://pip.pypa.io/en/latest/installing.html>`__.


.. _sect-pyth-depen:

Python dependencies
-------------------

The packages listed below are required to run **ASteCA**.

-  `numpy >= 1.8.2`_
-  `matplotlib >= 1.3.1`_ 
-  `sciPy >= 0.14.0`_
-  `astroML >= 0.2`_
-  `scikit-learn >= 0.14.1`_
-  `rpy2 >= 2.4.3`_ (optional)

These versions are the ones I used, the code could work with older versions of
the packages but I can't guarantee it.

To save some time, we install first all the required libraries listed in Sect.
:ref:`sect-trouble`:

.. code-block:: bash

  $ sudo apt-get install g++ libreadline-dev libblas-dev liblapack-dev \
  libatlas-base-dev gfortran libfreetype6-dev python-dev libevent-dev

If you are running **ASteCA**  in `Linux Mint`_, you'll probably need to install
these libraries too:

.. code-block:: bash

  $ sudo apt-get install libpcre3-dev liblzma-dev libbz2-dev

All the **Python** dependencies for can be installed at once via the
included ``requirements.txt`` file. To do this, first move into the main
**ASteCA** directory (where this file resides) and run:

.. code-block:: bash

  $ pip install --download=/tmp -r requirements.txt
  $ pip install --user --no-index --find-links=/tmp -r requirements.txt

The first command downloads all packages and the second one installs them.
We split the installation like this so that if something fails, the packages
won't have to be downloaded all over again.

.. important::

  Be aware that **R** *should already be installed* before attempting to
  install all packages using the ``requirements.txt`` file, otherwise
  the installation for the ``rpy2`` package will fail. See Sect.
  :ref:`sect-extra-pack` on how to install **R**.

  If you want to use this file to install all packages *except* ``rpy2``,
  simply open the ``requirements.txt`` file and comment this package out (or
  delete its line) before running the command shown above.

The manual way to install each of the above packages using **pip** is:

.. code-block:: bash

  $ pip install --user numpy
  $ pip install --user matplotlib
  $ pip install --user scipy
  $ pip install --user astroml
  $ pip install --user scikit-learn
  $ pip install --user rpy2

.. warning::

  Don't use ``sudo`` to apply the above commands. This may seem like a quick way
  to solve issues but it is `discouraged`_ since it can mess with your system's
  **Python**  install. If you run into any issues installing the packages, check
  Sect :ref:`sect-trouble` to see how to solve them (if your issue is not listed
  there, contact me or open an issue in the code's Github tracker).


.. pyenv
.. -----

.. This section outlines how to install a **Python** version and all
.. its dependencies in a local environment, apart from your global system
.. configuration.

.. An alternative to installing packages separately is to download a **Python**
.. distribution which comes with many packages already installed:

.. The best and easiest way to install and manage several versions of
.. **Python** and its packages without affecting your system is `pyenv`_.


.. _sect-trouble:

Troubleshooting
---------------

* If you have issues installing ``rgl`` within **R**, you probably have unmet
  dependencies.

  Install (after this, install ``rgl``):

  .. code-block:: bash

    $ sudo apt-get build-dep r-cran-rgl

  If you see an error:

  >>> E: You must put some 'source' URIs in your sources.list

  this is related to ``build-dep``. Run:

  .. code-block:: bash

    $ echo 'deb-src http://cran.rstudio.com/bin/linux/ubuntu trusty/' | sudo \
    tee -a /etc/apt/sources.list.d/r.list
    $ gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
    $ gpg -a --export E084DAB9 | sudo apt-key add -
    $ sudo apt-get update

* Error (when installing ``rpy2``):

  >>> usr/bin/ld: cannot find -l<NameOfTheLibrary>
  >>> collect2: error: ld returned 1 exit status

  this can (probably) be solved by installing:

  .. code-block:: bash

    $ sudo apt-get install lib<NameOfTheLibrary>-dev

  If this does not work, you'll need to do some `linking`_.

  Error:

  >>> gcc: error trying to exec 'cc1plus': execvp: No such file or directory

  install:

  .. code-block:: bash

    $ sudo apt-get install g++

  Error:

  >>> fatal error: readline/readline.h

  install:

  .. code-block:: bash

    $ sudo apt-get install libreadline-dev

* Error (when installing ``scipy``):

  >>> numpy.distutils.system_info.NotFoundError: no lapack/blas resources found

  install:

  .. code-block:: bash

    $ sudo apt-get install libblas-dev liblapack-dev libatlas-base-dev

  Error:

  >>> error: library dfftpack has Fortran sources but no Fortran compiler found

  install:

  .. code-block:: bash

    $ sudo apt-get install gfortran

* Error (when installing ``matplotlib``):

  >>> * The following required packages can not be built:
  >>> * freetype, png

  install:

  .. code-block:: bash

    $ sudo apt-get install libfreetype6-dev

* Error (when running ``matplotlib``):

  >>> ImportError: matplotlib requires <package>

  install (add any other missing package not listed here):

  .. code-block:: bash

    $ pip install --user python-dateutil pyparsing

* Error:

  >>> error: command 'x86_64-linux-gnu-gcc' failed with exit status 1

  install (**Python's** development headers):

  .. code-block:: bash

    $ sudo apt-get install python-dev libevent-dev


.. _Python - 2.7.8: https://www.python.org/download/releases/2.7.8/
.. _open a new issue: https://github.com/Gabriel-p/asteca/issues/new
.. _function: https://github.com/Gabriel-p/asteca/blob/master/functions/get_p_value.py
.. _R statistical software: http://www.r-project.org/
.. _rpy2: http://rpy.sourceforge.net/
.. _Linux Mint: http://www.linuxmint.com/download.php
.. _discouraged: http://www.dabapps.com/blog/introduction-to-pip-and-virtualenv-python/
.. _pip: https://pypi.python.org/pypi/pip/
.. _the docs: https://pip.pypa.io/en/latest/index.html
.. _numpy >= 1.8.2: http://www.numpy.org/
.. _matplotlib >= 1.3.1: http://matplotlib.org/
.. _sciPy >= 0.14.0: http://www.scipy.org/
.. _astroML >= 0.2: http://www.astroml.org/
.. _scikit-learn >= 0.14.1: http://scikit-learn.org/
.. _rpy2 >= 2.4.3: http://rpy.sourceforge.net/
.. _pyenv: https://github.com/yyuu/pyenv
.. _linking: http://stackoverflow.com/q/16710047/1391441
