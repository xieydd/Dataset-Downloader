<!--
 * @Author: xieydd
 * @since: 2020-06-29 15:39:37
 * @lastTime: 2020-06-29 15:45:09
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
#### 引用
- [academic 种子下载链接](http://academictorrents.com/collection/)
- [hyper.ai 种子](https://hyper.ai/datasets/)
