# ARP（Attention Rectification and Preservation）


This study provides a new understanding of the adversarial attack problem by examining the correlation between adversarial attack and visual attention change. In particular, we observed that: images with incomplete attention regions are more vulnerable to adversarial attacks; and uccessful adversarial attacks lead to deviated and scattered attention map. 

We hope the attention-related data analysis and defense solution in this study will shed some light on the mechanism behind the adversarial attack and also facilitate future adversarial defense/attack model design.

## Paper
ARP is based on the work presented in [Attention, Please! Adversarial Defense via Attention Rectification and Preservation
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
Following pre-trained models are available:

Network Architecture | Adversarial training | Checkpoint
---------------------|----------------------|----------------
Inception v3 | Step L.L. | [adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/adv_inception_v3_2017_08_18.tar.gz)
Inception v3 | Step L.L. on ensemble of 3 models | [ens3_adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/ens3_adv_inception_v3_2017_08_18.tar.gz)
Inception v3 | Step L.L. on ensemble of 4 models| [ens4_adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/ens4_adv_inception_v3_2017_08_18.tar.gz)


## Screenshots

Below are some screenshots of lime explanations. These are generated in html, and can be easily produced and embedded in ipython notebooks. We also support visualizations using matplotlib, although they don't look as nice as these ones.

#### Two class case, text

Negative (blue) words indicate atheism, while positive (orange) words indicate christian. The way to interpret the weights by applying them to the prediction probabilities. For example, if we remove the words Host and NNTP from the document, we expect the classifier to predict atheism with probability 0.58 - 0.14 - 0.11 = 0.31.

![twoclass](doc/images/twoclass.png)

#### Multiclass case

![multiclass](doc/images/multiclass.png)

#### Tabular data

![tabular](doc/images/tabular.png)

#### Images (explaining prediction of 'Cat' in pros and cons)

<img src="https://raw.githubusercontent.com/marcotcr/lime/master/doc/images/images.png" width=200 />

## Tutorials and API

For example usage for text classifiers, take a look at the following two tutorials (generated from ipython notebooks):

- [Basic usage, two class. We explain random forest classifiers.](https://marcotcr.github.io/lime/tutorials/Lime%20-%20basic%20usage%2C%20two%20class%20case.html)
- [Multiclass case](https://marcotcr.github.io/lime/tutorials/Lime%20-%20multiclass.html)

For classifiers that use numerical or categorical data, take a look at the following tutorial (this is newer, so please let me know if you find something wrong):

- [Tabular data](https://marcotcr.github.io/lime/tutorials/Tutorial%20-%20continuous%20and%20categorical%20features.html)
- [Tabular data with H2O models](https://marcotcr.github.io/lime/tutorials/Tutorial_H2O_continuous_and_cat.html)

For image classifiers:

- [Images - basic](https://marcotcr.github.io/lime/tutorials/Tutorial%20-%20images.html)
- [Images - Faces](https://github.com/marcotcr/lime/blob/master/doc/notebooks/Tutorial%20-%20Faces%20and%20GradBoost.ipynb)
- [Images with keras](https://github.com/marcotcr/lime/blob/master/doc/notebooks/Tutorial%20-%20Image%20Classification%20Keras.ipynb)
- [MNIST with random forests](https://github.com/marcotcr/lime/blob/master/doc/notebooks/Tutorial%20-%20MNIST%20and%20RF.ipynb)

For regression:
- [Simple regression](https://marcotcr.github.io/lime/tutorials/Using%2Blime%2Bfor%2Bregression.html)

Submodular Pick :
- [Submodular Pick](https://github.com/marcotcr/lime/tree/master/doc/notebooks/Submodular%20Pick%20examples.ipynb)

The raw (non-html) notebooks for these tutorials are available [here](https://github.com/marcotcr/lime/tree/master/doc/notebooks).

The api reference is available [here](https://lime-ml.readthedocs.io/en/latest/).

## What are explanations?

Intuitively, an explanation is a local linear approximation of the model's behaviour.
While the model may be very complex globally, it is easier to approximate it around the vicinity of a particular instance.
While treating the model as a black box, we perturb the instance we want to explain and learn a sparse linear model around it, as an explanation.
The figure below illustrates the intuition for this procedure. The model's decision function is represented by the blue/pink background, and is clearly nonlinear.
The bright red cross is the instance being explained (let's call it X).
We sample instances around X, and weight them according to their proximity to X (weight here is indicated by size).
We then learn a linear model (dashed line) that approximates the model well in the vicinity of X, but not necessarily globally. For more information, [read our paper](https://arxiv.org/abs/1602.04938), or take a look at [this blog post](https://www.oreilly.com/learning/introduction-to-local-interpretable-model-agnostic-explanations-lime).

<img src="https://raw.githubusercontent.com/marcotcr/lime/master/doc/images/lime.png" width=300px />

## Contributing

Please read [this](CONTRIBUTING.md).
