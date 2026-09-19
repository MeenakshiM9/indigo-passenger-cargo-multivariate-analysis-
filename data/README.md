# Dataset

## Dataset Description

This project uses monthly domestic operational statistics for IndiGo covering the period **2009–2025**.

The dataset contains operational, passenger, cargo, capacity, and utilization measures used for the multivariate analysis.

## Data Availability

The raw Excel dataset is **not included in this repository**.

The dataset was obtained from publicly available aviation statistics. The relevant source should be consulted and cited when reproducing the analysis.

## Primary Variables Used

The multivariate analysis uses the following six variables:

- `Aircraft_Departures`
- `Passengers_Carried`
- `Total_Cargo_Tonnes`
- `Available_Seat_Km`
- `Passenger_Load_Factor`
- `Weight_Load_Factor`

## Reproducing the Analysis

To reproduce the analysis:

1. Obtain the source dataset from the cited public aviation statistics source.
2. Place the Excel file in this `data/` directory.
3. Use the following filename:

```text
Indigoairlines_data_updated.xlsx
