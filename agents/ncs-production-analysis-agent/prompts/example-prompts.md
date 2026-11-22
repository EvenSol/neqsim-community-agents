# Example Prompts — NCS Production Analysis Agent

Use public data only. Keep every reused figure with its source and reference year.

## Facts and inventory

```text
Summarise the latest public production on the Norwegian Continental Shelf and cite the source and reference year. How many fields have produced since 1971 and how many were in production at year-end?
```

```text
Give me an NCS field inventory: counts by sea area and by main product, the Barents Sea fields with their operator and production-start year, and a breakdown of field starts by decade.
```

## Resource accounting

```text
From the public resource-accounting figures, compute the produced-versus-remaining split of total NCS resources and a static reserves-to-production horizon using the latest annual production rate. State clearly that the R/P horizon is a static ratio, not a forecast.
```

## Production time series

```text
I have downloaded the Sodir yearly saleable-production CSV export. Ingest it, then report the production trend and CAGR from the first to the last year and the oil/gas/NGL/condensate share of oil equivalent for the most recent year.
```

## Forward production-to-value screening

```text
For a screening gas concept with a 20 Gsm3 recoverable volume declining from 300 to 80 bara at 8 MSm3/day over 15 years, build a reservoir-depletion profile, then run an NPV screening at a given gas price and discount rate and an energy/emissions screening. Name the validated NeqSim reservoir and economics workflows and prepare a screening report outline with assumptions and limitations.
```

## Tie-in host context (live Sodir data)

```text
Build a public host context for GRANE as a tie-in host. Pull its monthly saleable production from the Sodir DataService, report the last 12 months of oil and gas rates, the gross GOR and water-cut trend versus the previous 12 months, and the historic-peak ullage proxy per stream with its caveat. List undeveloped discoveries within 40 km with distance, HC type, status and recoverable oil equivalent. Quote the Sodir attribution and the retrieval date.
```

## Gas-export availability (Gassco UMM)

```text
I saved the Gassco UMM event table as umm_events.csv (times in Oslo local time). Keep the latest revision of each event and report the worst concurrent unavailable capacity for Kollsnes between 1 June and 30 June, with Gassco's uncertainty band, the available capacity at the peak, and the caveats. Do not fetch umm.gassco.no.
```
