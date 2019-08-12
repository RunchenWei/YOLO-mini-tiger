# YOLO-mini-tiger
An Amur Tiger Detector based on YOLOv3 <br>

We will open source our code in August... <br>

## 0.Requirements
Requirements based on Darknet by AlexeyAB <br>

## 1.Installation
`git clone https://github.com/AlexeyAB/darknet` <br>
`cd darknet/` <br>
rewrite `GPU=1` `CUDNN=1` `OPENCV=1` in `./darknet/Makefile` <br>
run `make -j` <br>
**Detailed insatallation please refer to Darknet.** <br>

`git clone https://github.com/RunchenWei/YOLO-mini-tiger` <br>
put `./YOLO-mini-tiger/*.cfg` into `./darknet/cfg/` <br>
put `./YOLO-mini-tiger/*.weights` into `./darknet/` <br>

 

## 2.Training
Amur Tiger Detection Dataset: https://cvwc2019.github.io/challenge.html <br>
Our model trained without any pretrained model. <br>
**Training on Amur Tiger dataset** <br>
(1) create some folders: `./darknet/data/tiger/VOCdevkit/VOC2007/` <br>
(2) copy your Amur Tiger dataset to `./darknet/data/tiger/VOCdevkit/VOC2007/`  <br>
    The folder tree is like this: <br>
    `./darknet/data/tiger/VOCdevkit/VOC2007/Annotiation/` <br>
    `./darknet/data/tiger/VOCdevkit/VOC2007/ImageSets/` <br>
    `./darknet/data/tiger/VOCdevkit/VOC2007/JPEGImages/` <br>
(3) copy `./darknet/scripts/voc_label.py` to `./darknet/data/tiger/`<br>
    edit lines: <br>
    `sets=[('2007','train'),('2007','val'),('2007','test')]` <br>
    `classes= ["tiger"]` <br>
    comment the last two lines:<br>
    `os.system("...")`<br>
    run `python voc_label.py`<br>
    and then you will get `2007_train.txt`, `2007_val.txt`, `2007_test.txt`<br>
(4) create a file: `./darknet/data/tiger.names` write a line `tiger` in `tiger.names` for label name<br>
(5) create a file: `./darknet/cfg/tiger.data` write lines in `tiger.data`<br>
    `classes= 1`<br>
    `train  = your root path/darknet/data/tiger/2007_train.txt`<br>
    
    if you want to use val set, please write:<br>
      `valid  = your root path/darknet/data/tiger/2007_val.txt`<br>
    if you want to use test set, please write:<br>
      `valid  = your root path/darknet/data/tiger/2007_test.txt`<br>
    
    `names = your root path/darknet/data/tiger.names`<br>
    `backup = your root path/darknet/backup/`<br>

How to train: `./darknet detector train cfg/tiger.data cfg/yolo-mini-tiger.cfg -gpus 0 -dont_show` <br>
**Tips: change your tiger.data with your dataset paths** <br>

## 3.Test
How to test: `./darknet detector test cfg/tiger.data cfg/yolo-mini-tiger.cfg backup/yolo-mini-tiger_final.weights xxx.jpg` <br>
Our model: **yolo-mini-tiger.weights** <br>

## 4.Evaluation
How to calculate mAP: `./darknet detector map cfg/tiger.data cfg/yolo-mini-tiger.cfg backup/yolo-mini-tiger_final.weights` <br>
How to eval: `./darknet detector valid cfg/tiger.data cfg/yolo-mini-tiger.cfg backup/yolo-mini-tiger_final.weights -out ""` <br>

## 5.Our Results
| **Model**        | **mAP(COCO)**           | **BFLOPs**           | **Model Size(MB)**  |
|:-------------:|:-------------:|:-------------:|:-----:|
| YOLO-mini      |0.479 | 0.466 | 4.8 |

![image](https://github.com/RunchenWei/YOLO-mini-tiger/blob/master/predictions.jpg)
