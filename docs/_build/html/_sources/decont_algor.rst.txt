.. _decont-algor:

Decontamination algorithm
=========================

.. todo::
   Not finished.

A correct determination of the most probable true cluster members, allows to
recover a much clearer picture of a cluster's photometric structure. It is also
essential to ensure a more accurate and all around better estimation of the
cluster's fundamental parameters.

Since it is not possible to *unequivocally* discriminate between true members
and field region stars from photometry alone (even when proper motions or
radial velocities are available), the decontamination algorithms (DA, also
membership probability assignment algorithms) in the literature usually give
each star in the cluster region a *probability of being a true member*.

The process by which these membership probabilities (MP) are assigned by the
code, is explained in detail in the article where **ASteCA** was introduced. The
algorithm is based basically on a Bayesian scheme, and the repeated estimation
of a 'clean' cluster region by means of a random removal of stars.

The first four binning schemes that can be used by the DA are taken from the
`astroML`_ package; the rest are well known rules:

* ``blocks``: `Bayesian Blocks`_.
* ``knuth``: `Knuth's rule`_.
* ``scott``: `Scott's rule`_.
* ``freedman``: `Freedman-Diaconis rule`_.
* ``sturges``: `Sturge's rule`_.
* ``sqrt``: 
* ``bb``: 

These same binning methods are made available to the Dolphin likelihood equation
in the *Best fit* block, see Sect. :ref:`sect-likelihood`.

Once the DA process has finished, every star inside the cluster region will
have a MP associated to it. These MPs are stored, along with the data on each
star in the cluster region, in a file named ``XXXX_memb.dat`` (where ``XXXX``
is the name of the analyzed cluster).

Reduced membership
------------------

After MPs have been assigned to all the stars within the cluster region,
what follows is the *selection criteria*, referred here as the "Reduced
membership" algorithm. This process determines which stars, among all those
located within the cluster region, will be used by the best fit
process (see Sect. :ref:`best-fit`).

Several options are available in **ASteCA**, associated to this function. These
options are handled by the ``Reduced membership`` block in the
``params_input.dat`` file.

* ``local``: combines the assigned MPs with a cell by cell removal of stars in
  the photometric diagram. The stars discarded are those with lower MPs and
  the number is equal to the excess of field stars present in each cell.
* ``n_memb``: use the N stars with the highest MPs, where N is the approximate
  number of members found via the cluster region vs field region star
  density comparison.
* ``mp_05``: selects only those stars with MP>=0.5, i.e.: stars with higher
  probability of being a cluster member than a field star.
* ``top_h``: selects the top half of all stars in the cluster region with the
  highest MPs.
* ``man``: the minimum probability value has to be set manually via
  the ``prob_min`` parameter (0, 1).
* ``mag``: switches the ``prob_min`` value to a ``mag_min`` value so the user
  can select a minimum magnitude to be used in the best fit function, instead
  of a minimum probability (the "minimum magnitude" value is the value of
  the dimmest star wished to be taken into account in the fitting process).
* ``skip``: use all stars in the cluster region.

.. _astroML: http://www.astroml.org/user_guide/density_estimation.html
.. _Bayesian Blocks: http://adsabs.harvard.edu/abs/2012arXiv1207.5578S
.. _Knuth's rule: http://adsabs.harvard.edu/abs/2006physics...5197K
.. _Scott's rule: http://biomet.oxfordjournals.org/content/66/3/605
.. _Freedman-Diaconis rule: http://www.springerlink.com/content/mp364022824748n3/
.. _Sturge's rule: http://www.jstor.org/stable/2965501
