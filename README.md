# Air-Pollution-Traffic-Accident-Risk-Modeling-Bayesian-Hierarchical-Negative-Binomial-Analysis-

# Executive Summary 
This project investigates the relationship between short-term PM2.5 exposure and traffic accident counts across New York City boroughs using a Bayesian hierarchical Negative Binomial model.

# Unlike traditional Poisson regression, this approach:
Accounts for overdispersion in count data
Models borough-level heterogeneity via hierarchical priors
Quantifies full posterior uncertainty
Produces probabilistic risk estimates instead of point estimates
The result is a statistically rigorous, uncertainty-aware framework for estimating the effects of environmental risks on public safety outcomes.

# Business / Policy Motivation

Traffic accidents are influenced by environmental, behavioral, and structural factors. Air pollution may impair visibility, cognition, and driver response time.

# Key questions:
# Does short-term PM2.5 exposure increase accident risk?
Is the effect consistent across boroughs?
How uncertain are the estimates?

# This framework enables:
Risk-aware urban planning
Evidence-based environmental policy evaluation
Probabilistic forecasting under pollution spikes

# Data
Time Period: 2015–2023
Granularity: Borough-Day level

# Sources
NYC Motor Vehicle Collision Records
NYC PM2.5 Air Quality Data

# Processing
Aggregated accident counts per borough-day
Generated 1-day lag PM2.5 exposure variable
Standardized continuous predictors
Encoded borough as a hierarchical grouping factor
Validated missingness and temporal alignment

# Modeling Approach
# Why Negative Binomial?
Accident counts exhibit overdispersion:
# Var(yi​)>E(yi​)
# Poisson models underestimate variance and inflate significance.
# The Negative Binomial introduces an overdispersion parameter 𝜙 :
# Var(yi​)=μi​+ϕμi2

# Hierarchical Bayesian Specification :
# yi​∼NegBinomial(μi​,ϕ)
# log(μi​)=αb[i]​+β⋅PM25i
# αb∼N(μα,σα)
# 𝛽∼𝑁(0,1)
# ϕ∼HalfNormal(5)​

# Estimation
MCMC sampling via NUTS (No-U-Turn Sampler)
Posterior diagnostics: R-hat, ESS
Trace inspection for convergence
Posterior predictive checks

# Key Results
Positive posterior mean for PM2.5 coefficient (β)
Credible intervals quantify uncertainty of pollution impact
Borough-level baseline accident rates vary significantly
Negative Binomial successfully captures overdispersion

# Interpretation:

# A one standard deviation increase in PM2.5 is associated with a multiplicative change in expected accident counts of:

# exp (𝛽)exp(β)
(Insert your numerical estimate here)

# Model Validation
Posterior predictive checks show improved variance capture vs Poisson baseline
Convergence diagnostics indicate stable sampling
Sensitivity to priors assessed
Effect size remains directionally stable

# Tech Stack
Python
PyMC (Bayesian Modeling)
ArviZ (Diagnostics & Posterior Analysis)
Pandas / NumPy (Data Engineering)
Matplotlib (Visualization)​

	​

	​
