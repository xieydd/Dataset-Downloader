<!--
 * @Author: xieydd
 * @since: 2020-06-29 15:39:37
 * @lastTime: 2020-07-02 10:23:06
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
WiderFace can download from google cloud and tencent cloud from [here](http://shuoyang1213.me/WIDERFACE/)

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


#### 引用
- [academic 种子下载链接](http://academictorrents.com/)
- [hyper.ai 种子](https://hyper.ai/datasets/)
- [OCR_DataSet](https://github.com/WenmuZhou/OCR_DataSet)
