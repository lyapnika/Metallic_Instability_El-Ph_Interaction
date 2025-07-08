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

### To generate Fig. 2 in the main text and Figs. 1 and 2 in the supplementary material: use "Fig_2_Main_Text.ipynb"

In this notebook, we solve the generalized eigenvalue equation that appears in the linear stability analysis of the kinetic equation with multiple phonon frequencies -- i.e., Eq. (14) of the main text. By doing this, we obtain the data for the $\gamma$ versus $\lambda$ plot in Fig. 2. In this notebook, we also include the codes and data that involve solving the generalized eigenvalue equation.  

The generalized eigenvalue problem in Julia is defined as: $\mathbb{A}\cdot\mathbf{x} = \sigma \mathbb{B}\cdot\mathbf{x}$, where $\mathbb{A}$ and $\mathbb{B}$ are two *real symmetric* matrices. Here $\mathbb{B}$ must be positive definite. Here $\sigma$ and $\mathbf{x}$ are *generalized eigenvalues* and *generalized eigenvectors* respectively. The command to find the generalized eigenvalues is: eigen(A, B).  

We recast the generalized eigenvalue problem (Eq. (13) in the main text) as $(\mathtt{A_{Total-Mat}}-\mathtt{B_{Total-Mat}}) \cdot \mathbf{\dot{\varphi}} = (\mathtt{C_{Total-Mat}}-\mathtt{D_{Total-Mat}}) \cdot \mathbf{\varphi}$. In Eqs. (13) and (14), $\mathtt{A_{Total-Mat}}-\mathtt{B_{Total-Mat}}$ and $\mathtt{C_{Total-Mat}}-\mathtt{D_{Total-Mat}}$ are denoted as $A$ and $- M$, respectively. Writing $\mathbf{\dot{\varphi}} \propto e^{\sigma t}$, we obtain $(\mathtt{A_{Total-Mat}}-\mathtt{B_{Total-Mat}}) \cdot \mathbf{\varphi} = (1/\sigma)(\mathtt{C_{Total-Mat}}-\mathtt{D_{Total-Mat}}) \cdot \mathbf{\varphi}$. We write the generalized eigenvalue problem in this way because $(\mathtt{C_{Total-Mat}}-\mathtt{D_{Total-Mat}})$ is positive definite. As a result, the generalized eigenvalues $\sigma$ obtained in this code is related to $\gamma$ in Fig. 2 of the main text as $\sigma = -\gamma$.

In this code, the energy $E$ is discretized in steps of $\epsilon \equiv \Delta E = 0.05$. The phonon frequencies are $\omega_{k} = (39+k)\epsilon$ with $\lambda_{k} = \lambda/21$, where $k = 1, 2, \ldots, 21$. We start at $\lambda = 0.9788$ and scan upto $\lambda = 1.9788$ in steps of $\Delta\lambda = 10^{-2}$. All the generalized eigenvalues as we scan over $\lambda$ are stored in "Data_Fig_2_Main_Text."

In the same notebook, we provide the code for obtaining the plots for the satable and unstable generalized eigenvectors (as shown in Fig. 1 in the supplemental material) for $\lambda = 5.00$ with the same $\omega_k$ and $\lambda_k$ as above.

We also provide a code to obtain the values of $\lambda_c$ for different values of temperature $T_0$ using the linear stability analysis delineated in the supplemental material. The data can be found in "Data_Fig_2_Supp_Material." Finally, we have also included the data and the code to reproduce Fig. 2 of the supplemantal material in this notebook.
