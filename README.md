# TRELLIS.2-ROCm

## Info:
### This fork is no longer being developed. 
I recommend installing via https://github.com/Mateusz-Dera/ROCm-AI-Installer or directly using an alternative fork: https://github.com/hqnicolas/TRELLIS.2_rocm

This is a fork of TRELLIS.2 that enables running 3D model generation on AMD GPUs using ROCm.<br>
The script uses HIPIFY, and most libraries are patched on the fly; therefore, make sure you have the same versions of ROCm and HIPIFY installed.<br>
If you want a reliable test environment, it is recommended to use a Podman container (https://github.com/Mateusz-Dera/ROCm-AI-Installer
).

The script uses <b>nvdiffrast-hip</b> from https://github.com/CalebisGross/TRELLIS-AMD

The script applies patches dynamically:
- https://github.com/JeffreyXiang/nvdiffrec.git
- https://github.com/JeffreyXiang/CuMesh.git
- https://github.com/JeffreyXiang/FlexGEMM.git

Replaced:
- RMBG-2.0 by https://github.com/plemeri/InSPyReNet (transparent-background)

Original repository: https://github.com/microsoft/TRELLIS.2<br>
Original README: https://github.com/Mateusz-Dera/TRELLIS.2-ROCm/blob/main/ORGINAL_README.md

> [!Note]
> Core model generation is functional. Features such as the model preview or proper texturing are currently unavailable.

### Test platform:
|Name|Info|
|:---|:---|
|CPU|AMD Ryzen 9 9950X3D|
|GPU|AMD Radeon 7900XTX|
|RAM|64GB DDR5 6600MHz|
|Motherboard|Gigabyte X870 AORUS ELITE WIFI7 (BIOS F8)|
|OS|Debian 13.2|
|Kernel|6.12.57+deb13-amd64|

## Instalation:

1\. Install <b>uv</b>:
```bash
sudo apt -y install pipx
pipx install uv
```
2\. Install libjpeg-dev
```bash
sudo apt install -y libjpeg-dev
```
3\. Set the GPU architecture (If you are not using Podman):
```bash
export ROCM_PATH="/opt/rocm"
export HSA_OVERRIDE_GFX_VERSION="11.0.0" # RADEON 7900 XTX
export TARGET_GFX="gfx1100" # RADEON 7900 XTX
export PYTORCH_ROCM_ARCH="gfx1100" # RADEON 7900 XTX
```
3\. Run setup.sh:
```bash
bash ./setup.sh
```

## After installation:
1\. Activate venv<br>
2\. Go to https://huggingface.co/facebook/dinov3-vitl16-pretrain-lvd1689m<br>
3\. Click “Agree and access repository” to accept the license.<br>
4\. Activate your Hugging Face token in the terminal.<br>

## Run app:
```bash
source .venv/bin/activate
python ./app.py
```