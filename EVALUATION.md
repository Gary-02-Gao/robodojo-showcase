# Evaluation notes

[Overview](README.md) · [中文](README.zh-CN.md)

The data files report selected aggregate results from the completed November 2026 evaluation. The three stages answer separate questions and use different sets of layouts.

| Stage | Comparison | Design |
| --- | --- | --- |
| Formal baseline | Official π0 vs official π0.5 | 100 matched pairs, 20 pairs per task. Each of four tasks used 20 layouts. `cover_blocks` used five layouts repeated four times. |
| Development | B09 vs B12, both with π0.5 | Six layouts, three runs per layout and setup. `stack_bowls` used two layouts, and each other task used one. |
| Insertion pilot | Official π0.5 entry vs full B12 setup | Five layouts separate from both earlier batches, two repeats per layout and setup. All ten pairs were valid and complete, with zero retries. |

## Measurement

- **Success.** The simulator's official success check defines the outcome. Reaching the step limit with a failed check is a valid failure. The formal batch had 23 successes and 177 valid failures.
- **Task average.** The macro score gives each of the five tasks the same weight. In development, B09 completed 9/18 episodes successfully and B12 completed 8/18. Bowl stacking contributed six episodes per setup, so the pooled episode rates differ from the task averages.
- **Pairing.** Pairing matches layout and repeat ID. Some layouts were reused and service processes were shared within the formal batch. Treat the rates as descriptive for the evaluated layouts.
- **Pilot time.** Elapsed time starts at slot claim and ends after result review. It includes setup, execution and checks. Both pilot arms used the same official success rule and every episode reached 500 steps. The process and data transport differed between setups, so the timing comparison cannot isolate the effect of the action prefix.
- **Trajectory examples.** The three PNGs are simulated head-camera keyframes from development. The frame number and episode verdict refer to different units. A visible tilt or stable placement at one frame does not identify the exact predicate that determined the final verdict.

## Data dictionary

- [baseline.csv](data/baseline.csv) reports successes and valid episodes for each task and checkpoint. For each model, sum the successes to obtain the total over 100 episodes.
- [insertion-pilot.csv](data/insertion-pilot.csv) reports one row per layout and repeat. L01–L05 are display IDs. Success is 1 for pass and 0 for fail. The timing column is candidate B12 minus official, in seconds, over the claim-to-review window.

## Upstream versions

The formal baseline used the `arx_x5_sim` normalization assets with official RoboDojo joint checkpoints for π0 (training step 60000) and π0.5 (training step 59999). Both predicted up to 50 actions per inference call. The links point to the pinned benchmark and policy sources.

- [RoboDojo benchmark source](https://github.com/RoboDojo-Benchmark/RoboDojo/tree/f57e1633ffed59761bc8e568cfe7530c4b33381c)
- [XPolicyLab policy source](https://github.com/XPolicyLab/XPolicyLab/tree/5d0be1499634d3176258c8f2e31f5fe816497b0a)
