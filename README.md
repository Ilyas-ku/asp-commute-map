# Commute to AS+P — reliability-adjusted transit isochrones

Interactive map: **https://ilyas-ku.github.io/asp-commute-map/**

How far can you live from Hedderichstraße 108–110, Frankfurt, and still get there
by public transport in 10–60 minutes on a weekday morning — and how much does that
area shrink once real delays and cancellations are taken into account?

- **Timetable:** GTFS for Rhein-Main (DELFI via gtfs.de), Tuesday 20 Oct 2026.
- **Delays:** my own collector of operators' GTFS-Realtime feed, weekday arrivals
  24 Sep – 16 Oct 2026, per stop, line and hour (median, 80th, 90th, 95th percentile,
  cancellation rate).
- **Routing:** reverse Connection Scan Algorithm (latest departure that still arrives
  by the deadline), walking 4.8 km/h on a 1.3× detour, ≥2 min per transfer.
- **Reliability levels:** every leg's arrival is pushed back by the delay quantile for
  that stop/line/hour plus the expected wait from cancellations; the next vehicle is
  assumed on time, so missed connections are part of the result.
- **Population:** Zensus 2022, 100 m grid.

`pipeline/` holds the scripts: `export_inputs.py` and `export_delays.py` run against
the collector's DuckDB, `build.py` computes the 65 scenarios into `data.json`.

Independent analysis, not affiliated with AS+P. Data: DELFI / gtfs.de (CC BY-SA 4.0),
Zensus 2022 (dl-de/by-2-0), © OpenStreetMap contributors, basemap © Esri.
