# A-Fast-RCNN: Hard Positive Generation via Adversary for Object Detection
By Xiaolong Wang, Abhinav Shrivastava, and Abhinav Gupta

### Introduction

This is a Caffe based version of A-Fast-RCNN ([arxiv_link](https://arxiv.org/pdf/1704.03414.pdf)). Although we originally implement it on torch, this Caffe re-implementation is much simpler, faster and easier to use.

We release the code for training A-Fast-RCNN with Adversarial Spatial Dropout Network.


### License

This code is released under the MIT License (refer to the LICENSE file for details).

### Citing

If you find this useful in your research, please consider citing:

    @inproceedings{WangCVPR17afrcnn,
        Author = {Xiaolong Wang and Abhinav Shrivastava and Abhinav Gupta},
        Title = {A-Fast-RCNN: Hard Positive Generation via Adversary for Object Detection},
        Booktitle = {Conference on Computer Vision and Pattern Recognition ({CVPR})},
        Year = {2017}
    }

### Disclaimer

This implementation is built on a *fork* of the OHEM code ([here](https://github.com/abhi2610/ohem)), which in turn builds on the Faster R-CNN Python code ([here](https://github.com/rbgirshick/py-faster-rcnn)) and Fast R-CNN ([here](https://github.com/rbgirshick/fast-rcnn)). Please cite the appropriate papers depending on which part of the code and/or model you are using.

### Results
    | Approach                       | training data           | test data         | mAP
    | Fast R-CNN  (FRCN)             | VOC 07 trainval         | VOC 07 test       | 67.6
    | FRCN with adversary            | VOC 07 trainval         | VOC 07 test       | 70.8

**Note**: The reported results are based on the VGG16 network.



### Installation
- Step 1:
  Download the selective search data by running script 'data/script/fetch_selective_search_data.sh'.
- Step 2:
  Download the caffemodel by running script 'data/script/fetch_imagenet_models.sh'.
- Step 3:
  Create the link to VOCdevkit.You can find the details from ['data/README.md'](https://github.com/NB-Dragon/A-Fast-RCNN/blob/master/data/README.md).

### Usage

To run the code, one can simply do,
```Shell
./train.sh
```

It includes 3-stage of training:

```Shell
./experiments/scripts/fast_rcnn_std.sh [GPU_ID] VGG16 pascal_voc
./experiments/scripts/fast_rcnn_adv_pretrain.sh [GPU_ID] VGG16 pascal_voc
./copy_model.h
./experiments/scripts/fast_rcnn_adv.sh [GPU_ID] VGG16 pascal_voc
```
All output training files and logs can be downloaded from my [Baidu cloud disk](https://pan.baidu.com/s/1nvac2Jv).
