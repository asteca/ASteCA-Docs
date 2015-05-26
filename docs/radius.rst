Cluster radius estimation
=========================

.. important::

  This section is outdated.

We begin by counting the number of RDP points that fall below a given maximum
tolerance interval above :math:`d_{field}`. When the number of these points
reaches a fixed value, :math:`n_{fixed}`, the point closest to
:math:`d_{field}` is stored as the most probable radius for this iteration.
This process is repeated increasing the tolerance around :math:`d_{field}`
which results in another probable radius being stored, not necessarily the
same found in the previous iteration.
The final estimation for :math:`r_{cl}` and its associated error comes from
averaging the set of radius values stored this way and taking its standard
deviation, respectively.
