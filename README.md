<!--
 * @Author: xieydd
 * @since: 2020-06-29 15:39:37
 * @lastTime: 2020-07-07 10:54:32
 * @LastAuthor: Do not edit
 * @message: 
--> 
### Dataset-Downloader
Download different DataSet Collection

#### 1. Imagenet
When torrent dir file can`t use, see all, if can use, see 4 directly.

1. ```sudo apt-get install aria2```

2. Navigate to ```http://academictorrents.com/collection/imagenet-2012``` and download torrent files for train and validation datasets.

3. Follow this page ```https://aria2.github.io/``` and do ```aria2c path_to_you_torrent_file.torrent``` for both validation and training files.

4. By now, you should have two files in your folder ```ILSVRC2012_img_train.tar``` and ```ILSVRC2012_img_val.tar```.

5. Run this command: 
```
mkdir train && mv ILSVRC2012_img_train.tar train/ && cd train
tar -xvf ILSVRC2012_img_train.tar && rm -f ILSVRC2012_img_train.tar
find . -name "*.tar" | while read NAME ; do mkdir -p "${NAME%.tar}"; tar -xvf "${NAME}" -C "${NAME%.tar}"; rm -f "${NAME}"; done
cd ..
```
6. And this:
```
mkdir val && mv ILSVRC2012_img_val.tar val/ && cd val && tar -xvf ILSVRC2012_img_val.tar
wget -qO- https://raw.githubusercontent.com/soumith/imagenetloader.torch/master/valprep.sh | bash
```

#### 2. Cifar10 and Cifar100

Directly download in http://www.cs.toronto.edu/~kriz/cifar.html for tar file

#### 3. COCO
When torrent dir file can`t use, see imagenet 1 2 3, if can use, see below directly.

#### 4. CelebA
Download torrent from hyper.ai/datasets/

#### 5. WiderFace
WiderFace can download from google cloud and tencent cloud from [here](http://shuoyang1213.me/WIDERFACE/) office.Or can download in [baiducloud](https://pan.baidu.com/s/1faHNz9ZrtEmr_yw48GW7ZA), code is `ievk`
If you need CNNPoint for MTCNN Train, you can download it in [here](http://mmlab.ie.cuhk.edu.hk/archive/CNN_FacePoint.htm).
#### 6. LFW
Labeled Faces in the Wild - aligned with deep funneling from site 1, this is not origin lfw dataset, if need, can download from site 1

#### 7. Mnist
Mnist raw file for test.

#### 8. OCR
[BaiduCloud](https://pan.baidu.com/s/1mRepVEvMa-U4e9ThiskVXg#list/path=%2F) code: 9s4x
| 数据集                              | 主页                                                         | 适用情况  | 数据情况                                                     | 标注形式                                                     | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ | --------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ICDAR2015                           | https://rrc.cvc.uab.es/?ch=4                                 | 检测&识别 | 语言: 英文     train:1,000     test:500                      | x1, y1, x2, y2, x3, y3, x4, y4, transcription                | 坐标: x1, y1, x2, y2, x3, y3, x4,  y4     transcription : 框内的文字信息 |
| MLT2019                             | https://rrc.cvc.uab.es/?ch=15                                | 检测&识别 | 语言: 混合     train:10,000     test:10,000                  | x1,y1,x2,y2,x3,y3,x4,y4,script,transcription                 | 坐标: x1, y1, x2, y2, x3, y3, x4,  y4     script: 文字所属语言     transcription : 框内的文字信息 |
| COCO-Text_v2                        | https://bgshih.github.io/cocotext/                           | 检测&识别 | 语言: 混合     train:43,686     validation:10,000     test:10,000 | json                                                         |                                                              |
| ReCTS                               | https://rrc.cvc.uab.es/?ch=12&com=introduction               | 检测&识别 | 语言: 混合     train:20,000     test:5,000                   | {       “chars”: [         {“points”:  [x1,y1,x2,y2,x3,y3,x4,y4], “transcription” : “trans1”, "ignore":0  },         {“points”:  [x1,y1,x2,y2,x3,y3,x4,y4], “transcription” : “trans2”, " ignore ":0  }],       “lines”: [         {“points”:  [x1,y1,x2,y2,x3,y3,x4,y4] , “transcription” : “trans3”, "ignore ":0  }],     } | points: x1,y1,x2,y2,x3,y3,x4,y4       chars: 字符级别的标注     lines: 行级别的标注.      transcription : 框内的文字信息     ignore: 0:不忽略，1:忽略 |
| SROIE                               | https://rrc.cvc.uab.es/?ch=13                                | 检测&识别 | 语言: 英文     train:699     test:400                        | x1, y1, x2, y2, x3, y3, x4, y4, transcription                | 坐标: x1, y1, x2, y2, x3, y3, x4,  y4     transcription : 框内的文字信息 |
| ArT(已包含Total-Text和SCUT-CTW1500) | https://rrc.cvc.uab.es/?ch=14                                | 检测&识别 | 语言: 混合     train: 5,603     test: 4,563                  | {     “gt_1”: [  {“points”: [[x1, y1], [x2, y2], …, [xn,  yn]], “transcription” : “trans1”, “language” : “Latin”,  "illegibility": false },             {“points”: [[x1, y1],  [x2, y2], …, [xn, yn]], “transcription” : “trans2”, “language” : “Chinese”,  "illegibility": false }],     } | points:  x1,y1,x2,y2,x3,y3,x4,y4…xn,yn      transcription : 框内的文字信息     language: 语言信息     illegibility: 是否模糊 |
| LSVT                                | https://rrc.cvc.uab.es/?ch=16                                | 检测&识别 | 语言: 混合     全标注     train: 30,000     test: 20,000     只标注文本     400,000 | {     “gt_1”: [  {“points”: [[x1, y1], [x2, y2], …, [xn,  yn]], “transcription” : “trans1”, "illegibility": false },             {“points”: [[x1, y1],  [x2, y2], …, [xn, yn]], “transcription” : “trans2”, "illegibility":  false }],     } | points:  x1,y1,x2,y2,x3,y3,x4,y4…xn,yn      transcription : 框内的文字信息     illegibility: 是否模糊 |
| Synth800k                           | http://www.robots.ox.ac.uk/~vgg/data/scenetext/              | 检测&识别 | 语言: 英文     800,000                                       | imnames:      wordBB:      charBB:      txt:                 | imnames: 文件名称     wordBB: 2*4*n,每张图像内的文本框     charBB: 2*4*n,每张图像内的字符框     txt: 每张图形内的字符串 |
| icdar2017rctw                       | https://blog.csdn.net/wl1710582732/article/details/89761818  | 检测&识别 | 语言: 混合     train:8,034     test:4,229                    | x1,y1,x2,y2,x3,y3,x4,y4,<识别难易程度>,transcription         | 坐标: x1, y1, x2, y2, x3, y3, x4,  y4     transcription : 框内的文字信息 |
| MTWI 2018                           | [识别:   https://tianchi.aliyun.com/competition/entrance/231684/introduction](https://tianchi.aliyun.com/competition/entrance/231684/introduction)      [检测: https://tianchi.aliyun.com/competition/entrance/231685/introduction](https://tianchi.aliyun.com/competition/entrance/231684/introduction) | 检测&识别 | 语言: 混合     train:10,000     test:10,000                  | x1, y1, x2, y2, x3, y3, x4, y4, transcription                | 坐标: x1, y1, x2, y2, x3, y3, x4,  y4     transcription : 框内的文字信息 |
| 百度中文场景文字识别                | https://aistudio.baidu.com/aistudio/competition/detail/20    | 识别      | 语言: 混合     train:未统计     test:未统计                  | h,w,name,value                                               | h: 图片高度     w: 图片宽度     name: 图片名     value: 图片上文字 |
| mjsynth                             | http://www.robots.ox.ac.uk/~vgg/data/text/                   | 识别      | 语言: 英文     9,000,000                                     | -                                                            | -                                                            |
| Synthetic Chinese String  Dataset(360万中文数据集)   | 链接：https://pan.baidu.com/s/1jefn4Jh4jHjQdiWoanjKpQ 提取码：spyi | 识别      | 语言: 混合     300k                                          | -                                                            | -                                                            |
| 英文识别数据大礼包(https://github.com/clovaai/deep-text-recognition-benchmark) 训练：MJSynth和SynthText  验证：IIIT, SVT, IC03, IC13, IC15, SVTP, CUTE   | 链接：https://pan.baidu.com/s/1KSNLv4EY3zFWHpBYlpFCBQ 提取码：rryk | 识别      | 语言: 英文                                              | -                                                            | -                                                            |

##### 数据生成工具
                                                    
https://github.com/TianzhongSong/awesome-SynthText
 
##### 数据集读取脚本
- [检测读取脚本](https://github.com/WenmuZhou/OCR_DataSet/tree/master/dataset/det.py)
- [识别读取脚本](https://github.com/WenmuZhou/OCR_DataSet/tree/master/dataset/rec.py)

#### 9. MS-Celeb-1M
Use this command `aria2c -c -j16 -s16 -x16 --follow-torrent=mem -o 'hyperai.torrent' 'https://hyper.ai/tracker/download?torrent=6470'`


#### 手势数据整理

| | 图片数量|	2d/3d| 真实/生成 | 标注类型	|url|备注
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| VGG|	2686 张图，13050 个手（4170高质量大手）	| 2d| 真实|手部 bbox ，不过并不一定都是正的 bbox |http://www.robots.ox.ac.uk/~vgg/data/hands/	|
VIVA Hand Detection Dataset	|54个视频	|2d|	真实|	手部 bbox|	http://cvrr.ucsd.edu/vivachallenge/index.php/hands/hand-detection/ |	2D bbox 信息，数据集场景为汽车内部驾驶员和乘客
OneHand10K	|11703 张图|	2d|	真实|	手部关键点位置以及手部mask图像|	https://www.yangangwang.com/papers/WANG-MCC-2018-10.html|	每张图仅有一只手，图片真实世界采集，室内外场景都有
MU HandImages ASL	|2425 张图|	2d|	真实|	手势类别信息（36种）|	http://www.massey.ac.nz/~albarcza/gesture_dataset2012.html|	手部基本占据整个图片，并且背景区域为黑。
EgoHands | 48个 videos，2700 frames，15000 个手	|2d	|真实|	手部像素级别的标注信息（左手、右手、观察者手和对方手）|	http://vision.soic.indiana.edu/projects/egohands/	|数据集事件全部为两个人之间的交互，例如下棋、玩游戏，双方的手都出现在图中
CVPR-HANDS 3D	|886个手势例子|	3d	|真实（Kinect采集）	|19 种动态手势类别，手部位置信息|	http://cvrr.ucsd.edu/LISA/hand.html	|数据集为司机驾驶汽车场景下手部信息或者车内乘客手部信息
HandNet	|212928	|3d	|真实	|指尖和手掌位置信息和方向信息	|http://www.cs.technion.ac.il/~twerd/WetzlerSlossbergKimmel-BMVC15.pdf	|该数据集多用来作指尖检测
11KHands	|11076 	|2d	|真实	|手掌人属性信息，包括性别，年龄等	|https://arxiv.org/pdf/1711.04322	|主要用来做性别识别和生物特征识别，手部占据整个图像，背景为白色
Hand Images Databases	|3000	|2d	|真实	|手掌人属性信息，性别、年龄、职业等	|https://www.mutah.edu.jo/biometrix/hand-images-databases.html	|用于预测手部人物属性信息，分为手机和网络摄像头拍摄获取两种
CMU Hand Dataset	|2800	|2d	|真实	|手部关键点信息|	http://domedb.perception.cs.cmu.edu/handdb.html	|该数据集论文方法识别关键点效果很好
Hand Gesture dataset|	|2d|	生成|	手势类别|	http://www-vpu.eps.uam.es/DS/HGds/index.html	|
NYU	|8252测试集和72757训练集|	3d|	真实|	| | 网站进不去详细信息没看到
GANerated Hands Dataset	|330,000	|2d	|生成|	21个手部关键点的2D、3D坐标|	http://handtracker.mpi-inf.mpg.de/projects/GANeratedHands/GANeratedDataset.htm	|
Large-scale Multiview 3D Hand Pose Dataset|	20, 500 different frames distributed in 21 sequences.|	3d|	真实|	bbox，关键点2D、3D坐标|	http://www.rovit.ua.es/dataset/mhpdataset/ |	多个视角拍摄手部
EgoGesture Dataset | 2,081 RGB-D videos, 24,161 gesture samples and 2,953,224 frames |3d|	真实|	83种静态和动态的手势类别，video标注信息包含手势开始和结束帧号|	http://www.nlpr.ia.ac.cn/iva/yfzhang/datasets/egogesture.html	|中科院自动化所模式识别实验室构建的大型数据集
MSRA Hand Gesture database| 9个人右手，每个人17种手势，每种手势500帧|	3d	|真实|	手势类别，手部 bbox 位置|	https://www.dropbox.com/s/c91xvevra867m6t/cvpr15_MSRAHandGestureDB.zip?dl=0	|官方论文网址进不去，失效
ChaLearn Gesture Data 2011 | | | | | http://gesture.chalearn.org/data/cgd2011	
Microsoft Kinect and Leap Motion Dataset|	14人采集，每人拍10种手势，每种手势10张图，共1400张图像	|3d|	真实|	|http://lttm.dei.unipd.it/downloads/gesture/	|
SCUT-Ego-Finger Dataset | 93729 frames from 24 videos	|2d|	真实|	手部位置和关节点位置	|http://www.hcii-lab.net/data/SCUTEgoFinger/index.htm	
SCUT-Ego-Gesture Dataset | 59,111 RGB images | 2d	|真实|	手部位置和关节点位置	|http://www.hcii-lab.net/data/SCUTEgoGesture/index.htm	

#### 引用
- [academic 种子下载链接](http://academictorrents.com/)
- [hyper.ai 种子](https://hyper.ai/datasets/)
- [OCR_DataSet](https://github.com/WenmuZhou/OCR_DataSet)
