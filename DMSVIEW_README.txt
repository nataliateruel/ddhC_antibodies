dms-view outputs
================

Pair-specific folders contain a dms_view/ directory with:
  - dmsview_<AB>_<ligand>.csv
  - dmsview_<AB>_<ligand>_structure.pdb
  - dmsview_<AB>_<ligand>_description.md

These three files form the safest dms-view package because dms-view accepts one structure at a time.

DMSVIEW_ALL_PAIRS.csv combines all eight AB-ligand conditions in one data table. It is formally compatible with the dms-view CSV schema, but a single dms-view session can display only one PDB structure. Therefore use the pair-specific packages when exact 3D mapping to the corresponding top-pose medoid matters.

Mutation metrics:
  mut_delta_CF_vs_WT = CF_mutant - CF_unmodified_WT
    positive = less favorable Surfaces interaction
  mut_binding_effect_vs_WT = -mut_delta_CF_vs_WT
    positive = more favorable Surfaces interaction
  mut_delta_CF_vs_self_model = CF_mutant - same-site self mutant
  site_modeling_floor_abs_CF = abs(CF_self_model - CF_unmodified_WT)
    practical position-specific modeling noise floor; not a formal CI
  mut_exceeds_site_modeling_floor = 1 if abs(delta_CF_vs_WT) > floor
