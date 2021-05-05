Running
=======

To run the code simply position a cluster’s photometric data file in the
``input/`` folder, modify the ``params_input.dat`` file to both
inform the code of the distribution of columns in your photometric file
and set the values for each function within the code.
Photometric files can also be stored in ``input/`` inside a
sub-folder.

**Every** file inside the ``input/`` folder (inside or outside a
sub-folder) will be processed by **ASteCA**, with the exception of the
membership probabilities files that end with a ``_memb.dat`` extension
(see Sect. :ref:`decont-algor`).

Once the file(s) are in place and the ``params_input.dat`` file correctly
modified, the code can be executed with the command:

.. code-block:: bash

    (asteca) $ python asteca.py

This should work both in Linux based systems and OS X (Mac), but I've
only tested it with Linux (since that's what I use).

The ``CLUSTER.DAT`` file located in the ``input/`` folder contains
a synthetic open cluster generated with Gaia EDR3 photometry and the
following parameter values:

::

	z = 0.0151
	log(age) = 8.5
	E(B-V) = 0.5
	(m-M)o = 12.0
	M = 2000 Mo
        b_fr = 0.3

and serves as an example cluster to be analyzed with **ASteCA**.


Theoretical isochrones
----------------------

**ASteCA** needs at least one set of theoretical isochrones stored in the
``isochrones/`` folder, to be able to apply the *best-fit* function that
estimates the clusters’ parameters.
Currently, the only isochrone files supported are those obtained via the
`CMD service`_ (`Girardi et al. 2002`_), but any set can in theory be used
(with some changes made to the code).
Please `contact me <gabrielperren@gmail.com>`_ if you wish to use a different
set of theoretical isochrones.

The isochrones must be downloaded with the package `ezPadova-2`_.
This code takes care of downloading the isochrones for a given range of
metallicities, storing them in files named following the proper
naming convention, and place them inside a folder also with the correct name.

This way, once this code finishes you can just cut the generated folder and
paste it inside the ``isochrones/`` folder in **ASteCA**.


.. _CMD service: http://stev.oapd.inaf.it/cgi-bin/cmd
.. _Girardi et al. 2002: http://www.aanda.org/articles/aa/abs/2002/31/aah3268/aah3268.html
.. _ezPadova-2: https://github.com/asteca/ezpadova-2
.. [#] Fork of original ezpadova code by Morgan Fouesneau (https://github.com/mfouesneau/ezpadova).