# 1. Computer Vision Tools

## 1.1. MMPose Installation Guide

### Prerequisites
- Ensure you have Python 3.7+ and CUDA 9.2+ installed. To check, run:
  ```bash
  nvcc --version
  python --version

### Step 1: Install Miniconda
- Download and install Miniconda from https://docs.anaconda.com/miniconda/.

### Step 2: Create Conda Environment with PyTorch
- Open the command prompt, create a new Conda environment, and make sure PyTorch is installed:
  ```bash
  conda create --name mmpose python=3.8 -y
  conda activate mmpose
  conda install pytorch torchvision -c pytorch
- Note: This approach assumes you have a GPU platform.

### Step 3: Install Microsoft C++ Build Tools
- Install "Microsoft C++ Build Tools" from the Visual Studio Installer at https://visualstudio.microsoft.com/de/visual-cpp-build-tools/.
- During installation, select "Desktop Development with C++" (this includes the necessary compiler).

### Step 4: Install MMEngine and MMCV
- Use OpenMMLab Installation Manager (MIM) to install MMEngine and MMCV:
  ```bash
  pip install -U openmim
  mim install mmengine
  mim install "mmcv>=2.0.1"

### Step 5: Install MMDetection
- Some MMPose scripts require MMDetection for human detection. Install using:
  ```bash
  mim install "mmdet>=3.1.0"

### Step 6: If Necessary, Resolve Dependency Issues
- If you encounter version incompatibility issues:
    1. Use the following command to list and inspect the versions of installed packages:
       ```bash
       pip list | grep mm
    2. Downgrade or upgrade dependencies as required. Example:
       ```bash
       pip uninstall mmcv
       mim install "mmcv<2.2.0,>=2.0.0rc4"
       mim install "mmdet>=3.0.0,<3.3.0"

### Step 7: Install MMPose
- Finally, install MMPose as Python library with:
  ```bash
  mim install "mmpose>=1.1.0"

### Step 8: Run an Inference Test
- Download a congif and checkpoint file to verify the installation:
  ```bash
  mim download mmpose --config td-hm_hrnet-w48_8xb32-210e_coco-256x192 --dest .
- Test the installation by applying inference on an example image in Python.
- Ensure to choose the correct Python interpreter linked to the MMPose environment created in Step 2, e.g., "3.8.20 (mmpose)":
  ```python
  from mmpose.apis import inference_topdown, init_model
  from mmpose.utils import register_all_modules
  
  register_all_modules()
  
  config_file = 'td-hm_hrnet-w48_8xb32-210e_coco-256x192.py'
  checkpoint_file = 'td-hm_hrnet-w48_8xb32-210e_coco-256x192-06e76c616_20220913.pth'
  model = init_model(config_file, checkpoint_file, device='cuda:0')  # or device='cpu'
  
  # Save an image with a person
  # Run the inference and print keypoints
  results = inference_topdown(model, 'demo.jpg')
  print(results)
- The code will estimate body keypoints and display the data.
- If this works, is is possible to continue with the keypoint exatraction script (i.e., estimate keypoints and save data as JSON files).
