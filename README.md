# YOLO-mini-tiger
An Amur Tiger Detector based on YOLOv3

We will open source our code in August...

## 0.Requirements
Requirements based on Darknet by AlexeyAB

## 1.Installation
`git clone https://github.com/AlexeyAB/darknet` <br>
`cd darknet/` <br>
rewrite `GPU=1` `CUDNN=1` `OPENCV=1` in ./darknet/Makefile <br>
run `make -j` <br>
**Detailed insatallation please refer to Darknet.** <br>

`git clone https://github.com/RunchenWei/YOLO-mini-tiger` <br>
put `./YOLO-mini-tiger/*.cfg` into `./darknet/cfg/` <br>
put `./YOLO-mini-tiger/*.weights` into `./darknet/` <br>

 

## 2.Training
Amur Tiger Detection Dataset: https://cvwc2019.github.io/challenge.html <br>
Our model trained without any pretrained model. <br>
How to train: `./darknet detector train cfg/tiger.data cfg/yolo-mini-tiger.cfg -gpus 0 -dont_show` <br>
**Tips: change your tiger.data with your dataset paths** <br>

## 3.Test
How to test: `./darknet detector test cfg/tiger.data cfg/yolo-mini-tiger.cfg backup/yolo-mini-tiger_final.weights xxx.jpg` <br>
Our model: to be continue... <br>

## 4.Evaluation
How to calculate mAP: `./darknet detector map cfg/tiger.data cfg/yolo-mini-tiger.cfg backup/yolo-mini-tiger_final.weights` <br>
How to eval: `./darknet detector valid cfg/tiger.data cfg/yolo-mini-tiger.cfg backup/yolo-mini-tiger_final.weights out ""` <br>

## 5.Our Results
to be continue <br>
![image] https://github.com/RunchenWei/YOLO-mini-tiger/blob/master/predictions.jpg
