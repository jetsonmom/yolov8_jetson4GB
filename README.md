
##### 참고 링크 https://docs.ultralytics.com/
##### 참고 링크 https://blog.naver.com/tory0405/223246391729  설치는 따라하니 잘 되지만 하드웨어 환경이 나랑 다른 듯하다. 코드를 따로 수정을 해주었다. 
##### https://medium.com/@deandu/how-to-use-the-yolov8-with-csi-camera-in-jetson-xavier-d2286a0f22bb
##### 1. Image Download
Jetson Nano Developer Kit SD Card Image, and note where it was saved on the computer.
######[Download the Jetson Nano Developer Kit SD Card Image]([https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write] URL "Download Jetson Nano Image")
######자신의 Linux가 몇 bit로 구성되어 있는지 확인하기 
``` bash
 $uname -m
```
!![Screenshot from 2024-03-08 18-53-36](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/917672ac-b7ff-45c5-8f8f-b27e57e2227e)

- 제가 사용하는 환경은 aarch64입니다. 따라서 설치하는 버전이 일반적인 것과 다르니 유의합시다
##### 2. cooling fan
```bash
git clone https://github.com/jetsonworld/jetson-fan-ctl.git
ls
cd jetson-fan-ctl
sudo sh install.sh
````
###### sudo sh install.sh 명령어는 리눅스나 유닉스 기반 시스템에서 사용되며, 주로 스크립트나 프로그램을 관리자 권한으로 설치하기 위해 사용됩니다. 이 명령어를 분해하여 그 의미를 자세히 설명하겠습니다:sudo: "Superuser Do"의 약자로, 다른 명령어를 슈퍼유저(루트 유저)의 권한으로 실행하게 해주는 프로그램입니다. 일반 사용자가 시스템에 영향을 미치는 작업(예: 소프트웨어 설치, 시스템 설정 변경 등)을 수행할 때 사용합니다.sh: "Shell"의 약자로, 쉘 스크립트를 해석하고 실행하는 명령어 해석기입니다.sh는 다양한 쉘 중 하나인 Bourne Shell을 가리키기도 하며, 리눅스나 유닉스 시스템에서 스크립트를 실행하는 데 사용됩니다.install.sh: install.sh는 일반적으로 설치 스크립트 파일의 이름입니다.이 스크립트는 소프트웨어나 프로그램을 시스템에 설치하기 위한 명령어들을 포함하고 있습니다.파일 이름의 .sh 확장자는 이 파일이 쉘 스크립트임을 나타냅니다.따라서, sudo sh install.sh 명령어는 install.sh라는 쉘 스크립트를 슈퍼유저 권한으로 실행하여, 스크립트에 포함된 지시에 따라 프로그램이나 소프트웨어를 설치하라는 의미입니다.이 명령어를 사용함으로써, 사용자는 스크립트에 정의된 대로 소프트웨어 설치 과정을 자동으로 진행할 수 있습니다.이 방법은 복잡한 설치 과정을 단순화하고, 설치 시 필요한 다양한 명령어를 일일이 입력할 필요 없이 소프트웨어를 쉽게 설치할 수 있게 해줍니다.
##### 3.  usb카메라 (usb카메라는 잘 된다. 하지만 csi카메라는 가상에서는 실행이 되질 않았다)

##### 4. swap memory
``` bash
free -m

```
##### 결과
!![Screenshot from 2024-03-08 17-55-55](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/e9c856b1-259d-434e-984b-7ea3b2759ec2)

``` bash
 free -m
 sudo chmod 600 /swapfile
 sudo mkswap /swapfile
 sudo mkswap /swapfile
```
##### 결과
!![Screenshot from 2024-03-08 17-58-15](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/e9a6381b-435b-48a4-8376-981448ab4293)



##### 5. 한글 폰트 설치

``` bash
sudo apt-get install language-pack-ko
sudo locale-gen ko_KR.UTF-8
sudo apt-get install fonts-nanum fonts-nanum-coding fonts-nanum-extra

````
##### 6. conda install

###### 참고 https://cyb.tw/docs/Tech/2020/9/18_Install-anaconda-on-Jetson-Nano.html#install-archiconda

``` bash
sudo apt-get update
````

```bash
wget --quiet -O archiconda.sh https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh && \
sh archiconda.sh -b -p $HOME/archiconda3 && \
rm archiconda.sh

````
###### archiconda3 폴더와 archiconda.sh가 생긴다. 그리고 archiconda.sh 삭제가 된다

```bash
 export PATH="/path/dli/anaconda3/bin:$PATH"
````
###### 위의 명령을 해줬는데 command not found가 뜨면 터미널을 껏다가 다시 열어서 하세요

###### 3.8을 설치하기 위해 챗에 물어보고 수정 된 명령들  설정 갱신에 필요하다고 한다. 그런데 이미 있다고 나온다

```bash
conda config --add channels gaiar
````
###### 결과 
###### Warning: 'gaiar' already in 'channels' list, moving to the top

``` bash
conda config --add channels conda-forge
````
###### 결과 Warning: 'gaiar' already in 'channels' list, moving to the top

``` bash
conda config --add channels c4aarch64
````
###### 결과 Warning: 'gaiar' already in 'channels' list, moving to the top

``` bash
conda update -n base --all
```
###### 위의 문장은 실행에 시간이 많이 걸림 시간이 좀 걸림

!![Screenshot from 2024-03-08 18-22-41](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/0ba64d82-7cff-482d-a3f9-3b525ea490e3)
!![Screenshot from 2024-03-08 18-24-19](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/d38a4f30-7826-4a26-a8a5-565c8c3707c5)

````
``` bash
conda install -y python=3.8 libiconv
````

``` bash
conda install -y conda-build
````
!![4](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/d5ffbf82-b689-4817-9e3d-726367259654)

``` bash
conda install -y anaconda-client
````
!![5](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/7a159b75-c993-4da4-8a71-fd21ee705a40)
``` bash
conda create -n py38 python=3.8
````

###### 참고 https://cyb.tw/docs/Tech/2020/9/18_Install-anaconda-o다
!![1](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/e27f1316-7bc5-47cb-88d9-0009a2274891)
!![2](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/8b656fe5-aaca-44e8-9c43-d1bc558a1fa7)

###### 가상환경 만들고 가상환경에서 실행한다.
``` bash
conda activate py38

````
###### 앞부분에 괄호가 생긴다.
###### (py38) dli@dli-desktop:~$ 
##### 6. python3 버전 확인하기

``` bash
python3 --version


##### 7. vi ~/.bashrc -> # 'activate a conda environment' 앞에 '#'을 써준다 저장한다. wq!

``` bash
vi ~/.bashrc
````
``` bash
source ~/.bashrc
````
``` bash
 conda activate py38
````
##### 8. gdown이 없다면 설치한다 가상에서
``` bash
 pip install -U pip wheel gdown
````

##### 9.   pytorch 1.11.0, torchvision 1.12.0  
!![1](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/20f7e0dd-50ce-47e3-8d39-1c67fe61a870)


```bash
gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM
````
```bash
gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV
````
```bash
sudo  mv torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl ~/Jetson-Nano2/V8
````

```bash
sudo  mv torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl ~/Jetson-Nano2/V8
````
###### 가상환경으로 간다.

```bash
 conda activate py38
````
```bash
cd Jetson-Nano2/V8
````
```bash
 pip install torch-*.whl torchvision-*.whl
````
###### 결과는 다음과 같다. Processing ./torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl
Requirement already satisfied: typing-extensions in /home/dli/archiconda3/envs/py38/lib/python3.8/site-packages (from torch==1.11.0a0+gitbc2c6ed) (4.4.0)
Installing collected packages: torch
Successfully installed torch-1.11.0a0+gitbc2c6ed

###### 10. 확인하기 (py38) dli@dli-desktop:~$ python3
 ```bash
python3
import torch
import torchvision
print("torch ver :",torch.__version__)
print("CUDA used:", torch_cuda.is_available())
````
###### 결과는 다음과 같다. Python 3.8.13 | packaged by conda-forge | (default, Mar 25 2022, 05:56:18) 
[GCC 10.3.0] on linux Type "help", "copyright", "credits" or "license" for more information. 
import torch
import torchvision 
print("torch ver :",torch.__version__) 
torch ver : 1.11.0a0+gitbc2c6ed
print("torchvision ver :",torchvision.__version__)
torchvision ver : 0.12.0a0+9b5a3fe
print("CUDA used:", torch_cuda.is_available())
CUDA used: True
quit()  —>  빠져나오는 명령

##### 11. file clone 가상환경에
 ```bash
sudo git clone https://github.com/Tory-Hwang/Jetson-Nano2.git
````
```bash
 ls
cd Jetson-Nano2/V8
````
 ```bash
pip install ultralytics
````
```bash
gedit requirements.txt
````
```bash
torch==1.11.0
torchvision=0.12.0
````
```bash
pip install -r requirements.txt
````
!![2](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/4442d525-ee44-425c-8dbc-83b76ad02718)

```bash
pip install ffmpeg-python
````
