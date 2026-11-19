# Wattcheck: Worked Example

One building, followed through every stage of the analysis with real numbers. Formulas are defined in [FORMULAS.md](FORMULAS.md).

## The building

- Floor area: **1,800 m²**
- A complete 12-month record of bills
- 12-month electricity use: **252,000 kWh**
- 12-month electricity cost: **6,048,000**

## Step by step

### 1. How intense is the energy use?

$$
\text{EUI} = 252{,}000 / 1{,}800 = 140.0\ \mathrm{kWh/m^2/year}
$$

This lets the building be compared fairly with others of a different size.

### 2. What does a unit of energy cost?

$$
\text{Cost per kWh} = 6{,}048{,}000 / 252{,}000 = 24.00
$$

### 3. Where does the energy go?

The equipment inventory adds up to **120,000 kWh** a year. Lighting accounts for **60,000 kWh** of that:

$$
\text{Lighting share} = 60{,}000 / 120{,}000 = 50\%
$$

### 4. Does the inventory match the bills?

$$
\text{gapPct} = (252{,}000 - 120{,}000) / 252{,}000 \times 100 \approx 52.4\%
$$

This is above the 15% tolerance, so the app raises a warning. It is expected here: the inventory covers only part of the building's equipment, which is the cue to look for missing equipment.

### 5. What could we save with an LED retrofit?

The library says LED retrofits typically save **50%** of lighting energy and cost **250,000**.

$$
\text{baselineCost} = 6{,}048{,}000 \times 0.50 = 3{,}024{,}000
$$

$$
\text{estimatedAnnualSaving} = 3{,}024{,}000 \times 0.50 = 1{,}512{,}000
$$

### 6. How fast does it pay for itself?

$$
\text{payback} = 250{,}000 / 1{,}512{,}000 \approx 0.2\ \text{years}
$$

## Summary

| Result | Value |
|---|---|
| EUI | 140.0 kWh/m²/year |
| Cost per kWh | 24.00 |
| Lighting share of inventory | 50% |
| Reconciliation gap | 52.4% (warning) |
| LED retrofit saving | 1,512,000 per year (estimate) |
| LED retrofit payback | about 0.2 years |

All savings and paybacks are **estimates** based on typical figures, not verified measurements.
