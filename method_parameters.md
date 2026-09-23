# PRACT Reproducibility Parameters

## Cohort and planning space

The NBH-STN-DBS cohort contained 20 cases with T1WI and T2WI, of which 15 had usable SWI. The 15-case SWI analysis cohort comprised 30 hemispheres and used a patient-specific T1WI planning grid with a voxel spacing of 1.0000 × 0.9375 × 0.9375 mm.

## Spatial mapping

PRACT used the patient-specific T1WI planning space as the unified anatomical reference. T2WI-derived subthalamic-nucleus and red-nucleus masks were mapped to the T1WI planning space, and SWI was mapped to the same planning grid when available.

Spatial mapping used the existing NIfTI affine/header geometry. Intensity images were resampled using linear interpolation, whereas binary masks were resampled using nearest-neighbour interpolation. Registration accuracy was not independently quantified in the present cohort.

## Safety thresholds

The baseline vessel, sulcus, and ventricle safety thresholds were 3.0, 2.0, and 2.0 mm, respectively.

## Uncertainty scenarios

For cases with vessel, sulcus, and ventricle information, the uncertainty set comprised 13 evaluation scenarios: one nominal scenario and 12 perturbed scenarios. One voxel corresponded to 1.0000 mm along voxel axis 0 and 0.9375 mm along voxel axes 1 and 2.

| Scenario | Operation | Magnitude |
|---|---|---:|
| nominal | Unperturbed masks and target | 0 |
| vessel_dilate_1voxel | Vessel boundary broadening | 1 voxel |
| sulcus_erode_1voxel | Sulcus-mask erosion | 1 voxel |
| sulcus_dilate_1voxel | Sulcus-mask dilation | 1 voxel |
| ventricle_erode_1voxel | Ventricle-mask erosion | 1 voxel |
| ventricle_dilate_1voxel | Ventricle-mask dilation | 1 voxel |
| combined_conservative_mask_dilation | Simultaneous dilation of all available risk structures | 1 voxel per mask |
| target_shift_x_plus_1voxel | Target shift along +voxel axis 0 | 1.0000 mm |
| target_shift_x_minus_1voxel | Target shift along −voxel axis 0 | 1.0000 mm |
| target_shift_y_plus_1voxel | Target shift along +voxel axis 1 | 0.9375 mm |
| target_shift_y_minus_1voxel | Target shift along −voxel axis 1 | 0.9375 mm |
| target_shift_z_plus_1voxel | Target shift along +voxel axis 2 | 0.9375 mm |
| target_shift_z_minus_1voxel | Target shift along −voxel axis 2 | 0.9375 mm |

The perturbation configuration included erosion and dilation of the sulcal and ventricular masks, one-voxel boundary broadening of the vascular risk regions, simultaneous dilation of all available risk structures, and six target-position shifts.

## Candidate trajectory generation

For each predefined STN target, candidate directions were sampled outward toward the cortical surface in the patient-specific T1WI planning space. Intersections with the cortical surface defined the initial cortical entry candidates.

Candidate trajectories were retained when they satisfied the predefined angular constraints of 10°–25° relative to the sagittal plane and 50°–65° relative to the axial plane. A coronal-suture-based entry-zone constraint retained cortical entry candidates located within 20 mm anterior to the estimated coronal-suture reference. Each retained cortical entry point was connected to the predefined STN target to form a straight-line candidate trajectory.

## Aggregate candidate statistics

The following aggregate results were obtained for the 15-case SWI analysis cohort under the baseline safety thresholds:

| Metric | Result |
|---|---:|
| Initial candidate trajectories | 15,000 |
| Nominal-feasible candidates | 8,131 |
| Robust-feasible candidates | 5,940 |
| Pareto non-dominated candidates | 241 |
| Candidates rejected after robust screening | 2,191 (26.9%) |
| Hemispheres retaining at least one robust-feasible trajectory | 30/30 |

## Runtime

- Optimization runtime: 1.033 ± 0.074 s per hemisphere.
- Total preprocessing runtime: 159.676 ± 14.246 s per case.

