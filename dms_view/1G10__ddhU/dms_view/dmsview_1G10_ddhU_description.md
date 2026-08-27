# Computational DMS: 1G10 / ddhU

Computational mutational scan of antibody residues having a heavy atom within 0.40 nm of the ligand in the medoid of the highest-occupancy binding state. All 20 canonical amino acids, including self mutants, were modeled with Modeller and evaluated with Surfaces.

## Metrics

- `delta_CF_vs_WT = CF_mutant - CF_unmodified_WT`; positive values indicate a less favorable calculated interaction.
- `binding_effect_vs_WT = -delta_CF_vs_WT`; positive values indicate a more favorable calculated interaction and are often more intuitive for visualization.
- `delta_CF_vs_self_model` compares each substitution with the same-site Modeller self mutant.
- `site` is the linear antibody sequence coordinate used on the dms-view x-axis: heavy-chain sequence first, followed by light-chain sequence. `label_site` retains biological labels such as H99 or L97.
- `site_modeling_floor_abs_CF = abs(CF_self_model - CF_WT)` is the position-specific modeling-noise floor. Effects smaller than or equal to this value are flagged as not exceeding the perturbation introduced by rebuilding the WT residue itself. This is a practical confidence threshold, not a statistical confidence interval.
