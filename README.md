## Intro

Mask R-CNN is a deep learning model for computer vision developed by the Facebook AI group that achieves state-of-the-art results on semantic segmentation (object recognition and pixel labeling) tasks. An implementation of the model is made available by Matterport on their [github page](github.com/matterport). The code in their repo works with MS Coco (a benchmark dataset for semantic segmentation) out of the box, but provides for easy extensibility to any kind of dataset or image segmentation task.

![Instance Segmentation Sample](assets/street.png)

This is a fork of the [matterport/mask_rcnn repo](github.com/matterport/mask-rcnn) that we have set up to integrate with Weights and Biases (wandb). wandb is a cloud interface for tracking model parameters and performance, allowing machine learning teams to coordinate work in a way similar to github. [Here](https://app.wandb.ai/trentwatson1/mask-rcnn) are the results of our runs. For a more detailed overview of our process and results see our [blog post](https://medium.com/@connorandtrent/mask-r-cnn-hyperparameter-experiments-with-weights-and-biases-bd2319faae26).

## Setup

We have also streamlined the setup process of the original repo to get it up and running quickly on the tensorflow_p36 environment of the AWS Deep Learning AMI (Ubuntu) Version 10.0. To do so, start up an instance with at least 100 GB of storage, ssh into it, and do:

1. `source activate tensorflow_p36`
2. `git clone https://github.com/connorhough/mask_rcnn`
3. `cd mask_rcnn`
4. `pip install cython`
5. `pip install -r requirements.txt`
6. `pip install tensorflow-gpu==1.7.0`
7. `python setup.py install`
8. `wandb init`, then follow the init steps
9. `wandb run samples/coco/coco.py train --model=imagenet --dataset=../coco --download=True`

After the first run, use the above command without the `--download=True` argument

The parameter sweep can be run with `./sweep.sh`
