# VoxelSeq-CAD: Synthetic Dataset Generator for 3D Manufacturing Parts

This project features a Python-based FreeCAD macro designed to generate synthetic datasets of 3D manufacturing parts and their operation sequences. The tool automates the creation of voxelized representations of parts while tracking material removal at each machining step.

The generated dataset includes:

- **STL files** representing part geometries after each operation
- **HDF5 files** containing 3D voxel grids with delta volumes and operation labels

These datasets can be utilized for training machine learning models in manufacturing process automation. The generated samples adhere to random machining sequencing rules derived from a predefined set of literature-based guidelines. These rules focus on feature intersections, such as drilling, slant-face, and milling features, as well as volume removal.

Below is an example of a generated data sample, illustrating the voxelized representation of a 3D manufacturing part. This sample includes intersecting drill, mill, and slant-face features. The sequence of operations is generated according to the predefined rules that govern these intersections. In cases where no intersecting rules apply, the operation order is determined by the volume of material removed.

![Data Sample](teaser.png)

## Project Structure
```
/VoxelSeq-CAD/
│
├── generate_data.FCMacro         # Main FreeCAD macro for dataset generation
├── example_data.FCMacro          # Example FreeCAD macro file for testing
│
├── /bin/                         # Executable files (binvox should be placed here)
│   └── binvox                    # Binvox executable for voxelization
│
├── /data/                        # Folder for generated datasets
│   ├── /stl/                     # Folder for STL files (part shapes after each operation)
│   └── /h5/                      # Folder for HDF5 voxel data with delta volumes
│
├── /scripts/                     # Python scripts for dataset generation and utilities
│   ├── voxels.py                 # VoxelConverter class for voxel operations
│   ├── parts.py                  # PartGenerator class for generating CAD parts
│   ├── macro.py                  # Additional macro-related functionality
│   ├── data_utils.py             # Utility functions for dataset processing
│   └── __init__.py               # Makes the scripts directory a package
│
├── /notebooks/                   # Jupyter notebooks for data visualization and experiments
│   └── data_view.ipynb           # Notebook for visualizing voxel data
|
├── requirements.txt              # Required Python packages for FreeCAD environment
│
└── README.md                     # Project documentation
```

## Getting Started

### Requirements

To run the `generate_data.FCMacro`, you need:
- **FreeCAD** installed with Python support.
- **Binvox** for voxelization. The binvox executable is included in the `/bin/` folder; ensure it is added to your system's PATH.
- The packages listed in `requirements.txt` must be installed in the Python environment of the FreeCAD installation.

### Running the Macro

1. Open FreeCAD and load the `generate_data.FCMacro`.
2. Modify the sample size if necessary; it is set to generate **180,000 samples** by default.
3. Run the macro within FreeCAD's macro editor to start dataset generation. The generated datasets will be stored in the `/data/` folder, organized into `stl/` for part shapes and `h5/` for voxel data.

### Folder Descriptions

- **/bin/**: Contains the binvox executable required for voxelization.
- **/data/**: This folder will hold the generated datasets after the macro runs.
  - **/stl/**: Stores STL files of part geometries.
  - **/h5/**: Contains HDF5 files with voxel data and delta volumes.
- **/scripts/**: Python scripts utilized for dataset generation and related utilities.
- **/notebooks/**: Jupyter notebooks for data visualization and experimentation.

## Note

The dataset is not included in this repository; it will be generated when you run the macro.

## Contributing

Contributions to enhance the functionality or expand the dataset generation process are welcome. Please feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

