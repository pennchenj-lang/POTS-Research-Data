# Original source retrieval and acquisition mapping

Official source: https://limu.ait.kyushu-u.ac.jp/~agri/komatsuna/
The original provider page lists the following multiview archives and documentation; none is mirrored in this release:

- Plant crops: https://limu.ait.kyushu-u.ac.jp/~agri/komatsuna/multi_plant.zip
- Provider instance labels: https://limu.ait.kyushu-u.ac.jp/~agri/komatsuna/multi_label.zip
- Full source frames: https://limu.ait.kyushu-u.ac.jp/~agri/komatsuna/multi_original.zip
- Calibration photographs: https://limu.ait.kyushu-u.ac.jp/~agri/komatsuna/multi_calibration.zip
- Provider documentation: https://limu.ait.kyushu-u.ac.jp/~agri/komatsuna/multi_readme.pdf

SOURCE_RETRIEVAL.csv supplies exact member names and original hashes for all 18 excluded crops/labels used by the three fitted cases. File naming is rgb or label, camera ID, plant ID, day ID, time ID. The selected plant IDs are 00, 01 and 02, day 009, time 00. Cameras 00 and 02 are training views; camera 01 is held out for projection evaluation. The target is leaf04 as recorded in the evaluation records. Provider labels can include petiole and do not define a physical lamina-area reference.

After obtaining the archives, locate each exact member named in SOURCE_RETRIEVAL.csv and check its SHA256. Keep acquisitions in a separate local external-data directory; the excluded_materials/ values in this release are identifiers, not supplied files. The data index must not be taken as a claim that the external images were redistributed. Automatic downloading is not performed by this package.

Crop/principal-point transformations are in inputs/real/cameras/p00_crop_mapping.json and additional_crop_mapping.json. They record original dimensions, crop origins, crop dimensions, full-frame/crop hashes and the no-resize checks. Camera calibration uses the documented 9 by 6 inner checkerboard corners, square side 1.0 in unknown physical checker-square units. Camera IDs and training/held-out calibration capture IDs are in calibration_protocol.json; fitted parameters and detection failures are in calibration_result.json. Full source frame filenames and hashes remain in the crop records. These facts do not bind metric scale.

Annotation B/T endpoints, Q paths and W strokes, source-coordinate domains, interpolation and review-state fields remain in the researcher records. The p03 rejected candidate remains in provenance and is not promoted to an analyzed plant. The provider's raster labels and label-derived mask PNGs are excluded; numerical projection scores are retained. The optional final-projection-mask PNG previews are also excluded.

Documentation attribution: Uchiyama et al., ICCVW 2017, DOI 10.1109/ICCVW.2017.239. No permission or availability change is asserted. The original provider controls access to these materials.
