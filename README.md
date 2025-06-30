# Instability of Metals with Respect to Strong Electron-Phonon Interaction

[![DOI](https://zenodo.org/badge/1009402009.svg)](https://doi.org/10.5281/zenodo.15751877)

## The version of Julia needed: 1.10.3
## To add Julia to Jupyter Notebook, add the package IJulia. 
## Additional packages needed to run each notebook are listed in the very first line of that notebook

### To generate Fig. 1 in the main text: use "Fig_1_Main_Text.ipynb"

We are solving the kinetic equation for a single phonon frequency. In this notebook, the step size of the discrete energy grid is denoted as $\epsilon$. The energy cutoff is denoted as $N\epsilon$; in other words, the quantity referred to as $L$ in the supplemental material is labeled $N$ here. Here we have $N\epsilon \gg \{T,T_{0}\}_\mathrm{max}$. 

Here we consider Einstein (dispersionless) phonons with frequency $\Omega = r\epsilon$. We keep $N/r = 10$ for all our simulations. Also, in our energy units $(g = \lambda\Omega^2 = 1)$, fixing $\Omega$ immediately fixes the dimensionless electron-phonon coupling constant $\lambda$. 

Initially, we consider the distribution to be the Fermi distribution with temperature $T = T_{0} + \Delta T$. The distribution functions then quickly (we consider $t_\mathrm{end} = 20.0$) relax to equilibrium Fermi distribution with temperature $T_{0}$ when $\lambda < 1.27$. If we choose $\Omega$ so that $\lambda > 1.27$, the distribution function show unstable behavior --- see Fig. 1 of the main text.

The data to generate Fig. 1(a) is found in the folder "Data_Fig_1_Main_Text/Unstable". The data to generate Fig. 1(b) is found in the folder "Data_Fig_1_Main_Text/Stable" 

### To generate Fig. 2 in the main text and Fig. 1 in the supplementary material: use "Lin_Analysis_Multiple_Phonons.ipynb"

### To generate Fig. 2 in the supplementary material: use "Omega_Critical_Plot.ipynb"
