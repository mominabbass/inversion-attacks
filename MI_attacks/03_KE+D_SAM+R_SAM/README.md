# Enhancing Inversion Attacks via Sharpness-Aware Minimization
##### Course Project: CSCI 4962/6962 Security and Privacy of Machine Learning (Spring-2024) 
##### Instructor: [Prof. Lei Yu](https://leiyucs.github.io/)
###### Group: [Momin Abbas](https://mominabbas.github.io/)
Language: Python
API: Pytorch


## Requirement
This code has been tested with Python 3.9.15, PyTorch 1.13.1 and cuda 11.4.

## Getting Started
* Install the necessary packages.
* Download relevant datasets including Celeba, MNIST, CIFAR10.
* Get target model prepared or run our code
    `python train_classifier.py` <br>
    Please note that this script offers three model architectures only: VGG16, IR152, and Facenet. Pretrained checkpoints for these models are available for download at: https://drive.google.com/drive/folders/1U4gekn72UX_n1pHdm9GQUQwwYVDvpTfN?usp=sharing.

## Stage-1: Build a inversion-specific GAN via Sharpness-Aware Minimziation
* Modify the configuration in 'celeba.json'.
* Update the target model path in 'k+1_gan.py' to reflect your custom location.
* Execute the command:
    `python k+1_gan.py`.
* The model checkpoints and generated image results will be stored in the 'improvedGAN' directory.


## Stage-2: Distributional Recovery via Sharpness-Aware Minimziation
Execute the following command:
    `python recovery.py`
    
* `--model` selects the target model to attack.
* `--improved_flag` specifies whether an inversion-specific GAN is utilized. If set to False, a general GAN will be employed.
* `--dist_flag` determines if distributional recovery is conducted. If set to False, optimization is applied solely on a single sample instead of a distribution.
* By setting both `improved_flag` and `dist_flag` be False, we are simply using the method proposed in [[1]](#1).

## Reference
<a id="1">[1]</a> 
Zhang, Yuheng, et al. "The secret revealer: Generative model-inversion attacks against deep neural networks." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2020.


