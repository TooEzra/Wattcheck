# Wattcheck: Features and User Guide

What users can do in the app, and who can do it. For how the analysis works, see the [README](../README.md).

## Who uses it

Wattcheck serves several institutions (schools, colleges, hospitals, offices) in one app. Each institution only ever sees its own data.

| Role | Can do |
|---|---|
| **Admin** | Everything an Auditor can, plus manage users, change institution settings (name, currency, building limit) and delete data |
| **Auditor** | Create and edit audit data |

New auditors receive a one-time temporary password and must change it at first login. No e-mail is sent.

## The audit workflow

1. **Buildings**: register each building with its type, floor area and operating hours. Up to 100 per institution by default (admins can raise it to 1000).
2. **Energy records**: enter monthly kWh and cost by hand, or import a CSV (`month,kwh,cost`). Imports show a preview with per-row checks and duplicate-month detection, and only valid rows are saved once confirmed.
3. **Equipment inventory**: list the equipment in each building across 15 categories. A "Start from common equipment" picker (about 100 items with indicative wattages) pre-fills the form, and every value stays editable.
4. **Reconciliation**: compare what the bills say with what the equipment list adds up to, with a 15% tolerance warning.
5. **Audit findings**: record observations by area (lighting, AC and ventilation, motors and pumps, operating hours, practices) with a priority and an optional JPG/PNG photo (up to 5 MB).
6. **Recommendations**: start from the measure library, adjust cost and saving, and see the payback automatically. Institutions can add their own measures, visible only to them.
7. **Reports**: a per-building audit report with key figures, energy summary, EUI, monthly chart (unusual months highlighted), findings, recommendations and an editable conclusion. Export to PDF or print.

## Dashboard

An institution-wide overview:

- Annual consumption and cost
- EUI for each building
- Monthly trend chart
- EUI comparison between buildings
- Flagged unusual months

Charts include monthly consumption, trend, EUI comparison and end-use breakdown, each with an accessible data-table alternative.

## Data export

Download the institution's own data as JSON or CSV at any time.

## Trust and honesty built in

- Partial-year EUI is never shown.
- Every saving and payback is labelled an **estimate**.
- Comparing buildings of different types shows a fairness warning.
