# Xilinx Vitis on Singularity

This repository provides practices for running Xilinx Vitis on Singularity.

## Verified Environment
- Host OS: Ubuntu22.04
- Singularity-CE version: 3.11.3-bionic
- Vitis: 2023.1
- Requires over 400GB of free HDD space

## Preparation
Please download `Xilinx_Unified_2023.1_0507_1903.tar.gz` from the Xilinx download page and place it in the same directory as this file.

## Build
To build the Singularity container, run the following command:

```bash
sudo singularity build vitis.sif vitis.def
```

## Launching Tools
You can start various tools by running the following commands:

```bash
singularity exec vitis.sif vivado
singularity exec vitis.sif vitis
singularity exec vitis.sif vitis_hls
```

Please ensure to replace the necessary file names, commands, or version details to accurately represent your project details.
