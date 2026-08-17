# Data Dictionary

## Benchmark task files

Each `data/benchmark_tasks/tasks_AGV##_T###.csv` contains **one task set per iteration**. The task locations are not duplicated across solution columns.

- `iteration_id`: 1--30, corresponding to the row in the original experiment file.
- `task_count`: number of task locations in the scenario.
- `task_locations`: JSON array of `[x,y]` grid coordinates. Coordinates are sorted for a stable, assignment-independent representation.

## Algorithm result files

Each result file contains one row for each nonblank candidate/Pareto solution in the corresponding original CSV.

- `iteration_id`: 1--30, preserving the original row number.
- `solution_id`: 1-based original column position. Blank cells from the original files are omitted.
- `agv_count`: number of AGVs in the scenario.
- `running_times_seconds`: JSON array with one running-time value per AGV.
- `energy_consumptions_joules`: JSON array with one energy-consumption value per AGV.
- `max_running_time_seconds`: maximum of the AGV running-time vector; this is the time objective used in the final two-objective analysis in the manuscript.
- `total_energy_consumption_joules`: sum of the AGV energy vector; this is the energy objective used in the final two-objective analysis in the manuscript.
- `source_auxiliary_value`: present only for ALNS source files because the original VNS-formatted cells contain one additional scalar. It is preserved for traceability and is not used to define the two reported objectives.

## Algorithm-name mapping

The cleaned repository uses manuscript-facing names:

- `results_VNS_improved_*` -> `ALNS`
- `Values_NSGA_improved_*` -> `NSGA-II`
- `Knee_*` -> `KnEA`
- `Values_Knee_samp1_*` -> `IKnEA`
- `Values_Knee_samp2_*` -> `ND-IKnEA`
