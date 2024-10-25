######  참고 링크 https://blog.naver.com/tory0405/223246391729

###### 잘 되던게 github 정리하려고 다시 시작했는데 안된다. 경험하지 않은 에러가 속출한다. 그 내용은 블로그에 정리를 하였다. 에러가 많아서 무척 길고 해결에 많은 시간이 필요했다https://blog.naver.com/jmerrier/223392057106 그리고 다시 정리한다. 제타님이 처음부터 가상에서 한 점이 나랑 다르다. 그래서 가상에서 하였다.  참고 https://medium.com/@scofield44165/jetson-nano-dev-kit%E4%B8%AD%E5%AE%89%E8%A3%9Darchiconda-install-archiconda-in-jetson-nano-dev-kit-1e695326596f
https://blog.naver.com/zeta0807

<b> 참고 링크 : 강의 때 상금 걸고 대회 했을 때 1등한 학생이 한 내용
chatgpt도움을 받아서 컴공과 학생이 만듦
https://github.com/moon-joy/Jetson-nano/blob/main/README.md




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

 실행 중 선택하라고 나온다.
설치 프로그램 진행 방법
./Archiconda3-0.2.3-Linux-aarch64.sh 실행이미 실행 중인 상태이므로 바로 다음 단계로 넘어갑니다.
라이선스 스크롤링라이선스 텍스트를 모두 읽거나 빠르게 넘기고 싶다면 [q] 키를 누르세요. 텍스트가 모두 표시될 때까지 Enter 키를 계속 누를 수도 있습니다.
설치 경로 지정 및 설치 완료설치 경로를 입력하라는 메시지가 나타납니다. 기본 경로를 사용하려면 [Enter] 키를 눌러 계속하세요.
환경 변수 설정설치가 완료되면 터미널에서 conda 명령을 사용하기 위해 다음과 같이 .bashrc에 경로를 추가하세요.
enter
yes--->
enter --->
yes
in your /home/ldh/.bashrc ? [yes|no]
[no] >>> yes
```

``` bash
  ./Archiconda3-0.2.3-Linux-aarch64.sh 결과는 아래와 같다

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
conda deactivate
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
pip install torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl
pip install torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl
python -c "import torch; print(torch.__version__)"

```


###### 위의 에러는 numpy 다운로드 안되어 있어서 에러 발생
``` bash
 conda install numpy                                       # 또는 >>> 다음에 설치를 해도 된다.
```
after download -> install

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
(yolo) dli@dli:~/Jetson-Nano2$ sudo apt install tree
(yolo) dli@jdli:~/Jetson-Nano2$ tree -L 2
```
#####

![image](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/3eaf5716-b3f0-403c-88c1-473befe274e0)
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

brtsp = True를 설정하는 것은 RTSP(Real Time Streaming Protocol) 스트림 처리와 관련이 있습니다. 이 설정의 의미와 변경하는 이유를 설명해드리겠습니다:

brtsp(Better RTSP) 설정의 목적:

더 효율적인 RTSP 스트림 처리
버퍼링 최적화
프레임 스킵 방지
메모리 사용량 최적화


True로 설정할 때의 장점:

더 안정적인 스트림 처리
지연시간 감소
메모리 효율성 향상


False로 변경하는 주요 이유들:

하드웨어 리소스가 제한적일 때
실시간성보다 처리의 정확성이 더 중요할 때
메모리 사용량을 줄여야 할 때
레거시 시스템과의 호환성이 필요할 때
# 상황에 따른 설정 예시
if hardware_limited:
    brtsp = False  # 리소스 제한적인 경우
elif need_realtime:
    brtsp = True   # 실시간 처리 중요한 경우
elif legacy_system:
    brtsp = False  # 구형 시스템 호환성


``` bash
(yolo) yolo@yolo-desktop:~/Jetson-Nano2/V8$ python detectY8.py
```
!![Screenshot from 2024-03-25 13-23-47](https://github.com/jetsonmom/yolov8_jetson4GB/assets/92077615/f84b0a67-571e-45aa-969e-4e6e8188a0b8)

``` bash
# Ultralytics YOLO 🚀, GPL-3.0 license

import argparse
import torch
from ultralytics.yolo.engine.predictor import BasePredictor
from ultralytics.yolo.engine.results import Results
from ultralytics.yolo.utils import DEFAULT_CFG, ROOT, ops
from ultralytics.yolo.utils.plotting import Annotator, colors, save_one_box


class DetectionPredictor(BasePredictor):

    def get_annotator(self, img):
        return Annotator(img, line_width=self.args.line_thickness, example=str(self.model.names))

    def preprocess(self, img):
        img = torch.from_numpy(img).to(self.model.device)
        img = img.half() if self.model.fp16 else img.float()  # uint8 to fp16/32
        img /= 255  # 0 - 255 to 0.0 - 1.0
        return img

    def postprocess(self, preds, img, orig_img):
        preds = ops.non_max_suppression(preds,
                                        self.args.conf,
                                        self.args.iou,
                                        agnostic=self.args.agnostic_nms,
                                        max_det=self.args.max_det,
                                        classes=self.args.classes)

        results = []
        for i, pred in enumerate(preds):
            orig_img = orig_img[i] if isinstance(orig_img, list) else orig_img
            shape = orig_img.shape
            pred[:, :4] = ops.scale_boxes(img.shape[2:], pred[:, :4], shape).round()
            path, _, _, _, _ = self.batch
            img_path = path[i] if isinstance(path, list) else path
            results.append(Results(orig_img=orig_img, path=img_path, names=self.model.names, boxes=pred))
        return results

    def write_results(self, idx, results, batch):
        p, im, im0 = batch
        log_string = ''
        if len(im.shape) == 3:
            im = im[None]  # expand for batch dim
        self.seen += 1
        imc = im0.copy() if self.args.save_crop else im0
        if self.source_type.webcam or self.source_type.from_img:  # batch_size >= 1
            log_string += f'{idx}: '
            frame = self.dataset.count
        else:
            frame = getattr(self.dataset, 'frame', 0)
        self.data_path = p
        self.txt_path = str(self.save_dir / 'labels' / p.stem) + ('' if self.dataset.mode == 'image' else f'_{frame}')
        log_string += '%gx%g ' % im.shape[2:]  # print string
        self.annotator = self.get_annotator(im0)

        det = results[idx].boxes  # TODO: make boxes inherit from tensors
        if len(det) == 0:
            return log_string
        for c in det.cls.unique():
            n = (det.cls == c).sum()  # detections per class
            log_string += f"{n} {self.model.names[int(c)]}{'s' * (n > 1)}, "

        # write
        for d in reversed(det):
            cls, conf = d.cls.squeeze(), d.conf.squeeze()
            if self.args.save_txt:  # Write to file
                line = (cls, *(d.xywhn.view(-1).tolist()), conf) \
                    if self.args.save_conf else (cls, *(d.xywhn.view(-1).tolist()))  # label format
                with open(f'{self.txt_path}.txt', 'a') as f:
                    f.write(('%g ' * len(line)).rstrip() % line + '\n')
            if self.args.save or self.args.save_crop or self.args.show:  # Add bbox to image
                c = int(cls)  # integer class
                name = f'id:{int(d.id.item())} {self.model.names[c]}' if d.id is not None else self.model.names[c]
                label = None if self.args.hide_labels else (name if self.args.hide_conf else f'{name} {conf:.2f}')
                self.annotator.box_label(d.xyxy.squeeze(), label, color=colors(c, True))
            if self.args.save_crop:
                save_one_box(d.xyxy,
                             imc,
                             file=self.save_dir / 'crops' / self.model.model.names[c] / f'{self.data_path.stem}.jpg',
                             BGR=True)

        return log_string


def predict(cfg=DEFAULT_CFG, use_python=False):
   
    brtsp = False
    if brtsp: 
        cfg.source = 'rtsp://admin:satech1234@192.168.0.151:554/udp/av0_0'
    else:
        cfg.source = 'Moon.mp4'  # 동영상 파일 경로로 변경
        
    cfg.imgsz = 640
    cfg.show    = True    
    cfg.iou     = 0.45
    cfg.conf    = 0.15
    cfg.data    = "coco128.yaml"
    cfg.model   = 'yolov8n.pt'

    source = cfg.source if cfg.source is not None else ROOT / 'assets' if (ROOT / 'assets').exists() \
        else 'https://ultralytics.com/images/bus.jpg'

    args = dict(model=cfg.model, source=source)
    if use_python:
        from ultralytics import YOLO
        YOLO(cfg.model)(**args)(cfg)
    else:
        predictor = DetectionPredictor(overrides=args)
        predictor.predict_cli()


if __name__ == '__main__':
    predict(use_python = True)
```






