# Defect tracking method using ScaledYOLOv4 for getting rid of multiple counting errors


# Overview

Defect tracking involves following individual defects of interest across frames. It
combines the output of an [defect detector](https://ieeexplore.ieee.org/document/9515185) model
with a secondary algorithm to determine which detections are identifying "the same"
defect passing over frame over time.

Please read more in the README of the original [roboflow repository](https://github.com/roboflow-ai/zero-shot-object-tracking).
# Getting Started
First of all, if you do not have a ML background, it would be hard for you to keep track of everything. Hence, I would first recommend a deep dive into the subject.

If you just need to get something done quickly and to get it up and running, then follow the steps:


## Training your model
In order to perform tracking, you need an object detection model. This model needs lots of data to be trained. Hence, the first step is to gather lots of data for the object you want to detect.
The next step is to clone the [scaledyolov4 repository](https://github.com/WongKinYiu/ScaledYOLOv4). Look in the ReadME for the "train your custom classifier" section and train your custom classifier. 
Make sure you have a suitable infrastructure for training, because if you do not have a CUDA enabled GPU and you do not have a suitable workstation, you could lose days and days, without making any real progress. For an alternative, try [Google Colab](https://colab.research.google.com/). They have some free, low power GPU resources, that are good enough for basic research or testing.



## Performing Object Tracking
After you have trained you model, save the weights in a ".pt" format. Moreover, copy your weights into the Defect_tracking_with_ScaledYOLOv4 folder.

Make sure that CUDA is installed and that you have a CUDA comaptible GPU.
Make sure that you installed everything that is needed for ScaledYOLOV4, correctly (correct pytorch version, correctly installed mish-cuda etc).

For the moment this only runs on Ubuntu. I do not know a Windows version that can correctly install mish-cuda. A workaround would be to use another activation function, like ReLU, but then you lose out on ScaledYOLOv4's insane performance.

## We suggest this [tutorial](https://medium.com/analytics-vidhya/install-cuda-11-2-cudnn-8-1-0-and-python-3-9-on-rtx3090-for-deep-learning-fcf96c95f7a1) for installing everything correctly


### Next, clone repositories

```
git clone https://github.com/tulbureandreit/Defect_tracking_with_ScaledYOLOv4
       
### Install requirements 
Make sure you have Python 3.7+ installed & that you are on an Ubuntu 20.04 machine

### Run:
```bash
pip install --upgrade pip
pip install -r requirements.txt
```


### Run with ScaledYOLOv4 (this model is hardcoded in the algo - for other detectors please visit original roboflow repo).

```bash
python scaledolov4_defect_tracker.py --weights best.pt --source data/video/clean.mp4 --detection-engine scaledyolov4 --info
```


Help

```bash
python scaledyolov4_defect_tracker.py -h
```
```
--weights WEIGHTS                model.pt path
--source SOURCE                  source (works for video:webcam, industrial cameras, IP cameras & images)
--img-size IMG_SIZE              inference size (pixels)
--confidence CONFIDENCE          object confidence threshold                      
--overlap OVERLAP                IOU threshold for NMS
--device DEVICE                  cuda device, i.e. 0 or 0,1,2,3 or cpu
--view-img                       display results
--save-txt                       save results to *.txt
--save-conf                      save confidences in --save-txt labels
--classes CLASSES                filter by class: --class 0, or --class 0 2 3
--agnostic-nms                   class-agnostic NMS
--update                         update all models
--nms_max_overlap                Non-maxima suppression threshold: Maximum detection overlap.
--max_cosine_distance            Gating threshold for cosine distance metric (object appearance).
--info                           Print debugging info.
```
## We ran this on an RTX3090 GPU on an Ubuntu workstation.

## Acknowledgements

Huge thanks to:

- [yolov4-deepsort by theAIGuysCode](https://github.com/theAIGuysCode/yolov4-deepsort)
- [ScaledYOLOv4](https://github.com/WongKinYiu/ScaledYOLOv4)
- [Deep SORT Repository by nwojke](https://github.com/nwojke/deep_sort)
- [Zero-Shot Object Tracking announcement post](https://blog.roboflow.com/zero-shot-object-tracking/)

I do not own the CODE that was written before me and without any of the above mentioned people or organizations, nothing would have been published. I appended and modified some of the previous repositories. I plan on keeping this repository open-source, forever.

