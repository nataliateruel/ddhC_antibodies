# Antibody–ligand computational DMS

Computational deep mutational scanning (DMS) of antibody–ligand binding states for **1G10** and **4E2** with **ddhC, ddhU, cytidine, and ddhCTP**.

For each antibody–ligand pair, the highest-occupancy binding state from the MD clustering analysis was selected. Its representative medoid structure was used to identify antibody residues with at least one heavy atom within **4.0 Å** of the ligand. Each selected position was modeled as all 20 canonical amino acids, including the WT self mutant, and scored with **Surfaces**.

The final dataset contains **55 interface positions and 1,100 modeled variants** across eight antibody–ligand pairs.

## Repository contents

Each pair-specific `dms_view/` directory contains the three files needed by dms-view:

```text
dmsview_<antibody>_<ligand>.csv
dmsview_<antibody>_<ligand>_structure.pdb
dmsview_<antibody>_<ligand>_description.md
```

The PDB is the **representative medoid of the highest-occupancy binding state** used for that DMS, with biological antibody chain IDs and residue numbering restored.

The repository also contains:

```text
DMS_ALL_PAIRS_Surfaces.csv   # complete Surfaces results for all 1,100 variants
DMSVIEW_ALL_PAIRS.csv        # consolidated dms-view-format table
```

For exact 3D mapping, use the **pair-specific CSV together with its matching pair-specific PDB**.

## Main DMS metrics

- `mut_delta_CF_vs_WT`: Surfaces CF(mutant) − CF(unmodified WT). Positive values indicate less favorable binding; negative values indicate more favorable binding.
- `mut_binding_effect_vs_WT`: `-mut_delta_CF_vs_WT`, provided as an intuitive visualization metric where positive values indicate more favorable binding.
- `site_modeling_floor_abs_CF`: absolute CF difference between the Modeller-generated WT self mutant and the unmodified WT structure. This is used as a **position-specific modeling-noise floor / practical confidence threshold**.
- `mut_exceeds_site_modeling_floor`: 1 when the absolute mutation effect exceeds the WT→self-model perturbation at that position.

The modeling floor is a practical structural-modeling threshold, not a formal statistical confidence interval.

## Open a pair in dms-view

1. Upload the pair-specific `.csv`, `_structure.pdb`, and `_description.md` files to this GitHub repository.
2. Open each file on GitHub and choose **Raw**.
3. Copy the resulting `raw.githubusercontent.com` URLs.
4. Open [dms-view](https://dms-view.github.io/).
5. Paste the raw CSV URL into the **data file** field, the raw PDB URL into the **protein structure** field, and the raw Markdown URL into the **description** field.
6. Use the site, mutation, and protein-structure panels to explore the DMS. Useful starting metrics are `site_modeling_floor_abs_CF` for the site panel and `mut_binding_effect_vs_WT` or `mut_delta_CF_vs_WT` for the mutation panel.
7. After loading and configuring a view, copy the dms-view page URL to save or share that exact interactive state.

## Systems

```text
1G10–ddhC
1G10–ddhU
1G10–cytidine
1G10–ddhCTP
4E2–ddhC
4E2–ddhU
4E2–cytidine
4E2–ddhCTP
```

## Interpretation

Surfaces interaction scores are interpreted such that **more negative CF values are more favorable**. Mutation effects should therefore be considered together with the site-specific WT self-modeling floor before small CF changes are treated as meaningful.
