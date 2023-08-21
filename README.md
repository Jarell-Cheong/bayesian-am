# Bayesian Additive Models: Theory and Practice
- We survey and further clarify the theoretical underpinnings of the frequentist and Bayesian approaches to additive models.
- We create plots and replicate figures from key books and papers to allow for further understanding of additive model theory.
- We provide full derivations for numerous important theoretical results that are merely stated in key books and papers.
- We implement all variations of the additive model discussed on three benchmark datasets (a synthetic dataset of fifty points around the true function $y=-\sin^3(x)+\cos^3(x)$, the mcycle dataset, and a big multidimensional dataset measuring air quality in Beijing).
- We compare and make inferences about the relative performance for the different additive models considered when compared to less interpretable models (such as random forests) as well as more interpretable models (such as linear and generalized linear models).

# Models 
We have implemented nine models for our empirical analysis, namely:
-  Linear Model: we consider linear regression as a simple benchmark model, running the ordinary least squares method. Since all three datasets are nonlinear, we expect this model to perform poorly in comparison to the nonlinear, and whence more flexible, models in our list.
- Random Forest: we consider a random forest as a more sophisticated but less interpretable model for benchmarking purposes.
- Frequentist Additive Model: we consider a model using B-splines, which is a more general case of the cubic splines, under the penalized regression framework using second derivative smoothing as our penalty.
-  Squared Exponential Kernel Gaussian Process Prior: we consider a Gaussian process prior model introduced from Section 3 and Subsection 3.3 in our paper, using the squared exponential kernel function $k_{\text{SE}}(x,x')$. We use the eigendecomposition method detailed in Subsection 3.3 in the paper.
- Rational Quadratic Kernel Gaussian Process Prior: we consider a Gaussian process prior model introduced from Section 3 and Subsection 3.3 in our paper, using the rational quadratic kernel function $k_{\text{RQ}}(x,x')$. Similarly, we use the eigendecomposition method detailed in Subsection 3.3 in the paper.
- Ornstein-Uhlenbeck Kernel Gaussian Process Prior: we consider a Gaussian process prior model introduced from Section 3 and Subsection 3.3 in our paper, with the Ornstein-Uhlenbeck kernel function $k_{\text{OU}}(x,x')$. We use similar eigendecomposition methods as above.
- Difference Priors with Smooth Functions: we consider a model using B-splines and one-dimensional difference priors, as outlined in Section 4 and Subsection 4.1. Here, we only have the smoothness prior as our choice of difference prior.
- Difference Priors with Periodic Functions: we consider a model using B-splines and one-dimensional difference priors, as outlined in Section 4 and Subsection 4.1. Here, we will incorporate some periodicity into the difference prior, but in different ways. For the first two datasets, we consider both a smooth and a periodic component, while in the last dataset, we use only a periodic prior. 
- Difference Priors with Mixture of Functions: we consider a model using B-splines and one-dimensional difference priors, as outlined in Section 4 and Subsection 4.1. Here, we will incorporate a mixture of properties into the difference prior depending on the dataset. For the first two datasets, we consider a smooth plus periodic plus symmetric mixture, while in the last dataset, we only use a smooth and periodic mixture as symmetry is not a reasonable assumption.

# Datasets 
We have considered 3 datasets in our analysis, namely:
- Synthetic Functions: 50 datapoints sampled with scaled Normal noise around the true function $y=-\sin^3(x)+\cos^3(x)$, for $x\in [-\pi,\pi]$.
- mcycle Dataset: a dataset introduced by Silverman, where we examine the relationship between time and the acceleration of one's head in a simulated motorcycle accident. This is often used to test the robustness and efficacy of crash helmets.
- Beijing Air Quality Dataset: a dataset sourced from UCI Machine Learning Repository and first introduced in a 2017 paper by Zhang et al.. The dataset includes hourly air pollutants data from 12 nationally-controlled air quality sites. This data is collected by the Beijing Municipal Environmental Monitoring Center, and the meteorologial data in each air quality site is compared with the nearest weather station from the China Meteorological Administration. This data was collected from March 1, 2013 to February 28, 2017.

# Metrics
We applied four different statistics, namely the mean squared error (MSE), the root-mean-square error (RMSE), the mean absolute error (MAE), and the coefficient of determination ($R^2$) to measure performance after model fitting.

# Code 
- `paper_figures.ipynb`: Python notebook detailing code for all figures generated in the paper.
- `synthetic.ipynb`: Python notebook detailing fitting of a synthetic function $-\sin^3(x)+\cos^3(x)$.
- `synthetic.py`: contains helper functions for `synthetic.ipynb`.
- `mcycle.ipynb`: Python notebook detailing the fitting of the mcycle dataset.
- `mcycle.py`: contains helper functions for `mcycle.ipynb`.
- `beijing_EDA.ipynb`: Python notebook detailing an exploratory data analysis process on the Beijing Multi-Site Air-Quality dataset.
- `beijing.ipynb`: Python notebook detailing the fitting of the Beijing Multi-Site Air-Quality dataset.
- `utils.py`: contains functions for the interpolation of 1D and 2D matrices, as well as code for smooth functions for the fitting of difference prior AM models.

# Folders
- `data`: contains the original multivariate data from the Beijing Multi-Site Air-Quality Dataset, specifically the one collected at Aoti Zhongxin, from 2013-2017. 
- `paper_figures`: contains figures from `paper_figures.ipynb`.
- `EDA_figures`: contains figures from `beijing_EDA.ipynb`.
- `synthetic_figures`: contains figures from `synthetic.ipynb`.
- `mcycle_figures`: contains figures from `mcycle.ipynb`.
- `model_figures`: contains figures from `beijing.ipynb`.

# Installation
- Clone the GitHub file to your local desktop; in your terminal, run `git clone https://github.com/Jarell-Cheong/bayesian-am.git`.
- Check and install `requirements.txt`: `pip install -r requirements.txt`.
- Assuming you have Python and Conda configured as well as a text editor, run code files.

# Paper 
The paper can be accessed under the docs folder [here](docs/bayesian-am.pdf).
