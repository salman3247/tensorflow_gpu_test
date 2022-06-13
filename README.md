I successfully ran tensorflow on gpu. here is the procedure you should follow:

this procedure is completely based on tensorflow website:
https://www.tensorflow.org/install/pip
you can run main.py and see that in task manager in gpu part the cuda is started working

short description:
onda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0
python3 -m pip install tensorflow
# Verify install:
python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"




long descriptoin:
Step-by-step instructions

Note: Experimental support for WSL2 on Windows 10 19044 or higher with GPU access is now available. This corresponds to Windows 10 version 21H2, the November 2021 update. You can get the latest update from here: Download Windows 10. For instructions, please see NVIDIA’s setup docs for CUDA in WSL.
1. Install Microsoft Visual C++ Redistributable

Install the Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017, and 2019. Starting with the TensorFlow 2.1.0 version, the msvcp140_1.dll file is required from this package (which may not be provided from older redistributable packages). The redistributable comes with Visual Studio 2019 but can be installed separately:

    Go to the Microsoft Visual C++ downloads.
    Scroll down the page to the Visual Studio 2015, 2017 and 2019 section.
    Download and install the Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017 and 2019 for your platform.

Make sure long paths are enabled on Windows.
2. Install Miniconda

We recommend using Miniconda to create a separate environment to avoid changing any installed software in your system. This is also the easiest way to install the required software, especially for the GPU setup.

Download the Miniconda Windows Installer. Double-click the downloaded file and follow the instructions on the screen.
3. Create a conda environment

Create a new conda environment named tf with the following command.

conda create --name tf python=3.9

You can deactivate and activate it with the following commands.

conda deactivate
conda activate tf

Please make sure it is activated for the rest of the installation.
4. GPU setup

You can skip this section if you only run TensorFlow on CPU.

First, we need to install NVIDIA GPU driver if you have not.

Then, we install the CUDA, cuDNN with conda.

conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0

5. Install TensorFlow

TensorFlow requires a recent version of pip, so upgrade your pip installation to be sure you're running the latest version.

pip install --upgrade pip

Then, install TensorFlow with pip.
Note: Do not install with conda. It may not have the latest stable version. We recommend using pip since TensorFlow is only officially released to PyPI.

pip install tensorflow

6. Verify install

Verify the CPU setup:

python3 -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"

If a tensor is returned, you've installed TensorFlow successfully.

Verify the GPU setup:

python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"

If a list of GPU devices is returned, you've installed TensorFlow successfully.

