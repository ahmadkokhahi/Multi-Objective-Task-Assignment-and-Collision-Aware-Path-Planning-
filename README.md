# RMFS Multi-Objective Computational Data

This repository contains the computational data associated with the manuscript **Integrated Multi-Objective Task Assignment and Collision-Aware Path Planning for Robotic Mobile Fulfillment Systems**.

## Contents

The experiments use nine scenario combinations formed by task counts of 36, 72, and 100 and AGV fleet sizes of 5, 8, and 10. For each scenario, data are provided for five algorithms: ALNS, NSGA-II, KnEA, IKnEA, and ND-IKnEA.

```text
data/
  benchmark_tasks/     # 9 files; one common task set per iteration, not repeated across solutions
  results/
    ALNS/              # 9 cleaned result files
    NSGA-II/           # 9 cleaned result files
    KnEA/              # 9 cleaned result files
    IKnEA/             # 9 cleaned result files
    ND-IKnEA/          # 9 cleaned result files
manifest.csv
DATA_DICTIONARY.md
```

## Benchmark task instances

Task locations were extracted from the original VNS/ALNS files. Within a given scenario and iteration, the same underlying task-location set appears in every solution column even though the assignment and ordering of those tasks among AGVs can differ. Therefore, the benchmark task files store the task locations **once per iteration** rather than repeating them for every solution.

The same corresponding task instances were used for the other algorithms in the comparison.

## Result data

The original nested cells were converted into consistent, machine-readable CSVs. Each nonblank solution now reports the complete per-AGV running-time and energy vectors, as well as the two derived objectives used in the manuscript: maximum AGV running time and total AGV energy consumption. Original row and column positions are preserved through `iteration_id` and `solution_id`.

See `DATA_DICTIONARY.md` for field definitions and `manifest.csv` for the file-to-scenario mapping.

## Notes on source files

The original ALNS files used an internal VNS-oriented filename and included task assignments in every solution cell. Those task assignments were removed from the cleaned result files. The underlying task-location set was extracted into `data/benchmark_tasks/`. An additional scalar present in the ALNS source cells is retained as `source_auxiliary_value` for traceability.
