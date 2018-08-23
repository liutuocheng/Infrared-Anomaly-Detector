This is a guide of using the Anomaly Detector by calling python scripts in command line or Windows PowerShell. 

For inference, you can just follow the GUI notebooks #123.

For small amount of images, use anomaly_detecion_demo

## Creating datasets

### Tagged images, for training and evaluation

Assume images are tagged using VoTT and exported into Pascal VOC format.

use dataset_tools\create_pascal_tf_record_VOTT_Copy.py to convert Pascal VOC to TFrecord

```
python dataset_tools\create_pascal_tf_record_VOTT.py 
--data_dir=PATH_TO_PASCAL_DATASET
--set=trainval 
--output_path=PATH_OF_DESTINATION
```

Set can be chosen from [train, val, trainval], depend on how the image lists are constructed.

Note that, this script only works when 'anomaly' is the only class of objects in the dataset.

### Include negative examples in Dataset

Put both positive and negative frames together for labeling using VoTT.

Omit all the negative frames in tagging, then export.


### Consecutive Images with no labels, for inference

use GUI_#1_images_to_TFrecord.ipynb, see details in the notebook

Images should be consecutive frames exported by ResearchIR software.


## Inference on TFrecord

use inference\infer_detections.py

```
python inference\infer_detections.py 
--input_tfrecord_paths=PATH_TO_IMAGES.record
--output_tfrecord_path=PATH_OF_INFERENCE.record
--inference_graph=PATH_TO_MODEL.pb
```
GUI#2 use this script, but can only display progress after completed.

Use GUI_#3_process_detections.ipynb to read and visualize the inference record.

## Training models

### Train

use train.py

```
python train.py 
--train_dir=PATH_FOR_TRAINING_FILES 
--pipeline_config_path=PATH_OF_CONGIF.config

tensorboard --logdir=PATH_FOR_TRANING_FILES
```

### Evaluate

use eval.py

```
python eval.py --logtostderr 
--checkpoint_dir=PATH_FOR_TRAINING_FILES 
--eval_dir=PATH_FOR_EVAL_FILES 
--pipeline_config_path=PATH_FOR_TRAINING_FILES\pipeline.config

tensorboard --logdir=PATH_FOR_EVAL_FILES
```

In usual, a GPU have no enough memory for both training and evaluation.

You can run eval.py using a CPU version of tensorflow in a seperate virtual environment like Anaconda.

### Export Inference Graph (freeze model checkpoint)

use export_inference_graph.py
```
python export_inference_graph.py 
--input_type=image_tensor 
--pipeline_config_path=PATH_FOR_TRAINING_FILES\pipeline.config 
--trained_checkpoint_prefix=PATH_FOR_TRAINING_FILES\model.ckpt-12345 
--output_directory=PATH_OF_DESTINATION
```
Note that you can compare the eval metrics of checkpoints in Tensorboard before choosing which one to use.










