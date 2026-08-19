# Python port

Python implementation of the strategic sampling methods described in Faye et al., 2024, *Earth Science Informatics* — implemented in R at the root of this repository.

- `terrain_reader.py` — dependency-free reader for the project's multi-band, LZW-compressed GeoTIFF (`50m_rast_Attr2.tif`). No `rasterio`/`GDAL` required: implements just enough of the TIFF 6.0 spec (IFD parsing, TIFF-flavor LZW decompression) to recover the raw float32 bands.
- `sampling.py` — `kmeans_medoids()`, the Python counterpart of the R `scsCLARA`/`cdCLARA` functions: k-means clustering, then within each cluster the real observation closest to the centroid is kept as the sampled location (a medoid) instead of the centroid itself — `scikit-learn-extra` (a real CLARA/KMedoids implementation) isn't required.

Full write-up: [Méthodes d'échantillonnage stratégique](https://latsouckfaye.github.io/tutoriels/echantillonnage/echantillonnage.html).
