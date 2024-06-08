# logo detection 

This project is based on groundingDINO and clip model.

## :hammer_and_wrench: Install 

**Note:**

0. If you have a CUDA environment, please make sure the environment variable `CUDA_HOME` is set. It will be compiled under CPU-only mode if no CUDA available.

Please make sure following the installation steps strictly, otherwise the program may produce: 
```bash
NameError: name '_C' is not defined
```

If this happened, please reinstalled the groundingDINO by reclone the git and do all the installation steps again.

#### how to check cuda:
```bash
echo $CUDA_HOME
```
If it print nothing, then it means you haven't set up the path/

Run this so the environment variable will be set under current shell. 
```bash
export CUDA_HOME=/path/to/cuda-11.3
```

Notice the version of cuda should be aligned with your CUDA runtime, for there might exists multiple cuda at the same time. 

If you want to set the CUDA_HOME permanently, store it using:

```bash
echo 'export CUDA_HOME=/path/to/cuda' >> ~/.bashrc
```
after that, source the bashrc file and check CUDA_HOME:
```bash
source ~/.bashrc
echo $CUDA_HOME
```

In this example, /path/to/cuda-11.3 should be replaced with the path where your CUDA toolkit is installed. You can find this by typing **which nvcc** in your terminal:

For instance, 
if the output is /usr/local/cuda/bin/nvcc, then:
```bash
export CUDA_HOME=/usr/local/cuda
```
**Installation:**

1. Clone the code repository from GitHub.

```bash
git clone 
```

2. Change the current directory to the GroundingDINO folder.

```bash
cd logo_detection/
```

3. Install the required dependencies in the current directory.

```bash
pip install -e .
```

4. Install clip.

```bash
pip install git+https://github.com/openai/CLIP.git
```

5. Download pre-trained model weights.

```bash
mkdir weights
cd weights
# put groundingdino_swint_ogc.pth and best_model_vitb16.pt in this dir
cd ..
```

## :arrow_forward: Demo
Check your GPU ID (only if you're using a GPU)

```bash
nvidia-smi
```
Change CLIP_PTH and CLASS_JSON_PTH to the file best_model_vitb16.pt and class_indices.json in demo/inference_on_a_image.py.

Replace `{GPU ID}`, `image_you_want_to_detect.jpg` with appropriate values in the following command

```bash
CUDA_VISIBLE_DEVICES={GPU ID} python demo/inference_on_a_image.py  -i image_you_want_to_detect.jpg
 [--cpu-only] # open it for cpu mode
```

