Genetic algorithm
=================

The implementation of the GA can be divided into several blocks composed of
operators, as shown in :numref:`fig-ga-tree`.

.. _fig-ga-tree:

.. figure:: _static/ga-tree.png
   :align: center

   Genetic algorithm work tree.

The first step consists in drawing a random initial population, that is a set of
:math:`N_{pop}` random models taken from :math:`B`. This set is evaluated to
obtain the :math:`L_i` likelihood for each :math:`B_i` model via Eq. ?? and fed
to the GA loop as the starting generation.

The *selection* block (in gray) contains the selection operator that picks
models to reproduce from the generation pool with a breeding probability given
by their ranked fitness (the rank-based fitness function associates higher
:math:`L_i` values with higher probabilities) and the encode operator which
translates the parameter values that define each chosen model into a binary
chromosome .

The *breeding* block (in green) pairs chromosomes randomly and produces a new
generation via the crossover and mutation operators that combine each pair of
parent chromosomes into two (theoretically fitter) offsprings. 

The *evaluation* block (in red) is finally applied where each offspring
chromosome is decoded into a :math:`B_i` model, the best solutions from the
previous iteration added into this new generation by the elitism operator (to
ensure the fittest chromosomes are not lost) and the evaluation operator which
obtains the :math:`L_i^{\ast}` values associated with this generation. Every
generation produces a “best solution” or fittest chromosome/model; we count the
number of times this solution remains unchanged throughout generations and store
it as :math:`N_{bs}`. If :math:`N_{bs}` reaches a fixed value :math:`N_{ei}`,
the extinction/immigration operator is applied . This operator prevents the GA
from getting stuck in a local minima by discarding every chromosome but the
fittest one (extinction) and introducing :math:`N_{pop}-1` new random
chromosomes into the generation pool (immigration); the number of times this
operator is run consecutively is stored in :math:`N_{ct}^{ei}`.

An *exit switch* is put in place to terminate the GA if no improvement on the
best solution found happened after :math:`N_{es}` consecutive applications of
the extinction/immigration operator, i.e.: when :math:`N_{ct}^{ei}=N_{es}`, in
which case the GA is forced to halt.

The GA iterates for a maximum of :math:`N_{gen}` generations unless the exit
switch forces a premature termination, in either case the result is the best fit
model found for :math:`A`, the observed SC, represented by
:math:`\mathbf{L}_A(z^{\star},  a^{\star}, d^{\star}, e^{\star})`. Every
variable involved in the GA process (e.g.: :math:`N_{gen}`, :math:`N_{pop}`,
:math:`N_{ei}`, etc.) can be modified via **ASteCA**'s input data file.
