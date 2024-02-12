#### YOLOV88_jetson4GB
##### 참고 링크 https://docs.ultralytics.com/
##### 참고 링크 https://blog.naver.com/tory0405/223246391729  설치는 따라하니 잘 되지만 하드웨어 환경이 나랑 다른 듯하다. 코드를 따로 수정을 해주었다. 
##### https://medium.com/@deandu/how-to-use-the-yolov8-with-csi-camera-in-jetson-xavier-d2286a0f22bb
##### 1. Image Download
####### Jetson Nano Developer Kit SD Card Image, and note where it was saved on the computer.
######[Download the Jetson Nano Developer Kit SD Card Image]([https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write] URL "Download Jetson Nano Image")
##### 2. cooling fan
```bash
git clone https://github.com/jetsonworld/jetson-fan-ctl.git
ls
cd jetson-fan-ctl
sudo sh install.sh
````
###### sudo sh install.sh 명령어는 리눅스나 유닉스 기반 시스템에서 사용되며, 주로 스크립트나 프로그램을 관리자 권한으로 설치하기 위해 사용됩니다. 이 명령어를 분해하여 그 의미를 자세히 설명하겠습니다:sudo: "Superuser Do"의 약자로, 다른 명령어를 슈퍼유저(루트 유저)의 권한으로 실행하게 해주는 프로그램입니다. 일반 사용자가 시스템에 영향을 미치는 작업(예: 소프트웨어 설치, 시스템 설정 변경 등)을 수행할 때 사용합니다.sh: "Shell"의 약자로, 쉘 스크립트를 해석하고 실행하는 명령어 해석기입니다.sh는 다양한 쉘 중 하나인 Bourne Shell을 가리키기도 하며, 리눅스나 유닉스 시스템에서 스크립트를 실행하는 데 사용됩니다.install.sh: install.sh는 일반적으로 설치 스크립트 파일의 이름입니다.이 스크립트는 소프트웨어나 프로그램을 시스템에 설치하기 위한 명령어들을 포함하고 있습니다.파일 이름의 .sh 확장자는 이 파일이 쉘 스크립트임을 나타냅니다.따라서, sudo sh install.sh 명령어는 install.sh라는 쉘 스크립트를 슈퍼유저 권한으로 실행하여, 스크립트에 포함된 지시에 따라 프로그램이나 소프트웨어를 설치하라는 의미입니다.이 명령어를 사용함으로써, 사용자는 스크립트에 정의된 대로 소프트웨어 설치 과정을 자동으로 진행할 수 있습니다.이 방법은 복잡한 설치 과정을 단순화하고, 설치 시 필요한 다양한 명령어를 일일이 입력할 필요 없이 소프트웨어를 쉽게 설치할 수 있게 해줍니다.
##### 3.  usm카메라 (usm카메라는 잘 된다. 하지만 csi카메라는 가상에서는 실행이 되질 않았다)
##### 4. 한글 폰트 설치
```bash
sudo apt-get install language-pack-ko
sudo locale-gen ko_KR.UTF-8
sudo apt-get install fonts-nanum fonts-nanum-coding fonts-nanum-extra
````
##### 5. conda install
###### 참고 https://cyb.tw/docs/Tech/2020/9/18_Install-anaconda-on-Jetson-Nano.html#install-archiconda
```bash
sudo apt-get update
````
```bash
wget --quiet -O archiconda.sh https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh && \
    sh archiconda.sh -b -p $HOME/archiconda3 && \
    rm archiconda.sh
````

```bash
export PATH="/path/dli/anaconda3/bin:$PATH"
````
```bash
conda config --add channels gaiar
````
```bash
conda config --add channels conda-forge
````
```bash
conda config --add channels c4aarch64
````
```bash
conda update -n base --all
````
```bash 
conda create -n py38 python=3.8
````

