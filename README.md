######  참고 링크 https://blog.naver.com/tory0405/223246391729

###### 잘 되던게 github 정리하려고 다시 시작했는데 안된다. 경험하지 않은 에러가 속출한다. 그 내용은 블로그에 정리를 하였다. 에러가 많아서 무척 길고 해결에 많은 시간이 필요했다https://blog.naver.com/jmerrier/223392057106 그리고 다시 정리한다. 제타님이 처음부터 가상에서 한 점이 나랑 다르다. 그래서 가상에서 하였다.  참고 https://medium.com/@scofield44165/jetson-nano-dev-kit%E4%B8%AD%E5%AE%89%E8%A3%9Darchiconda-install-archiconda-in-jetson-nano-dev-kit-1e695326596f
https://blog.naver.com/zeta0807
``` python
uycgb
```


###### yolo 가상환경 만들기
``` bash
uname -a
wget https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh
sudo chmod 755 Archiconda3-0.2.3-Linux-aarch64.sh
````

``` bash
 ls
````
###### 결과
Archiconda3-0.2.3-Linux-aarch64.sh  Pictures
Desktop                             Public
Documents                           Templates
Downloads                           Videos
examples.desktop                    yolov8_4gb
Music

``` bash
 ./Archiconda3-0.2.3-Linux-aarch64.sh 
```
###### 실행 중 선택하라고 나온다.
설치 프로그램 진행 방법
./Archiconda3-0.2.3-Linux-aarch64.sh 실행이미 실행 중인 상태이므로 바로 다음 단계로 넘어갑니다.
라이선스 스크롤링라이선스 텍스트를 모두 읽거나 빠르게 넘기고 싶다면 [q] 키를 누르세요. 텍스트가 모두 표시될 때까지 Enter 키를 계속 누를 수도 있습니다.
설치 경로 지정 및 설치 완료설치 경로를 입력하라는 메시지가 나타납니다. 기본 경로를 사용하려면 [Enter] 키를 눌러 계속하세요.
환경 변수 설정설치가 완료되면 터미널에서 conda 명령을 사용하기 위해 다음과 같이 .bashrc에 경로를 추가하세요.
yes--->
enter --->
yes
in your /home/ldh/.bashrc ? [yes|no]
[no] >>> yes


``` bash
###### result 
ldh@ldh-desktop:~$  ./Archiconda3-0.2.3-Linux-aarch64.sh

Welcome to Archiconda3 0.2.3

In order to continue the installation process, please review the license
agreement.
Please, press ENTER to continue
>>> q
Copyright (c) 2016-2017 Jonathan J. Helmus
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

    * Redistributions of source code must retain the above copyright
       notice, this list of conditions and the following disclaimer.

    * Redistributions in binary form must reproduce the above
       copyright notice, this list of conditions and the following
       disclaimer in the documentation and/or other materials provided
       with the distribution.

    * Neither the name of the developers nor the names of any
       contributors may be used to endorse or promote products derived
       from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


Do you accept the license terms? [yes|no]
[no] >>> 
Please answer 'yes' or 'no':'
>>> yes

Archiconda3 will now be installed into this location:
/home/ldh/archiconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below

[/home/ldh/archiconda3] >>> 
PREFIX=/home/ldh/archiconda3
installing: python-3.7.1-h39be038_1002 ...
Python 3.7.1
installing: ca-certificates-2018.03.07-0 ...
installing: conda-env-2.6.0-1 ...
installing: libgcc-ng-7.3.0-h5c90dd9_0 ...
installing: libstdcxx-ng-7.3.0-h5c90dd9_0 ...
installing: bzip2-1.0.6-h7b6447c_6 ...
installing: libffi-3.2.1-h71b71f5_5 ...
installing: ncurses-6.1-h71b71f5_0 ...
installing: openssl-1.1.1a-h14c3975_1000 ...
installing: xz-5.2.4-h7ce4240_4 ...
installing: yaml-0.1.7-h7ce4240_3 ...
installing: zlib-1.2.11-h7b6447c_2 ...
installing: readline-7.0-h7ce4240_5 ...
installing: tk-8.6.9-h84994c4_1000 ...
installing: sqlite-3.26.0-h1a3e907_1000 ...
installing: asn1crypto-0.24.0-py37_0 ...
installing: certifi-2018.10.15-py37_0 ...
installing: chardet-3.0.4-py37_1 ...
installing: idna-2.7-py37_0 ...
installing: pycosat-0.6.3-py37h7b6447c_0 ...
installing: pycparser-2.19-py37_0 ...
installing: pysocks-1.6.8-py37_0 ...
installing: ruamel_yaml-0.15.64-py37h7b6447c_0 ...
installing: six-1.11.0-py37_1 ...
installing: cffi-1.11.5-py37hc365091_1 ...
installing: setuptools-40.4.3-py37_0 ...
installing: cryptography-2.5-py37h9d9f1b6_1 ...
installing: wheel-0.32.1-py37_0 ...
installing: pip-10.0.1-py37_0 ...
installing: pyopenssl-18.0.0-py37_0 ...
installing: urllib3-1.23-py37_0 ...
installing: requests-2.19.1-py37_0 ...
installing: conda-4.5.12-py37_0 ...
installation finished.
Do you wish the installer to initialize Archiconda3
in your /home/ldh/.bashrc ? [yes|no]
[no] >>> yes

Initializing Archiconda3 in /home/ldh/.bashrc
A backup will be made to: /home/ldh/.bashrc-archiconda3.bak


For this change to become active, you have to open a new terminal.

Thank you for installing Archiconda3!
```
``` bash
conda env list
conda activate base
jetson_release 

```
##### conda environments:
python3.8 가상환경 만들기

base가 아닌 native 환경에서 아래 명령어를 실행한다.
``` bash
conda create -n yolo python=3.8 -y
conda env list
```

``` bash
 conda activate yolo
```
###### "conda activate yolo"를 실행하여 yolo 가상환경으로 진입해서 pytorch, torchvision을 설치하는 과정이다.

###### 결과 가상에서 설치 torch, torchvosion 다운로드
(yolo) dli@dli:~$ 

``` bash
 pip install -U pip wheel gdown

 gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM

 gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV
```
아래 두 라인을 실행(library 설치) 후 torch, torchvision은 확인이 가능하였다.
``` bash
sudo apt-get install libopenblas-base libopenmpi-dev
sudo apt-get install libomp-dev
```
``` bash
(yolo) dli@dli:~$ python
Python 3.8.13 | packaged by conda-forge | (default, Mar 25 2022, 05:56:18) 
[GCC 10.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
/home/dli/archiconda3/envs/yolo/lib/python3.8/site-packages/torch/_masked/__init__.py:223: UserWarning: Failed to initialize NumPy: No module named 'numpy' (Triggered internally at  /pytorch/torch/csrc/utils/tensor_numpy.cpp:68.)
  example_input = torch.tensor([[-3, -2, -1], [0, 1, 2]])
>>>
```

###### 위의 에러는 numpy 다운로드 안되어 있어서 에러 발생
``` bash
 conda install numpy                                       # 또는 >>> 다음에 설치를 해도 된다.
```
after download -> install
``` bash
pip install torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl
pip install torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl
```
``` bash

(yolo) dli@dli:~$ python

>>> import torch
>>> import torchvision
>>> print(torch.__version__)
>>> print(torchvision.__version__)
>>> print("cuda used", torch.cuda.is_available())
cuda used True
>>> 
```
``` bash
git clone https://github.com/Tory-Hwang/Jetson-Nano2
```
``` bash
(yolo) dli@dli:~$ cd Jetson-Nano2/
(yolo) dli@dli:~/Jetson-Nano2$ cd V8
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install ultralytics
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install -r requirements.txt 
(yolo) dli@jdli:~/Jetson-Nano2/V8$ pip install ffmpeg-python
```
######  yolov8n.pt 다운로드
https://github.com/ultralytics/ultralytics?tab=readme-ov-file
위의 링크에서 다운로드 받았다.
경로는 (yolo) dli@jetson:~/Jetson-Nano2/V8

!![제목 없음](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/d687b7ea-5889-466e-83cb-a249954658f1)

!![Screenshot from 2024-03-24 23-44-20](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/89dc7fc0-fc81-48ba-8268-e9b7667e04f7)

!![Screenshot from 2024-03-24 23-50-56](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/bb772518-fb6a-4f07-a4af-b340ff53e476)



###### USB camera를 연결하였다. 그러나 전혀 Yolo를 실행하는 화면이 보이지 않았다. 이유는 토리삼촌과 나의 환경이 달라서이다. 코드 수정해야한다.
``` bash
gedit  detectY8.py
```

(yolo) dli@jetson:~/Jetson-Nano2/V8$ python detectY8.py 

###### 코드를 보니 rtsp가 기본으로 되어있다. 그래서 rtsp를 사용하지 않도록 변경했다.
!![Screenshot from 2024-03-25 12-58-30](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/3883ca74-efd7-4e92-9888-89b40a9e01bd)


def predict(cfg=DEFAULT_CFG, use_python=False):
    brtsp = True
-> 
    brtsp = False
detectY8.py 스크립트에서 RTSP(Remote Desktop Protocol)를 사용하지 않도록 변경하려면, brtsp = True 라인을 찾아 False로 변경해야 합니다. 이 변경은 스크립트가 RTSP 스트리밍 대신 다른 비디오 입력 소스(예: USB 카메라)를 사용하도록 지시합니다. 코드에서 brtsp 변수가 RTSP 스트리밍을 활성화하거나 비활성화하는 데 사용되는 것으로 보입니다.


``` bash
(yolo) yolo@yolo-desktop:~/Jetson-Nano2/V8$ python detectY8.py
```
!![Screenshot from 2024-03-25 13-23-47](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/f84b0a67-571e-45aa-969e-4e6e8188a0b8)





