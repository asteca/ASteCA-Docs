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
membership probabilities files that end with a ``.memb.dat`` extension
(see XXX).

Once file(s) are in place and the ``params_input.dat`` file correctly
modified, the code can be executed with the command:

.. code-block:: bash

    $ python asteca.py

The ``CLUSTER.DAT`` file located in the ``input/`` folder contains
a synthetic open cluster generated via the `MASSCLEAN`_ package with the
following parameter values:

::

	M = 500 Mo
	z = 0.008
	log(age) = 8.0
	E(B-V) = 0.32 (Av = 1.0)
	(m-M)o = 12.32 (d = 3 kpc)

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

The isochrones can be downloaded manually or the package `ezPadova-2`_
can be used to automatically fetch them from the site. I describe both
possibilities below.

.. important::
   The current version of the code only recognizes a handful of photometric
   systems from those available at CMD, but an upcoming version (v0.2.0) will
   extend **ASteCA** to support all systems present in the CMD service.
   
   The systems supported are:

   * UBVRIJHK (cf. Maiz-Apellaniz 2006 + Bessell 1990)
   * 2MASS JHK_s
   * Washington CMT1T2
   * SDSS ugriz


Manual download
...............

They isochrone files must follow a naming convention and be stored in a
sub-folder inside the  ``isohrones/`` folder, also named according to a
convention that makes them readable and identifiable to the code.

The steps to manually download and store the files are:

1. The CMD isochrones files must be downloaded using the *Sequence of
isochrones of constant metallicity, Z* option. That is, isochrones of the same
metallicity must all be stored in the same file.

2. Each file must have the name of the metallicity that characterizes it.
For example, if you download a sequence of isochrones with metallicity
``z=0.019``, then the file should be called ``0.019.dat`` or ``0.0190.dat``
or ``0.019000.dat``, etc.

  This means that the file name must respect the decimal point in the
  metallicity value, and that the number of zeros at the end of the value in
  the name does not matter.
  This is necessary because the code takes the metallicity value directly from
  the file name (which I plan to `simplify`_ sometime).

3. The theoretical isochrones files must be stored in a sub-folder of
``isochrones/``, with the naming convention: ``parsecXX_YYY`` (currently only
PARSEC isochrones are supported). In this name, ``XX`` is 10, 11 or 12
depending on the version of PARSEC used (1.0, 1.1 or 1.2S, respectively) and
'YYYY' is ``ubvi``, ``wash`` or ``2MASS``, depending on the system chosen to
generate the isochrones.

  For example, if the PARSEC v1.2S tracks and the *UBVRIJHK (cf. Maiz-Apellaniz
  2006 + Bessell 1990)* system is selected, the name of the sub-folder where
  the isochrones must be stored would be: ``parsec12_ubvi``.


Automatic download
..................

To avoid having to download each isochrone file by hand, I've written the
ezPADOVA-2 code [#]_ which can downloaded from:

    https://github.com/Gabriel-p/ezpadova

This code takes care of downloading the isochrones for a given range of
metallicities, storing them in files named following the above mentioned
naming convention, and place them inside a folder also with the correct name.

This way, once this code finishes you can just cut the generated folder and
paste it inside the ``isochrones/`` folder in **ASteCA**.


.. _MASSCLEAN: http://www.physics.uc.edu/~bogdan/massclean/
.. _CMD service: http://stev.oapd.inaf.it/cgi-bin/cmd
.. _Girardi et al. 2002: http://www.aanda.org/articles/aa/abs/2002/31/aah3268/aah3268.html
.. _ezPadova-2: https://github.com/Gabriel-p/ezpadova
.. _simplify: https://github.com/asteca/asteca/issues/161
.. [#] Fork of original ezpadova code by Morgan Fouesneau (https://github.com/mfouesneau/ezpadova).