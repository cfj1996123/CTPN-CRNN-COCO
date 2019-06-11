


***
# setup
- requirements: tensorflow1.3, cython0.24, opencv-python, easydict,(recommend to install Anaconda)
- build the library
```shell
cd lib/utils
chmod +x make.sh
./make.sh
```
***

# Quick Start
1. Install the dependencies
2. Download pretrained VGG model from [Google Drive](https://drive.google.com/file/d/15Plf9lWSlF7z0ZayOdEZJgKj9Sc3ndfs/view?usp=sharing), and put it into ./data/pretrain
3. Download the COCO data we prepared from [Google Drive](https://drive.google.com/file/d/1Bv20FApfheQGVI8g-21H3J4v5GvrmNTP/view?usp=sharing)
4. Simply run `python ./ctpn/train_net.py` in the same directory as this markdown file.
- you can modify some hyper parameters in ctpn/text.yml, or just used the parameters I set.

# parameters
there are some parameters you may need to modify according to your requirement, you can find them in ctpn/text.yml
- USE_GPU_NMS # whether to use nms implemented in cuda,if you do not have a gpu device,follow here to [setup](https://github.com/eragonruan/text-detection-ctpn/issues/43)
- DETECT_MODE # H represents horizontal mode, O represents oriented mode, default is H
***

# demo
put your images in data/demo, the results will be saved in data/results, and run demo in the root 
```shell
python ./ctpn/demo.py
```
***
# training
- to prepare your own dataset to train, first prepare dataset as stated in the paper.
```shell
cd prepare_training_data
python split_label.py
```
- it will generate the prepared data in current folder, and then run
```shell
python ToVoc.py
```
- to convert the prepared training data into voc format. It will generate a folder named TEXTVOC. move this folder to data/ and then run
```shell
cd ../data
ln -s TEXTVOC VOCdevkit2007
```
