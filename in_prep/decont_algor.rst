Decontamination algorithm
=========================

A correct determination of the most probable true cluster members, allows to
recover a much clearer picture of a cluster's photometric structure. It is also
essential to ensure a more accurate and all around better estimation of the
cluster's fundamental parameters.

Since it is not possible to *unequivocally* discriminate between true members and
field region stars from photometry alone (even when proper motions or radial
velocities are available), the decontamination algorithms (DA, also membership
probability assignment algorithms) in the literature usually give each star in
the cluster region a *probability of being a true member*.

The process by which these membership probabilities (MP) are assigned by the
code, is explained in detail in the article where **ASteCA** was introduced. The
algorithm is based basically on a Bayesian scheme, and the repeated estimation
of a 'clean' cluster region by means of a random removal of stars.

Once the DA has finished assigning MPs to all stars within the cluster region,
what follows is the selection criteria; this is the ``Reduced membership`` block
in the ``params_input.dat`` file.


