# Computer Vision

## MMPose Installation Guide

### Prerequisites
- Ensure you have Python 3.7+ and CUDA 9.2+ installed. To check, run:
  ```bash
  nvcc --version
  python --version

### Step 1: Install Miniconda
- Download and install Miniconda from https://docs.anaconda.com/miniconda/.

### Step 2: Create and Set up Conda Environment
- Open the command prompt, create a new Conda environment, and make sure PyTorch is installed:
```bash
  conda create --name mmpose python=3.8 -y
  conda activate mmpose
  conda install pytorch torchvision -c pytorch
- Note: This approach assumes you have a GPU platform.

### Step 3: Install Microsoft C++ Build Tools
- Install "Microsoft C++ Build Tools" from the Visual Studio Installer.
- During installation, select "Desktop Development with C++" (this includes the necessary compiler).
