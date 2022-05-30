Performance
===========

The code is optimized as far as my ability with ``python`` allows, and
hopefully more improvements in this area will be made in the future.

Nonetheless, there are a number of simple things the user can do to reduce
the time it takes **ASteCA** to process a cluster. Be aware that each one has
a cost though, mainly in that the final result will lack estimation of
certain parameters when some of these options are used.


**1-** The ``KDE p-value test`` can take up a substantial amount of time to
finish. If the cluster is a clear physical entity (i.e.: there are no
doubts about its existence as a true clustering of stars) then you can
safely skip this test.

**2-** If you already ran the ``Bayesian decontamination algorithm`` function
for a given cluster, and the center, radius and number of field regions
remains the same in the ``params_input.dat`` file, then you can use the
members file already generated to avoid running this function again.
To do this, in the ``Bayesian decontamination algorithm`` block select the
``read`` mode, then cut the ``XXX_memb.dat`` file generated (where ``XXX`` is
the name of the cluster; this file is saved along with the output images)
and paste it in the ``input/`` folder, next to the file that contains the photometric data of the cluster.

This way the code will not run this function again, instead it will read the
membership probability values already generated.

.. warning::
  This can only be done if the structural parameters (center and radius), the error rejection function used, and the number of field regions defined remains the same. Otherwise the values for the membership probabilities may change.

**3-** Lower the ``bootstrap`` number in the ``Best synthetic cluster fit``
function.
This option must be used with care and avoided whenever possible.
The bootstrap process assigns errors to the cluster's fundamental parameters
(metallicity, age, extinction, distance modulus, mass, binarity) found by the genetic algorithm.
If you disable this feature (by setting a value of 1 or 0) two things will
happen: first, parameters will have no errors estimation (which is not
good); second, the processing time of the GA will be *significantly reduced*.

The reduced processing time is due to the bootstrap function being the one
that takes up most of the running time in the code. This is so because, to obtain the errors estimates, it runs the GA again a number N of times.
For example, if the GA takes 1 hour to complete and the bootstrap function
was set to run ``N=10`` times, it will take the bootstrap function
approximately 10 hours to finish.

.. important::
  One of the biggest advantages of using **ASteCA** is the possibility of
  associating statistically meaningful errors to the cluster's parameters.
  A parameter that has an assigned value but no error estimate is
  *substantially* less valuable (and trustworthy) than one with a reasonable
  associated error.
