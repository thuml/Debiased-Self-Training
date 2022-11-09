# Debiased-Self-Training-for-Semi-Supervised-Learning

Code release of paper Debiased Self-Training for Semi-supervised Learning ([NeurIPS 2022 Oral](https://arxiv.org/abs/2202.07136)).

- [Introduction](#introduction)
- [Updates](#updates)
- [Installation](#installation)
- [Experiments](#experiments)
- [Contact](#contact)
- [Citation](#citation)
- [Acknowledgments](#acknowledgments)

## Introduction

Our method, Debiased Self-Training (DST), tackles the bias issue in self-training. It can serve as a general add-on to existing methods and boost their performance (for example, **18.9% improvement over FixMatch**). Besides, DST can be implemented in only several lines of code and introduce marginal computation overhead during training, and no overhead during inference. The main components of DST are briefly explained below. For details, please refer to our paper. 

####	Decoupled Pseudo Labeling

![arch](fig/arch.png)

One of the main issues in self-training is the so-called confirmation bias, where the model fails to correct its own mistakes due to error accumulation. Our experiments suggest that **the backbone of deep neural networks has better tolerance to noisy pseudo labels than the classifier head**. Based on this observation, we propose to introduce a complete parameter-independent pseudo head (shown in subfigure (d)) to take the duty of training with pseudo labels. In this way, we **decouple the generation and utilization of pseudo labels**.

#### Worst Case Estimation

![arch](fig/worst_case.png)

We further propose a worst-case estimation to improve the feature representation. This is achieved by introducing another worst-case head (different from the above-mentioned pseudo head) and a minimax game between the feature extractor and the worst-case head. We illustrate the idea of this process in the above figure.

- **(a)** Shift between the hyperplanes learned on limited labeled data and the true hyperplanes.
- **(b)** The worst hyperplanes are hyperplanes that correctly distinguish labeled samples while making as many mistakes as possible on unlabeled samples.
- **(c)** Feature representations are optimized to improve the performance of the worst hyperplanes.

## Updates

#### 2022.11

Code release.

## Installation

Our code is based on [Transfer Learning Library](https://github.com/thuml/Transfer-Learning-Library#introduction), please install it before usage. We evaluate DST when training from scratch and fine-tuning from different pre-trained models. Currently, we maintain our code in two different folders.

- [Code of fine-tuning experiments](https://github.com/thuml/Transfer-Learning-Library/tree/master/examples/semi_supervised_learning/image_classification)
- [Code of training-from-scratch experiments](https://github.com/thuml/Transfer-Learning-Library/tree/dev-ssl/projects/dst)

Further instructions and requirements can be found in these folders. We also provide the implementation of baseline methods.

## Experiments

We provide the benchmark results and optimal hyper-parameters for all experiments, which can be found in the above links, respectively.

## Contact

If you have any questions or want to use the code, please contact

- Baixu Chen (cbx_99_hasta@outlook.com)
- Junguang Jiang (JiangJunguang1123@outlook.com)

## Citation

If you find this code useful, please cite our paper.

```
@article{DST,
    title={Debiased Self-Training for Semi-Supervised Learning},
    author={Chen, Baixu and Jiang, Junguang and Wang, Ximei and Wang, Jianmin and Long, Mingsheng},
    journal={arXiv preprint arXiv:2202.07136},
    year={2022}
}
```

## Acknowledgments

We appreciate the following github repos for their valuable codebase:
- https://github.com/xternalz/WideResNet-pytorch
- https://github.com/kekmodel/FixMatch-pytorch
- https://github.com/TorchSSL/TorchSSL

