Genetic algorithm
=================

.. image:: _static/ga-tree.png

The implementation of the GA can be divided into several blocks composed of 
operators, as shown in Fig. \ref{fig:ga-tree}. The first step consists in 
drawing a random initial population, that is a set of $N_{pop}$ random models 
taken from $B$. This set is evaluated to obtain the $L_i$ likelihood for each 
$B_i$ model via Eq. \ref{eq:likelihood} and fed to the GA loop as the starting 
generation.
The \textit{selection} block (in gray) contains the selection operator that 
picks models to reproduce from the generation pool with a breeding probability 
given by their ranked fitness (the rank-based fitness function associates 
higher $L_i$ values with higher probabilities) and the encode operator which 
translates the parameter values that define each chosen model into a binary 
chromosome \citep{Wright_91}.
The \textit{breeding} block (in green) pairs chromosomes randomly and produces 
a new generation via the crossover and mutation operators that combine each 
pair of parent chromosomes into two (theoretically fitter) offsprings.
The \textit{evaluation} block (in red) is finally applied where each offspring 
chromosome is decoded into a $B_i$ model, the best solutions from the previous 
iteration added into this new generation by the elitism operator (to ensure the 
fittest chromosomes are not lost) and the evaluation operator which obtains the 
$L_i^{\ast}$ values associated with this generation.
Every generation produces a ``best solution'' or fittest chromosome/model; we 
count the number of times this solution remains unchanged throughout 
generations and store it as $N_{bs}$. If $N_{bs}$ reaches a fixed value 
$N_{ei}$, the extinction/immigration operator is applied 
\citep{Leehter_Yao_Sethares_1994}. This operator prevents the GA from getting 
stuck in a local minima by discarding every chromosome but the fittest one 
(extinction) and introducing $N_{pop}-1$ new random chromosomes into the 
generation pool (immigration); the number of times this operator is run 
consecutively is stored in $N_{ct}^{ei}$.
An \textit{exit switch} is put in place to terminate the GA if no improvement
on the best solution found happened after $N_{es}$ consecutive applications
of the extinction/immigration operator, i.e.: when $N_{ct}^{ei}=N_{es}$,
in which case the GA is forced to halt.
The GA iterates for a maximum of $N_{gen}$ generations unless the exit switch 
forces a premature termination, in either case the result is the best fit model 
found for $A$, the observed SC, represented by $\mathbf{L}_A(z^{\star}, 
a^{\star}, d^{\star}, e^{\star})$.
Every variable involved in the GA process (e.g.: $N_{gen}$, $N_{pop}$, 
$N_{ei}$, etc.) can be modified via \texttt{ASteCA}'s input data file.
