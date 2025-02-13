# OOTDiffusion
This repository is the official implementation of OOTDiffusion

🤗 [Try out OOTDiffusion](https://huggingface.co/spaces/levihsu/OOTDiffusion)

(Thanks to [ZeroGPU](https://huggingface.co/zero-gpu-explorers) for providing A100 GPUs)

<!-- Or [try our own demo](https://ootd.ibot.cn/) on RTX 4090 GPUs -->

> **OOTDiffusion: Outfitting Fusion based Latent Diffusion for Controllable Virtual Try-on** [[arXiv paper](https://arxiv.org/abs/2403.01779)]<br>
> [Yuhao Xu](http://levihsu.github.io/), [Tao Gu](https://github.com/T-Gu), [Weifeng Chen](https://github.com/ShineChen1024), [Chengcai Chen](https://www.researchgate.net/profile/Chengcai-Chen)<br>
> Xiao-i Research


Our model checkpoints trained on [VITON-HD](https://github.com/shadow2496/VITON-HD) (half-body) and [Dress Code](https://github.com/aimagelab/dress-code) (full-body) have been released

* 🤗 [Hugging Face link](https://huggingface.co/levihsu/OOTDiffusion) for ***checkpoints*** (ootd, humanparsing, and openpose)
* 📢📢 We support ONNX for [humanparsing](https://github.com/GoGoDuck912/Self-Correction-Human-Parsing) now. Most environmental issues should have been addressed : )
* Please also download [clip-vit-large-patch14](https://huggingface.co/openai/clip-vit-large-patch14) into ***checkpoints*** folder
* We've only tested our code and models on Linux (Ubuntu 22.04)

![demo](images/demo.png)&nbsp;
![workflow](images/workflow.png)&nbsp;

## Installation
1. Clone the repository

```sh
git clone https://github.com/levihsu/OOTDiffusion
```

2. Create a conda environment and install the required packages

```sh
conda create -n ootd python==3.10
conda activate ootd
pip install torch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2
pip install -r requirements.txt
```

## Inference
1. Half-body model

```sh
cd OOTDiffusion/run
python run_ootd.py --model_path <model-image-path> --cloth_path <cloth-image-path> --scale 2.0 --sample 4
```

2. Full-body model 

> Garment category must be paired: 0 = upperbody; 1 = lowerbody; 2 = dress

```sh
cd OOTDiffusion/run
python run_ootd.py --model_path <model-image-path> --cloth_path <cloth-image-path> --model_type dc --category 2 --scale 2.0 --sample 4
```

## Citation
```
@article{xu2024ootdiffusion,
  title={OOTDiffusion: Outfitting Fusion based Latent Diffusion for Controllable Virtual Try-on},
  author={Xu, Yuhao and Gu, Tao and Chen, Weifeng and Chen, Chengcai},
  journal={arXiv preprint arXiv:2403.01779},
  year={2024}
}
```

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=levihsu/OOTDiffusion&type=Date)](https://star-history.com/#levihsu/OOTDiffusion&Date)

## TODO List
- [x] Paper
- [x] Gradio demo
- [x] Inference code
- [x] Model weights
- [ ] Training code

Step 1: Clone the repository
```sh
git clone https://github.com/levihsu/OOTDiffusion
```
Step 2: Navigate inside the cloned repository
```sh
cd OOTDiffusion
```
Step 3: Create virtual environment
```sh
conda create -n ootd python==3.10
```
Step 4: Activate virtual environment
```sh
conda activate ootd
```
Step 5: Install torch with CUDA
```sh
pip install torch==2.0.1+cu118 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```
Step 6: Install requirements
```sh
pip install -r requirements.txt
```
Step 7: Fix requirements
```sh
pip install pydantic==2.9.2 pydantic_core==2.23.4 fastapi==0.112.4
```
Step 8: Install LFS support for HuggingFace / GitHub
```sh
git lfs install
```
Step 9: Download checkpoints
```sh
GIT_CLONE_PROTECTION_ACTIVE=false git clone https://huggingface.co/openai/clip-vit-large-patch14 checkpoints/clip-vit-large-patch14
```
Step 10: Download some more checkpoints (move humanparsing, ootd, and openpose to checkpoints folder)
```sh
GIT_CLONE_PROTECTION_ACTIVE=false git clone https://huggingface.co/levihsu/OOTDiffusion
```
Step 11: Change working directory to `run` folder
```sh
cd run
```
Step 12: Run `gradio_ootd.py` file with python
```sh
python gradio_ootd.py
```
