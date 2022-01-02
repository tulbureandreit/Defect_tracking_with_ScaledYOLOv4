# Andrei defect tracking method for getting rid of multiple counting errors


# Overview

Defect tracking involves following individual defects of interest across frames. It
combines the output of an [defect detector](https://ieeexplore.ieee.org/document/9515185) model
with a secondary algorithm to determine which detections are identifying "the same"
defect passing over frame over time.

Please read more in the README of the original [roboflow repository](https://github.com/roboflow-ai/zero-shot-object-tracking).
# Getting Started



## Training your model




## Performing Object Tracking

###Clone repositories

```
git clone https://github.com/roboflow-ai/zero-shot-object-tracking
cd zero-shot-object-tracking
git clone https://github.com/openai/CLIP.git CLIP-repo
cp -r ./CLIP-repo/clip ./clip          


###Install requirements (python 3.7+)

```bash
pip install --upgrade pip
pip install -r requirements.txt
```


###Run with ScaledYOLOv4
```bash

python clip_object_tracker.py --weights models/yolov5s.pt --source data/video/fish.mp4 --detection-engine yolov5 --info
```


Help

```bash
python clip_object_tracker.py -h
```
```
--weights WEIGHTS [WEIGHTS ...]  model.pt path(s)
--source SOURCE                  source (video/image)
--img-size IMG_SIZE              inference size (pixels)
--confidence CONFIDENCE          object confidence threshold                      
--overlap OVERLAP                IOU threshold for NMS
--thickness THICKNESS            Thickness of the bounding box strokes
--device DEVICE                  cuda device, i.e. 0 or 0,1,2,3 or cpu
--view-img                       display results
--save-txt                       save results to *.txt
--save-conf                      save confidences in --save-txt labels
--classes CLASSES [CLASSES ...]  filter by class: --class 0, or --class 0 2 3
--agnostic-nms                   class-agnostic NMS
--augment                        augmented inference
--update                         update all models
--project PROJECT                save results to project/name
--name NAME                      save results to project/name
--exist-ok                       existing project/name ok, do not increment
--nms_max_overlap                Non-maxima suppression threshold: Maximum detection overlap.
--max_cosine_distance            Gating threshold for cosine distance metric (object appearance).
--nn_budget NN_BUDGET            Maximum size of the appearance descriptors allery. If None, no budget is enforced.
--info                           Print debugging info.
```
## Acknowledgements

Huge thanks to:

- [yolov4-deepsort by theAIGuysCode](https://github.com/theAIGuysCode/yolov4-deepsort)
- [ScaledYOLOv4](https://github.com/WongKinYiu/ScaledYOLOv4)
- [Deep SORT Repository by nwojke](https://github.com/nwojke/deep_sort)
- [Zero-Shot Object Tracking announcement post](https://blog.roboflow.com/zero-shot-object-tracking/)
I do not own the CODE and without any of the above mentioned people or organizations, nothing would have been published.

