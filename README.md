# Install CUDA, cuDNN and PyTorch on a Linux Machine
This is a step-by-step guide to install CUDA and cuDNN on a Linux machine.

### Before we're beginning
- Check the system requirements: Before installing CUDA and cuDNN, you should check the system requirements to ensure that your machine meets the hardware and software specifications. The specific requirements may vary depending on the version of CUDA and cuDNN that you want to install, as well as your Linux distribution. You can check the system requirements on the NVIDIA website.

    ### To know what your operating system is in Linux, you can use the uname command. Here are the steps to take:
    Open a terminal window.

- Type the following command and press enter:
  ```
   uname -a
   ```
  This command will output a line of text that includes various details about your Linux system, such as the kernel version, machine hardware name, and operating system name. The operating system name is typically listed as the second field, and is often either "Linux" or the name of a specific Linux distribution (e.g. "Ubuntu", "Debian", "CentOS", etc.).

    For example, a typical output might look something like this:
    ```commandline
    Linux my-computer 4.19.0-22-cloud-amd64 #1 SMP Debian 4.19.260-1 (2022-09-29) x86_64 GNU/Linux
    ```
    In this example, the operating system name is "Ubuntu".

- You can also use other commands like `lsb_release -a`, `cat /etc/*release*`, or `hostnamectl` to get more information about your Linux distribution and operating system version.

    ### To check if CUDA and cuDNN are installed on your Linux machine, you can use the following steps:
- Open a terminal window.
- To check if CUDA is installed, type the following command and press enter:
    ```commandline
    nvcc --version
    ```
    If you have CUDA installed, this command will output the version number of your CUDA installation. If you don't have CUDA installed, you will see an error message.
- To check if cuDNN is installed, you can check for the presence of the cuDNN library files in the CUDA installation directory. The cuDNN library files are typically located in the lib64/ directory within the CUDA installation directory.

    To check if the cuDNN library files are present, type the following command and press enter:
    ```
    ls /usr/local/cuda/lib64/libcudnn*
    ```
    If the cuDNN library files are present, you will see a list of the files with their version number. If the files are not present, you will see an error message. 
    ##### If both CUDA and cuDNN are installed and the cuDNN library files are present, it means that your system is set up to use CUDA and cuDNN. You can now use CUDA and cuDNN-enabled applications, such as deep learning frameworks that rely on these libraries, on your Linux machine.


## CUDA and cuDNN on a Linux machine
### CUDA
1. Download the CUDA installer: Go to the [NVIDIA CUDA website](https://developer.nvidia.com/cuda-downloads) and download the installer for your Linux distribution. You can download the installer from the CUDA Downloads page.
    - Example:
      ```
      Linux my-computer 4.19.0-22-cloud-amd64 #1 SMP Debian 4.19.260-1 (2022-09-29) x86_64 GNU/Linux
      ```
      - Operating System: Linux
      - Architecture: x86_64
      - Distribution: Debian
      - For Version use `cat /etc/debian_version` command
      - Installer Type: deb(local)
      
2. Run the CUDA installer: Once you have downloaded the CUDA installer, you can run it to install CUDA on your machine. The installation process may take some time, as it will download and install the necessary files and packages.
   - Example of installation instructions for my machine:
     ```
     wget https://developer.download.nvidia.com/compute/cuda/12.0.1/local_installers/cuda-repo-debian10-12-0-local_12.0.1-525.85.12-1_amd64.deb
     sudo dpkg -i cuda-repo-debian10-12-0-local_12.0.1-525.85.12-1_amd64.deb
     sudo cp /var/cuda-repo-debian10-12-0-local/cuda-*-keyring.gpg /usr/share/keyrings/
     sudo add-apt-repository contrib
     sudo apt-get update
     sudo apt-get -y install cuda
     ```
3. Set up the PATH variable: After installing CUDA, you need to set up the PATH variable so that your system can find the CUDA binaries. To do this, add the following line to your shell startup file (e.g. ~/.bashrc for Bash):
    ```commandline
    export PATH=/usr/local/cuda-<version>/bin${PATH:+:${PATH}}
    ```
    Replace <version> with the version number of CUDA that you have installed (e.g. 11.5).
4. Check it by `nvidia-smi` and look for your CUDA version.
### cuDNN
1. Download the cuDNN library: Go to the [NVIDIA cuDNN website](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html) and download the cuDNN library that corresponds to your version of CUDA. You will need to create an NVIDIA Developer account if you don't have one already.
2. Extract the cuDNN files: After downloading the cuDNN library, extract the files to a temporary directory using the following command:
    ```commandline
    tar -xzvf <path/to/cudnn.tgz>
    ```
3. Copy the cuDNN files: Once you have extracted the cuDNN files, you need to copy them to the CUDA installation directory. To do this, use the following commands:
    ```commandline
    sudo cp -P cuda/include/cudnn*.h /usr/local/cuda-<version>/include
    sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-<version>/lib64
    sudo chmod a+r /usr/local/cuda-<version>/include/cudnn*.h /usr/local/cuda-<version>/lib64/libcudnn*
    ```
   Replace <version> with the version number of CUDA that you have installed (e.g. 11.5).
4. Verify the installation: To verify that CUDA and cuDNN have been installed correctly, you can run a simple program that uses CUDA and cuDNN. You can find examples and tutorials on the NVIDIA website.

### PyTorch
1. Go to [PyTorch website](https://pytorch.org/get-started/locally/), select your preferences and run the installation command

### That's it! You should now have CUDA and cuDNN installed on your Linux machine. Note that the installation process may vary depending on your Linux distribution and the version of CUDA and cuDNN that you want to install. Be sure to consult the documentation and resources provided by NVIDIA for more information.
