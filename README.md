# Singularity for Xilinx Vivado / Vitis

## Verified Environment
- Host OS: Ubuntu Server 22.04
- Singularity-CE version 4.0.0-jammy
- Vivado ML Edition / Vitis Core Development Kit 2023.2
- Over 400GB free HDD space

## Preparation
- Download `FPGAs_AdaptiveSoCs_Unified_2023.2_1013_2256.tar.gz` from [download page](https://www.xilinx.com/support/download.html)
- Put it in the same directory

## Build
```bash
sudo singularity build xilinx_2023.2.sif xilinx.def
```

## Creating the Links
```bash
ln -s xilinx_2023.2.sif vivado
ln -s xilinx_2023.2.sif vitis
ln -s xilinx_2023.2.sif vitis_hls
```

## Running the Tools
```bash
./vivado
./vitis
./vitis_hls
```
