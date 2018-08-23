# TTC Anomaly Detection

This application used Tensorflow Object Detection API to train power rail anomaly detectors on FILR infrared images. 

Faster R-CNN inception-v2 and SSD MobileNet V1 models are used. 

A few model checkpoints are provided in frozen_graphs. 

A few scripts are included in dataset_tools to help with constructing TFrecords. 

GUIs are developed for converting images into TFrecord, inference, processing detections and visualization.

## Getting Started

The anomaly_detector_demo notebook will give a simple example of detecting anomalies using a trained model.

Please see the step_by_step_guide for detailed explaination on how to inference new videos and train models.

Feel free to have a look on the API_tutorial to get a biref understanding of the development.


### Prerequisites and Installation

Since the app is based on Tensorflow Object Detection API, the file path structure is identical to the original API. 

However, only slim and object_detection are kept to reduce the size.

Prerequisites and installation are identical to the original API.

If anyone use this only for inference, not to train new models, some modules such as COCO API can be omitted.

## Authors

Developer: [liutuocheng](https://github.com/liutuocheng)
Supervisor: [ssanner](https://github.com/ssanner)


