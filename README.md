# Discrete-Event Simulation of a Ride-Sharing System

Built a discrete-event simulation of "BoxCar", a fictional ride-sharing platform, to evaluate rider service quality and driver earnings, and to test whether the company's original operating assumptions matched its real operational data.




## Approach

* Modelled the system as a discrete-event simulation, updating state only at driver/rider arrivals, trip completions, rider abandonments, and drivers going offline
* Validated the company's original stochastic assumptions (driver shift length, trip durations, rider/driver locations, arrival processes) against real operational data, and rejected several as unrepresentative (e.g. uniformity assumptions failing to hold, arrival processes not matching an exponential distribution as assumed)
* Recalibrated the simulation's stochastic inputs to the empirical distributions and re-ran the model, tracking key rider KPIs (abandon rate, waiting time) and driver KPIs (resting time, hourly earnings, Gini coefficient of earnings)
* Quantified the rider-vs-driver trade-off directly by sweeping two policy levers — fixed shift length (4-8 hours) and a hard cap on active drivers (10-45) — showing that improving rider service always came at the cost of driver earnings and idle time
* Designed and implemented a dynamic surge pricing mechanism (raising fares and driver inter-arrival rate under high demand, throttling it back above a driver-count threshold) that resolved the trade-off better than any static parameter setting
* Reported all KPIs with 95% confidence and prediction intervals across 100 simulation replications, rather than single point estimates

---

## Repository

```
src/     - simulation engine, KPI evaluation, and surge pricing model (notebooks + .py modules)

```

src:

1. `sim.py`
   - Core discrete-event simulation engine using the company's original (unvalidated) stochastic assumptions: driver/rider arrivals, matching, trip completion, and abandonment logic.

2. `rev_sim.py`
   - Revised simulation engine using stochastic inputs recalibrated to match empirical BoxCar data (e.g. truncated-normal driver locations instead of uniform).

3. `dat.py`
   - Computes real-world KPI values (abandon rate, wait times) from BoxCar's actual driver/rider data, used as a benchmark for the simulation.

4. `eval.py`
   - Plotting utilities for KPI distributions, overlaying confidence/prediction intervals and empirical comparison values.

5. `surgepricingfinal.py` / `runsurgepricingfinal.py`
   - Implements and runs the dynamic surge pricing mechanism: adjusts fares and driver inter-arrival rate in response to real-time driver availability.

6. `Simulation FINAL.ipynb` / `Revised_Simulation FINAL.ipynb`
   - Notebooks running the original and revised simulations respectively, generating the KPI tables and figures used in the report.

### Python Libraries Required

`numpy`, `scipy`, `pandas`, `matplotlib`, `seaborn`

---
**Generative AI use:** Used for resolving errors when coding and for grammar checks in the report write-up.
