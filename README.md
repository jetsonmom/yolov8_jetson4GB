######  참고 링크 https://blog.naver.com/tory0405/223246391729

https://medium.com/@scofield44165/jetson-nano-dev-kit%E4%B8%AD%E5%AE%89%E8%A3%9Darchiconda-install-archiconda-in-jetson-nano-dev-kit-1e695326596f

###### 잘 되던게 github 정리하려고 다시 시작했는데 안된다. 경험하지 않은 에러가 속출한다. 그 내용은 블로그에 정리를 하였다. https://blog.naver.com/jmerrier/223392057106 그리고 다시 정리한다. 


처음부터 yolo 가상환경 만들기
 uname -a
wget https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh
sudo chmod 755 Archiconda3-0.2.3-Linux-aarch64.sh

dli@dli:~$ ls
Archiconda3-0.2.3-Linux-aarch64.sh  Pictures
Desktop                             Public
Documents                           Templates
Downloads                           Videos
examples.desktop                    yolov8_4gb
Music

dli@dli:~$ ./Archiconda3-0.2.3-Linux-aarch64.sh 

yes
enter


yes

result 
installing: cryptography-2.5-py37h9d9f1b6_1 ...
installing: wheel-0.32.1-py37_0 ...
installing: pip-10.0.1-py37_0 ...
installing: pyopenssl-18.0.0-py37_0 ...
installing: urllib3-1.23-py37_0 ...
installing: requests-2.19.1-py37_0 ...
installing: conda-4.5.12-py37_0 ...
installation finished.
Do you wish the installer to initialize Archiconda3
in your /home/dli/.bashrc ? [yes|no]
[no] >>> yes

Initializing Archiconda3 in /home/dli/.bashrc
A backup will be made to: /home/dli/.bashrc-archiconda3.bak


For this change to become active, you have to open a new terminal.

Thank you for installing Archiconda3!


conda env list
conda activate base

dli@dli:~$ jetson_release

result

Software part of jetson-stats 4.2.7 - (c) 2024, Raffaello Bonghi
Model: NVIDIA Jetson Nano Developer Kit - Jetpack 4.5.1 [L4T 32.5.1]
NV Power Mode[0]: MAXN
Serial Number: [XXX Show with: jetson_release -s XXX]
Hardware:
 - P-Number: p3448-0000
 - Module: NVIDIA Jetson Nano (4 GB ram)
Platform:
 - Distribution: Ubuntu 18.04 Bionic Beaver
 - Release: 4.9.201-tegra
jtop:
 - Version: 4.2.7
 - Service: Active
Libraries:
 - CUDA: 10.2.89
 - cuDNN: 8.0.0.180
 - TensorRT: 7.1.3.0
 - VPI: 1.0.15
 - Vulkan: 1.2.70
 - OpenCV: 4.1.1 - with CUDA: NO

python3.8 가상환경 만들기

base가 아닌 native 환경에서 아래 명령어를 실행한다.

conda create -n yolo python=3.8 -y

dli@dli:~$ conda env list
# conda environments:
#
base                  *  /home/dli/archiconda3
yolo                     /home/dli/archiconda3/envs/yolo


dli@dli:~$ conda activate yolo
(yolo) dli@dli:~$ 

(yolo) dli@dli:~$ pip install -U pip wheel gdown

(yolo) dli@dli:~$  gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM

(yolo) dli@dli:~$ gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV

아래 두 라인을 실행(library 설치) 후 torch, torchvision은 확인이 가능하였다.
sudo apt-get install libopenblas-base libopenmpi-dev
sudo apt-get install libomp-dev

(yolo) dli@dli:~$ python
Python 3.8.13 | packaged by conda-forge | (default, Mar 25 2022, 05:56:18) 
[GCC 10.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
/home/dli/archiconda3/envs/yolo/lib/python3.8/site-packages/torch/_masked/__init__.py:223: UserWarning: Failed to initialize NumPy: No module named 'numpy' (Triggered internally at  /pytorch/torch/csrc/utils/tensor_numpy.cpp:68.)
  example_input = torch.tensor([[-3, -2, -1], [0, 1, 2]])

(yolo) dli@dli:~$ conda install numpy
after download -> install
pip install torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl

(yolo) dli@dli:~$ python

>>> import torch
>>> import torchvision
>>> print(torch.__version__)
>>> print(torchvision.__version__)
>>> print("cuda used", torch.cuda.is_available())
cuda used True
>>> 

git clone https://github.com/Tory-Hwang/Jetson-Nano2

(yolo) dli@dli:~$ cd Jetson-Nano2/
(yolo) dli@dli:~/Jetson-Nano2$ cd V8
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install ultralytics
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install -r requirements.txt 
(yolo) dli@jdli:~/Jetson-Nano2/V8$ pip install ffmpeg-python

yolo 실행은 display가 필요하므로 jetson을 TV에 연결하고 아래를 실행하였다. 물론 USB camera를 연결하였다. 그러나 전혀 Yolo를 실행하는 화면이 보이지 않았다.

(yolo) dli@jetson:~/Jetson-Nano2/V8$ python detectY8.py 

코드를 보니 rtsp가 기본으로 되어있다. 그래서 rtsp를 사용하지 않도록 변경했다.

def predict(cfg=DEFAULT_CFG, use_python=False):
    brtsp = True
-> 
    brtsp = False
detectY8.py 스크립트에서 RTSP(Remote Desktop Protocol)를 사용하지 않도록 변경하려면, brtsp = True 라인을 찾아 False로 변경해야 합니다. 이 변경은 스크립트가 RTSP 스트리밍 대신 다른 비디오 입력 소스(예: USB 카메라)를 사용하도록 지시합니다. 코드에서 brtsp 변수가 RTSP 스트리밍을 활성화하거나 비활성화하는 데 사용되는 것으로 보입니다.






