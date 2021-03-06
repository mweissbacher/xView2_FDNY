# Damage assessment using pre and post orthoimagery

This package is uses pre and post incident imagery to infer building locations and infer damage on those locations.
The underlying model is based on fifth-place model from the DIU xView2 competition

---
To run the inference
`python handler.py --pre_directory <path to pre input> --post_directory <path to post input> --output_directory <path to output> --staging_directory <path to staging> --destination_crs EPSG:4326 --post_crs EPSG:26915 --model_weight_path weights/weight.pth --model_config_path configs/model.yaml --n_procs 10 --is_use_gpu --create_overlay_mosaic`--create_shapefile

# Arguments:
- --pre_directory: Directory housing pre-disaster imagery. This will be parsed recursively.
- --post_directory: Directory housing pre-disaster imagery. This will be parsed recursively.
- --staging_directory: Directory to create intermediate data.
- --output_directory: Directory to place output data.
- --model_weight_path: Path to model weights.
- --model_config_path: Path to model config.
- --is_use_gpu: Flag to use GPU (must be supported by CUDA ie. NVIDIA cards).
- --n_procs: Number of processors to use for parallel processing.
- --batch_size: Number of photos to include in each inference batch.
- --num_workers: Number of workers.
- --pre_crs: CRS of pre-incident imagery. Setting will only be honored if image has no CRS set in metadata.
- --post_crs: CRS of post-incident imagery. Setting will only be honored if image has no CRS set in metadata.
- --destination_crs: CRS for destination exports.
- --create_overlay_mosaic: Flag for creating overlay mosaic.
- --create_shapefile: Flag for creating shapefile from damage inference.

# Dependencies

Requires python 3.7 and GDAL, which can be installed with [anaconda](https://anaconda.org/conda-forge/gdal).

# FAQ
1. Why the fifth place model?
    While it's not the most accurate of the models submitted, the fifth-place model in far less compute intensive than the other models.
