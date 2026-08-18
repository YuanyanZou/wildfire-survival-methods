# Methodology Notes

## Why a landmark design?

The feature window and prediction window must be separated. Here, early fire characteristics are summarized over the first 5 hours, and survival follow-up begins at hour 5. A 12-hour-from-ignition prediction therefore corresponds to 7 hours of follow-up from the landmark. This makes the estimation conditional on remaining event-free through the landmark.

## Why exclude distance variables?

The event is defined by proximity to an evacuation zone. In the analytic data, early distance variables showed an unusually sharp split around that same threshold. Competition organizers stated that the early feature window and later label window were separated, so this repository does not label the issue as proven future-information leakage. The practical modeling concern remains: a near-deterministic proxy for the outcome definition would turn the task into a shortcut and prevent meaningful evaluation of other early-stage signals. The public models therefore exclude distance and distance-derived fields by construction.

## Why screen with Elastic Net Cox?

The candidate fire-dynamics variables are correlated. Elastic Net combines L1 and L2 penalties, allowing shrinkage and selection while tending to retain correlated groups more stably than a pure Lasso. The Cox model is used as a screening and diagnostic stage, not automatically accepted as the final inferential model.

## Why transition from Cox PH to AFT?

Schoenfeld-residual tests in the course analysis indicated proportional-hazards violations for four covariates. Stratification would remove coefficient estimates for the stratified variables, and multiple time-varying effects would be difficult to support with only 69 observed events. We also considered a discrete-time survival model. However, event times were concentrated early in follow-up while censoring extended much later, making the choice of time bins arbitrary and potentially unstable. Fine bins would yield sparse event counts, whereas coarse bins would lose timing information. 

An AFT model does not require proportional hazards and expresses covariate associations as acceleration or deceleration of survival time, which is interpretable for movement toward an evacuation zone.

The course report compared several parametric distributions and selected a log-logistic baseline by AIC and BIC.

## Why keep RSF as a sensitivity analysis?

RSF can capture nonlinearities and interactions without proportional-hazards or parametric survival-time assumptions. In this small dataset, the expanded and reduced RSF models had nearly identical mean cross-validated C-index, while their full-sample-to-CV gaps were larger than the AFT model's. This supports using RSF as a benchmark and diagnostic rather than treating a small apparent performance gain as decisive.

Exploratory partial-dependence plots and spline-based AFT specifications were also examined for nonlinear structure. Neither provided strong evidence that additional functional complexity materially improved internal model performance, so the simpler AFT specification was retained.