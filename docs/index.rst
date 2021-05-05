.. ASteCA documentation master file, created by
   sphinx-quickstart on Thu Sep 18 11:26:27 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. image:: _static/front_page.png

* Article:       `ASteCA: Automated Stellar Cluster Analysis (A&A, 2015) <http://www.aanda.org/articles/aa/abs/2015/04/aa24946-14/aa24946-14.html>`_
* Site:          `asteca.github.io <http://asteca.github.io/>`_
* Source:        `github.com/asteca <https://github.com/asteca>`_

.. warning::
   This documentation is in the process of being written and it is
   **very much outdated**. Please contact me if you want to use
   **ASteCA** in your research, and I will gladly assist you.
   Last updated: May 5, 2021.

This is the manual of operation for the Automated Stellar
Cluster Analysis (**ASteCA**) package.
If you encounter any problems please `contact me`_ or `open a new issue`_.

**ASteCA** is an open source code developed entirely in Python, designed to
fully automatize the usual tests applied to stellar clusters in order to
determine their characteristics: center, radius, stars' membership probabilities
and associated intrinsic/extrinsic parameters (metallicity, age, extinction,
distance, binarity, and total mass).

The code is designed modularly thus allowing the user to select which
tests to run and which to skip, all managed through a simple input data
file.

A PDF version of this manual can be downloaded `here`__.


Table of Contents
-----------------

.. toctree::
   :numbered:
   :maxdepth: 2

   install
   input_data
   running



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

.. _contact me: mailto:gabrielperren@gmail.com
.. _open a new issue: https://github.com/Gabriel-p/asteca/issues/new
.. __: https://readthedocs.org/projects/asteca/downloads/pdf/latest/
