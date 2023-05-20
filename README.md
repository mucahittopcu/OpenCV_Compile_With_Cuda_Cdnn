# OpenCV Compile With CUDA and CUDNN

nvidia rtx 2060 
- nvidia driver metapackage 530

```sh
lspci | grep -i nvidia
sudo apt-get install linux-headers-$(uname -r)
sudo apt install build-essential
gcc --version
nvidia-smi
```
## CUDA Installation
[Source](https://developer.nvidia.com/cuda-downloads)
```sh
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/12.1.1/local_installers/cuda-repo-ubuntu2004-12-1-local_12.1.1-530.30.02-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2004-12-1-local_12.1.1-530.30.02-1_amd64.deb
sudo cp /var/cuda-repo-ubuntu2004-12-1-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda
```
Add a Path
```sh
gedit ~/.bashrc
```
Add the following lines to end of .bashrc
```sh
export PATH="/usr/local/cuda-12.1/bin:$PATH"
export LD_LIBRARY_PATH="/usr/local/cuda-12.1/lib64:$LD_LIBRARY_PATH"
```
Check CUDA
```sh
nvcc -V
```
## CDNN Installation
[Source](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html)
```sh
 sudo apt-get install zlib1g
 cd Downloads/
 sudo dpkg -i cudnn-local-repo-ubuntu2004-8.9.1.23_1.0-1_amd64.deb
 sudo cp /var/cudnn-local-repo-*/cudnn-local-*-keyring.gpg /usr/share/keyrings/
 sudo apt-get update
   
 sudo apt-get install libcudnn8=8.x.x.x-1+cudaX.Y bu örnek aşağıdaki gibi yazılacak
 sudo apt-get install libcudnn8=8.9.1.23-1+cuda12.1
   
 sudo apt-get install libcudnn8-dev=8.9.1.23-1+cuda12.1
 udo apt-get install libcudnn8-samples=8.9.1.23-1+cuda12.1
 ```
CDNN Test
```sh
cp -r /usr/src/cudnn_samples_v8/ $HOME
cd  $HOME/cudnn_samples_v8/mnistCUDNN
make clean && make
```
Note: If you have error, try the code below
```sh
sudo apt-get install libfreeimage3 libfreeimage-dev
```
```sh
cd  $HOME/cudnn_samples_v8/mnistCUDNN
make clean && make
./mnistCUDNN
```
Output: Test passed!
   
## OpenCV Compile
Open CV- Derleme <br>
- https://www.youtube.com/watch?v=whAFl-izD-4

Buran parametre al<br>
- https://gist.github.com/raulqf/f42c718a658cddc16f9df07ecc627be7
