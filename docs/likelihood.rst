Best fit model
--------------

The best fit synthetic cluster (SYC) is obtained via one of two likelihood
equations.

The ``tolstoy`` method in the **Cluster parameters assignation** block (``BF`` ID
line) uses Eqs. 9, 10 & 11 defined in the original article describing
**ASteCA**.

The ``dolphin`` method uses Eq. 10 in the `Dolphin (2002)`_ article. This equation
compares the `Hess diagrams`_ of the observed SC vs the SYC, as shown in **Fig.**
:num:`fig-likel`.

.. _fig-likel:

.. figure:: _static/likelihood.png
   :align: center

   Observed and synthetic clusters (left) are compared via their
   respective Hess diagrams (center and right). The minimum :math:`-\ln(PLR)`
   value determines the best fit SYC.

When ``dolphin`` is used to obtain the best fit SYC, the membership probabilities
obtained by the decontamination algorithm (see Sect. :ref:`decont-algor`) are included
in the equation via the ``weights`` parameter in the `numpy.histogramdd`_ function.

.. _Dolphin (2002): http://adsabs.harvard.edu/abs/2002MNRAS.332...91D
.. _Hess diagrams: https://en.wikipedia.org/wiki/Hess_diagram
.. _numpy.histogramdd: http://docs.scipy.org/doc/numpy/reference/generated/numpy.histogramdd.html