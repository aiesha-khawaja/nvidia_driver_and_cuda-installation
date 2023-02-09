# nvidia_driver_and_cuda-installation
# Install Nvidia driver
got to the below link and in case error occurs do not use auto mode to install nvidia driver, use the reccomended version
https://www.linuxbabe.com/ubuntu/install-nvidia-driver-ubuntu

# Install CUDA:
 - Before installation find GPU Model by runing below command
```
sudo lshw -C display
```
- **output**
 ```
 *-display
       description: 3D controller
       product: GK208M [GeForce GT 740M]   # this is my card Name and GK208M is GPUs Model
       description: 3D controller
       product: GK208M [GeForce GT 740M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:49 memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128)

 ```
 
 - [Installation Guide Official Link](https://docs.nvidia.com/datacenter/tesla/tesla-installation-notes/index.html)
 -  Read Carefully and scroll down to Ubuntu section and follow th instruction for installation
 -  check nvidia driver version 
 -  ```
    nvidia-smi --query-gpu=driver_version --format=csv
    ```
  - **Display all OEM enablement packages which apply to this system**
  - ```
     sudo ubuntu-drivers list-oem 
    ```
   -  **View all hardware NVidia devices which need drivers and which packages**
   - ```
      sudo ubuntu-drivers devices
     ```
   - **output**
   
   - ```
     == /sys/devices/pci0000:00/0000:00:1c.4/0000:0a:00.0 ==
     modalias : pci:v000010DEd00001292sv0000103Csd000021DAbc03sc02i00
     vendor   : NVIDIA Corporation
     model    : GK208M [GeForce GT 740M]
     manual_install: True
     driver   : nvidia-driver-455 - third-party non-free
     driver   : nvidia-340 - distro non-free
     driver   : nvidia-driver-450-server - distro non-free
     driver   : nvidia-driver-460 - third-party non-free recommended
     driver   : nvidia-driver-418-server - distro non-free
     driver   : nvidia-driver-470-server - distro non-free
     driver   : nvidia-driver-390 - distro non-free
     driver   : xserver-xorg-video-nouveau - distro free builtin
     
     ```
   - **Let us install recommended driver automatically 460**
   - ```
     sudo ubuntu-drivers install
     ```
   
# Cuda installation with any specific version 
- Before installtion of Cuda check your GPU compute compitibility in below link 
- [**Check for GPU compatibility with Cuda**](https://developer.nvidia.com/cuda-gpus)
- **output**
![gpu_compat](https://user-images.githubusercontent.com/101540227/217725506-bb662988-e9ab-4a17-bdec-8923b75b57b5.png)

- The above picture show that My GPU has 8.6 compute compatability but we will deep dive and will see in below link.

- You can also make sure your GPU Architecture and GPU model and GPU name in below link
- [check for GPU ](https://en.wikipedia.org/wiki/CUDA)
- I found my GPU like this.
![gpu_det](https://user-images.githubusercontent.com/101540227/217724964-7b261f8f-8b4b-4c08-82c8-29d68ae9513e.png)

- So above i find out that my GPU has **8.6** compute compatibility and **Amoere** is architecture and GPU model is **GA106** 
- Now i will check CUDA version computability with GPU you ccan check in above link  
- **Output**

- Now we can install different compatible version of cuda  on MY GPU so will Cuda installation in below link
- **Before Further do we will also check Nvidia Display driver comaptibility with cuda version**
- [vistit her](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html) and check tabel 2 and tabel 3 after that if you fullfill the requirement then you may proceed.
- Old version visit to below link
 >  [cuda toolkit archives](https://developer.nvidia.com/cuda-toolkit-archive)
 - reboot after installation
 - Set up the development environment by modifying the PATH and LD_LIBRARY_PATH variables:[you can check here ](https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html#linux)
 ```
 export PATH=/usr/local/cuda-12.0/bin${PATH:+:${PATH}}
 ```
 ```
 export LD_LIBRARY_PATH=/usr/local/cuda-12.0/lib64\
                         ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
 ```
# Install CUDnn
- Follow the instruction :[you can check here ](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html)
