# TTC Anomaly Detection

This application used Tensorflow Object Detection API to train power rail anomaly detectors on FILR infrared images. 

Faster R-CNN Inception V2 and SSD MobileNet V1 models are used. 

A few model checkpoints are provided in frozen_graphs. 

A few scripts are included in dataset_tools to help with constructing TFrecords. 

GUIs are developed for converting images into TFrecord, inference, processing detections and visualization.

## Getting Started

The anomaly_detection_demo notebook will give a simple example of detecting anomalies using a trained model.

Please see the step_by_step_guide for detailed explaination on how to inference new videos and train models.

Feel free to have a look on the API_tutorial to get a biref understanding of the development process.


## Prerequisites and Installation

Since the app is based on Tensorflow Object Detection API, its file path structure is identical to the original API. 

However, only slim and object_detection are kept to reduce the size.

Prerequisites and installation are identical to the original API. [See details](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md)

If anyone use this only for inference, not to train new models, some modules such as COCO API can be omitted.

Run anomaly_detection_demo to see if everything is installed properly.

## Notes

The code of original API is from April 2018, you can try download the latest version and copy following files into it.

anomaly_detection_demo.ipynb

GUI_#1_images_to_TFrecord.ipynb

GUI_#2_inference_TFrecord.ipynb

GUI_#3_process_detections.ipynb

GUI_Pascal_to_TFrecord.ipynb

Read_TFrecord.ipynb

dataset_tools/create_pascal_tf_record_VOTT_Copy.py

data/anomaly_label_map.pbtxt

test_data

test_images

frozen_graphs


## Authors

Developer: [liutuocheng](https://github.com/liutuocheng)

Supervisor: [ssanner](https://github.com/ssanner)
