<div align="center">

# ComfyUI Depth Anything TensorRT

[![python](https://img.shields.io/badge/python-3.10.12-green)](https://www.python.org/downloads/release/python-31012/)
[![cuda](https://img.shields.io/badge/cuda-12.3-green)](https://developer.nvidia.com/cuda-downloads)
[![trt](https://img.shields.io/badge/TRT-10.0-green)](https://developer.nvidia.com/tensorrt)
[![mit](https://img.shields.io/badge/license-MIT-blue)](https://github.com/spacewalk01/depth-anything-tensorrt/blob/main/LICENSE)

</div>

<p align="center">
  <img src="assets/demo.gif" />
</p>

This repo provides a ComfyUI Custom Node implementation of the [Depth-Anything-Tensorrt](https://github.com/spacewalk01/depth-anything-tensorrt) in Python for ultra fast depth map generation (30 fps, up to 5x faster)

## ⏱️ Performance

[Original Source](https://github.com/spacewalk01/depth-anything-tensorrt/blob/main/README.md#%EF%B8%8F-performance)
| Device | Model | Model Input (WxH) | Image Resolution (WxH)|Inference Time(ms)|
|:---------------:|:------------:|:------------:|:------------:|:------------:|
| RTX4090 | Depth-Anything-S |518x518 | 1280x720 | 3 |
| RTX4090 | Depth-Anything-B |518x518 | 1280x720 | 6 |
| RTX4090 | Depth-Anything-L |518x518 | 1280x720 | 12 |

## 🚀 Installation

Navigate to the ComfyUI `/custom_nodes` directory

```bash
git clone https://github.com/yuvraj108c/ComfyUI-Depth-Anything-Tensorrt.git
cd ./ComfyUI-Depth-Anything-Tensorrt
pip install -r requirements.txt
```

## 🛠️ Building Tensorrt Engine

1. Download one of the available [onnx models](https://huggingface.co/yuvraj108c/Depth-Anything-Onnx/tree/main) (e.g depth_anything_vitl14.onnx)
2. Edit paths inside `export_trt.py` accordingly and run it
3. Place the engine inside ComfyUI `/models/tensorrt/depth-anything` directory

## 🤖 Environment tested

- Ubuntu 22.04 LTS, Cuda 12.3, Tensorrt 10.0.1, Python 3.10, L40s GPU
- Windows (Not tested)

## 📝 Changelog

- 26/04/2024

  - Update to tensorrt 10.0.1
  - Massive code refactor, remove trtexec, remove pycuda, show engine building progress
  - Update and standardise engine directory for future tensorrt custom nodes suite

- 7/04/2024

  - Fix image resize bug during depth map post processing

- 30/03/2024

  - Fix CUDNN_STATUS_MAPPING_ERROR

- 27/03/2024

  - Major refactor and optimisation (remove subprocess)

## 👏 Credits

- [NVIDIA/Stable-Diffusion-WebUI-TensorRT](https://github.com/NVIDIA/Stable-Diffusion-WebUI-TensorRT)
- [spacewalk01/depth-anything-tensorrt](https://github.com/spacewalk01/depth-anything-tensorrt)
- [martenwikman/depth-anything-tensorrt-docker](https://github.com/martenwikman/depth-anything-tensorrt-docker)
