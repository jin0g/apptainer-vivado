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

## You can also run on M1 Mac

1. Install Lima, XQuartz, and Rosetta
2. Create an Apptainer Container
```
$ limactl start template://apptainer --vm-type=vz --rosetta --memory=8 --disk=400
```
- Next, select Open an editor... and add/change the following settings:
```
mounts:
  - location: "~"
    writable: true  # append

# append to the end
ssh:
  forwardX11: true
  forwardX11Trusted: true
```
3. Build the Vivado/Vitis SIF Image
```
# Log into the VM
$ limactl shell apptainer

# Add Swap
$ sudo dd if=/dev/zero of=/tmp/swapfile bs=1M count=8192
$ sudo chmod 600 /tmp/swapfile
$ sudo mkswap /tmp/swapfile
$ sudo swapon /tmp/swapfile

# Prepare for SIF image build
$ git clone https://github.com/jin0g/singularity-xilinx-vivado-vitis
$ cd singularity-xilinx-vivado-vitis
$ mv /PATH/TO/FPGAs_AdaptiveSoCs_Unified_2023.2_1013_2256.tar.gz ./

# Build the SIF image
$ sudo apptainer build xilinx_2023.2.sif xilinx.def
```
4. Launch Vivado
```
$ apptainer exec xilinx_2023.2.sif vivado
```

