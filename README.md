# AAD（ Attention-based Adversarial Defense）

This study provides a new understanding of the adversarial attack problem by examining the correlation between adversarial attack and visual attention change. In particular, we observed that: images with incomplete attention regions are more vulnerable to adversarial attacks; and uccessful adversarial attacks lead to deviated and scattered attention map. 
![image](https://github.com/wscjxky/AAD-framework/blob/master/static/head.jpg) 

We hope the attention-related data analysis and defense solution in this study will shed some light on the mechanism behind the adversarial attack and also facilitate future adversarial defense/attack model design.

## Paper
Attention-based Adversarial Defense framework is based on the work presented in [Attention, Please! Adversarial Defense via Attention Rectification and Preservation
](https://arxiv.org/abs/1811.09831) 

## Dependencies
* [Python 3.6+](https://www.continuum.io/downloads)
* [TensorFlow 1.10+](https://www.tensorflow.org/) (optional for tensorboard)


## Usage

### 1. Cloning the repository
```bash
$ git clone https://github.com/wscjxky/ARP.git
$ cd ARP/
$ python -m pip install -r requirements.txt
```

### 2. Downloading the dataset
To download the [cifar10](https://www.kaggle.com/c/cifar-10) dataset:
```bash
$ wget http://www.cs.toronto.edu/~kriz/cifar-10-binary.tar.gz
```

To download the [Imagenet2012](http://www.image-net.org/challenges/LSVRC/2012/) dataset you can download from：
```bash
wget -c (http://www.image-net.org/challenges/LSVRC/2012/nnoupb/ILSVRC2012_img_train.tar) 
wget -c (http://www.image-npet.org/challenges/LSVRC/2012/nnoupb/ILSVRC2012_img_val.tar)
wget -c (http://www.image-net.org/challenges/LSVRC/2012/nnoupb/ILSVRC2012_img_test.tar)
```




### 3. Downloading the pre-training model

#### inception-v3 model

```bash
curl -O http://download.tensorflow.org/models/image/imagenet/inception-v3-2016-03-01.tar.gz
tar xzf inception-v3-2016-03-01.tar.gz
```

####  adv pre-trained models :

Network Architecture | Adversarial training | Checkpoint
---------------------|----------------------|----------------
Inception v3 | Step L.L. | [adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/adv_inception_v3_2017_08_18.tar.gz)
Inception v3 | Step L.L. on ensemble of 3 models | [ens3_adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/ens3_adv_inception_v3_2017_08_18.tar.gz)
Inception v3 | Step L.L. on ensemble of 4 models| [ens4_adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/ens4_adv_inception_v3_2017_08_18.tar.gz)


## Screenshots

Below are some screenshots of lime explanations. These are generated in html, and can be easily produced and embedded in ipython notebooks. We also support visualizations using matplotlib, although they don't look as nice as these ones.



## What are explanations?



## Contributing

Please read [this](CONTRIBUTING.md).
