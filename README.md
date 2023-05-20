# agemo

[![PyPi Downloads](https://static.pepy.tech/personalized-badge/agemo?period=total&units=international_system&left_color=black&right_color=orange&left_text=Downloads)](https://pepy.tech/project/agemo) [![Anaconda-Server Badge](https://anaconda.org/conda-forge/agemo/badges/downloads.svg)](https://anaconda.org/conda-forge/agemo) ![License](https://img.shields.io/github/license/LohseLab/agemo) [![Documentation Status](https://readthedocs.org/projects/agemo/badge/?version=latest)](https://agemo.readthedocs.io/en/latest/?badge=latest)

Agemo is an open-source tool with a python API that allows users to generate the Laplace Transform of the coalescence time distribution of a sample with a given demographic history. 
In addition, agemo provides ways to efficiently query that distribution, by using the fact that its generating function can be represented most simply as a directed graph with all possible ancestral states of the sample as nodes. Past implementations have not made full use of this, relying on computer algebra systems instead of graph traversal to process these recursive expressions.

So far, agemo has been used to compute the probabilities of the joint site frequency spectrum for blocks of a given size, under models of isolation and migration. Calculating these probabilities requires repeated differentiation of the generating function (Lohse et al, 2011) which suffers from an explosion in the number of terms when implemented naively. Using a closed-form expression for the coefficients of a series expansion of the equations associated with each edge of the graph, we can efficiently propagate these coefficients through the graph avoiding redundant operations.
