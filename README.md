# Selection-Dominance-Demography_simulator
This simulator models population genetics in sexual organisms in a non-equilibrium demography with arbitrary selection strength and dominance coefficients.  The simulator models an initial population that splits at some time into two sub-populations, one of which experiences a population bottleneck, and the other does not.  For representative puurposes we will refer to the bottleneckeded population as "European", and the non-bottlenecked population as "African", as the simulation is particularly useful for modeling the expected genetic differences between Africans and Europeans due to the Out of Africa event.  More generally, the simplest model of a square bottleneck is useful for the exploration of parameter space to understand the transient response of alleles under both selection and dominance to a non-equilibrium event such as a bottleneck.

Three basic demographies are modeled:  

1) A simple square bottleneck followed by subsequent re-expansion to the original equilibrium population size.
2) The Gravel, et al. (PNAS 2011) model of African and European demography as inferred from the 1000 Genomes Project (1KG) data.
3) The Tennessen, et al. (Science 2012) model of African and European demography as inferred from Exome Sequencing Project (ESP) data.

For computational speed, the simulator only keeps track of allele frequencies in a freely recombining diploid system, rather than containing full genome information.  We use an infinite sites model with a mutation rate of 2e-08 per generation per site.   Allele counts in the current generation are sampled based on the frequencies in the previous generation x_{old}, the selection coefficient s, and the dominance coefficient h.  We calculate the expected frequency x_{current} in the current generation as: 

x_{current} = \frac{(x_{old}^2 (1+s)+x_{old} (1-x_{old} )(1+s)h)}{(x_{old}^2 (1+s)+2x_{old} (1-x_{old} )(1+s)h+(1-x_{old} )^2 )}.

The simulator has arguments for mutation rate, U_{d}, adding new mutations at a probability of U_{d} per base pair per generation, selection coefficient s, dominance coefficient h, a burn-in of 300,000 generations where sampling occurs every 100 generations in speed-up mode, a transition to sampling every 1 generation at 1000 generations before time t=0.  




Citations:

Gravel S, et al. (2011)
Demographic history and rare allele sharing among human populations.
Proc. Natl. Acad. Sci. USA 108:11983--11988.

Tennessen JA, et al. (2012)
Evolution and functional impact of rare coding variation from deep sequencing of human exomes.
Science 337(6090):64--69.
