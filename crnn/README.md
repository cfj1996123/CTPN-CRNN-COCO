Convolutional Recurrent Neural Network
======================================

Dependence
----------
* pytorch 0.3.0 +
* [warp-ctc](https://github.com/SeanNaren/warp-ctc)

Quick Usage
-----
1. install warp-ctc
2. Download prepared dataset from [Google Drive](https://drive.google.com/file/d/1FLLb22K3uLrfR-lAy3TRoSkvLNXHl_g2/view?usp=sharing)
3. Unzip it on crnn root directory.
4. Run `bash run_train.sh`  or  `python train.py --test-init True --test-epoch 5 --output-dir ./COCO_data_models --data-path cropped_COCO` 

Detailed Usage
-----

`python ./train.py --help`
`



Train on custom dataset
-----------------------

1. Create dataset

- Structure of dataset:
```
<root_dataset_dir>
---- data
-------- <img_filename_0>
...
-------- <img_filename_1>
---- desc.json
```

- Structure of desc.json:
```
{
"abc": <symbols_in_aphabet>,
"train": [
{
"text": <text_on_image>
"name": <img_filename>
},
...
{
"text": <text_on_image>
"name": <img_filename>
}
],
"test": [
{
"text": <text_on_image>
"name": <img_filename>
},
...
{
"text": <text_on_image>
"name": <img_filename>
}
]
}
```

2. Train simple OCR using custom dataset.
```
python train.py --test-init True --test-epoch 10 --output-dir <path_to_folder_with_snapshots> --data-path <path_to_custom_dataset>
```

3. Run test for trained model with visualization mode.
```
python test.py --snapshot <path_to_folder_with_snapshots>/crnn_resnet18_10_best --visualize True --data-path <path_to_custom_dataset>
```
