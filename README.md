# Discrete-Event Simulation of a Ride-Sharing System

Built a discrete-event simulation of "BoxCar", a fictional ride-sharing platform, to evaluate rider service quality and driver earnings, and to test whether the company's original operating assumptions matched its real operational data.



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


TO DO: 
WRITE REVISED SIMULATION FUNCTION
ADD DOCSTRINGS
FINAL CHECKS
FIX CODE ERRORS
