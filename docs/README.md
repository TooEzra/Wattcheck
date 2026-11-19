# Wattcheck

Wattcheck is a multi-institution energy-audit decision-support app for schools, colleges, hospitals and offices. It turns a building's electricity bills and equipment list into clear answers: how much energy it uses, where the energy goes, what looks wrong, and what to fix first.

Each institution only ever sees its own data. The app runs as a React (Vite) + Chart.js front end with a Node/Express + MongoDB back end.

## App features

- **Multi-tenant institutions** with two roles: **Admin** (manage users, settings and delete data) and **Auditor** (create and edit audit data).
- **Buildings** with type, floor area and operating hours.
- **Monthly energy records** entered by hand or imported from a CSV (`month,kwh,cost`) with per-row validation.
- **Equipment inventory** across 15 categories, with a common-equipment catalog to pre-fill typical ratings.
- **Reconciliation** of billed consumption against the equipment inventory, with a 15% tolerance warning.
- **Audit findings** by area, with priority and an optional JPG/PNG photo.
- **Recommendations** from a measure library, with estimated cost, estimated saving and automatic simple payback.
- **Dashboard** with annual totals, EUI comparison, monthly trend and flagged unusual months.
- **Reports** per building, exportable to PDF or printed, plus **JSON/CSV export** of the institution's own data.

## What goes in

| Input | Fields |
|---|---|
| **Building** | name, type, floor area (m²), operating hours |
| **Energy records** | month (`YYYY-MM`), kWh, cost |
| **Equipment** | category, name, location, rating (W), quantity, hours/day, days/year, condition |
| **Findings** | area, problem, location/system, suggested improvement, priority, optional JPG/PNG photo |
| **Recommendations** | measure or title, estimated cost, estimated annual saving, status |
| **Institution settings** | name, currency, building limit |

## What comes out

| Output | Contents |
|---|---|
| **Analysis** | latest-12-month kWh and cost, cost per kWh, EUI (only when 12 months are present), flagged months, end-use shares, reconciliation gap |
| **Dashboard** | institution totals, per-building EUI comparison, monthly trend |
| **Recommendations** | estimated yearly saving and payback for each improvement |
| **Reports** | per-building audit report as PDF or print |
| **Export** | the institution's own data as JSON or CSV |

## Documentation

| Document | Read it for |
|---|---|
| [Features and user guide](FEATURES.md) | What users can do and who can do it |
| [Formula reference](FORMULAS.md) | Every calculation the engine uses |
| [Worked example](WORKED_EXAMPLE.md) | One building followed through all the steps with numbers |
| [Technical documentation](TECHNICAL.md) | Tech stack, architecture, data storage, security |
| [Setup guide](SETUP.md) | Installing, configuring and running the app |

## Good to know

- Savings and paybacks are **estimates**, not measured results.
- The app does not adjust for weather, forecast the future, or calculate carbon emissions.
- Data lives in **MongoDB** (not PostgreSQL); tenant isolation is enforced in code by `tenantDb`.
