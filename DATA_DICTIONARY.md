# Data dictionary

## Objects and identifiers

case_id identifies a saved condition, not an independent biological specimen. Six synthetic conditions concern four targets: curved and twisted each occur under complementary visibility and a common gap; smooth_wave and smooth_twist each have a common gap. The real cases real_known_pilot, real_p01 and real_p02 correspond to p00, p01 and p02, one leaf per plant. target_id/plant_id/leaf_id, source case identifiers and timestamps retain their original meanings. Case p03 is a retained input rejection, not a fitted fourth plant.

method is POTS33 or symmetric24. level is 0 or 2 for the saved meshes. L2 shares the same piecewise-planar surface as L0. A method, mesh level, view, condition or table row must not be counted as an additional independent plant.

## Quantities and units

| Field/value | Meaning | Unit or rule |
| --- | --- | --- |
| lamina_area / Area | Sum of one selected lamina-side triangle areas, excluding petiole, reverse side and walls | model units squared (u²), unless an applicable physical scale is explicitly supplied |
| midrib_arc_length / Arc | Ordered B-to-T midrib polyline arc length in the acquisition state | model units (u) |
| half_arc_section_chord_width / Chord | Chord between exactly two boundary intersections at half cumulative midrib arc, normal to the local tangent/bisector | model units (u); not maximum leaf width |
| estimate_model, model_value, POTS33_value, symmetric24_value | Saved model-derived quantity | u² for area; u for lengths |
| reference_model, reference_value | Frozen evaluation-only numerical target quantity | same synthetic model units |
| estimate_physical, physical_value | Physical-unit estimate only where scale is applicable | unavailable for the three real leaves |
| scale_status, physical_reference_status | Declared scale/reference eligibility | preserve unknown/missing status; these are not zeros |
| signed_error_model / signed_error | estimate minus reference | same unit as the quantity |
| absolute_error_model / absolute_error | absolute signed difference | same unit as the quantity |
| signed_percent_error | 100 × (estimate − reference) / reference | percent; requires nonzero eligible numerical reference |
| absolute_percent_error, ARE_percent | 100 × absolute difference / absolute reference | percent |
| signed_bias_target_equal | Signed difference averaged across conditions within each target, then equally across targets | u² or u |
| MAE_target_equal | Mean absolute difference with the stated target/condition weighting | u² or u |
| RMSE_target_equal | Square root of the weighted mean squared difference | u² or u; averaging occurs before the square root |
| ARE_percent_target_equal | Weighted mean absolute relative difference | percent |
| nominal_target_weight, condition_weight_within_target, combined_weight | Explicit descriptive target/condition weights | dimensionless; read with scope |
| T/C, TC, target_count, condition_count | Target and condition denominators | counts, not biological sample multipliers |
| CI, p_value | Inferential summaries not estimated by this fixed-target comparison | missing/NA values remain unavailable |
| wall_seconds, seconds | Actual recorded timing for the indicated scope | seconds; nested timings are not additive |

## Quality, exclusions and missingness

scope, base_scope and subset distinguish all-output and post-hoc shared-quality-check summaries. included, excluded_both_methods, excluded_case_ids and corresponding target lists expose exclusions. A failed condition is excluded for both methods in paired quality-filtered comparisons and remains in all-output records.

triangle_intersection_pairs counts unordered triangle pairs with the saved floating-point diagnostic; common topological contact is excluded. degenerate_faces_at_normalized_area_1e_minus12, nonmanifold_edges, adjacent_edge_orientation_conflicts and degenerate_pairs_not_classified retain the diagnostic definitions. adjacent_normal_angle_max_deg is in degrees; an 85-degree warning is not a physical-accuracy acceptance threshold. own_saved_qc_pass and pair_both_saved_qc_pass concern the saved finite checks and do not establish anatomical correctness.

stage, failure_type, failure_reason and reason retain input rejection, geometry flags and unavailable reference states. Null, blank, NA, not_estimable, unknown and missing are distinct documented absence/status values; none denotes a measured zero. repeatability.csv is header-only. uncertainty_components.csv records unestimated components, not zero uncertainty. physical_accuracy_eligible/validated and anatomical_validity_validated must be interpreted as stored, never promoted by successful computation.

## Geometry and camera records

Frozen JSON mesh vertices contain saved three-dimensional coordinates; faces contain triangle vertex indices. level, coordinate_system, data_type, lineage and metadata preserve topology, organ definitions and parentage. Initial controls and fitted surfaces are kept separate. Synthetic reference JSON/NPZ files retain their original sampling; the analytic references are finite sampled surfaces, not exact continuous integrals.

The three prepared real records embed cameras, observations, initial_xyz, endpoint checks and training/evaluation assignments. K is the intrinsic matrix, R/t use the documented camera convention, and distortion plus crop/principal-point mappings are supplied in distorted_camera_contracts and camera provenance. The real unit unknown_checkerboard_square is not millimetres. Do not substitute unrelated archive cameras or independently rescale fitted leaves.

Observation records preserve B/T endpoint identity, ordered Q path samples, visible W strokes, coordinate domains, viewport transforms, confirmation/exclusion flags and raw-versus-interpolated source fields. Existing human, automatic, interpolated and review-state labels have not been promoted or replaced during packaging. The source export can contain p03 rejection records and evaluation-only material. Evaluation-only information must not enter fitting.

## Projection and software records

IoU is intersection divided by union of the retained projected and author instance masks. Pixel areas and boundary distances are image metrics; they are not physical leaf area. BT/Q/W counts distinguish raw visible samples and interpolated dense samples. RMS and boundary-distance fields use their recorded working/native pixel convention. Author instance labels may include petiole.

Synthetic single/batch reporting requests, reports and conditional propagation results are software fixtures. Attempt/accept/reject counts and flags are retained, and output draws are not independent biological observations. The nine planned_record tables are blank prospective forms.

## Formats and checksums

CSV_SCHEMAS.json lists every CSV header, row count and role without renaming scientific fields. JSON/JSONL records retain their source schemas. The file named frozen_protocol.yaml contains JSON syntax, which is also valid YAML. NPZ arrays are byte-identical; raster images are excluded from this public reviewer subset. Third-party PDF/HTML documents are excluded; their original source links are listed in SOURCE_RETRIEVAL.md. Embedded source hashes identify original archived bytes; DATA_INDEX.csv and FILE_MANIFEST.csv provide exported hashes separately. source_archive paths identify unbundled records and do not resolve inside this package.
