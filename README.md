# AutoAlbument

AutoAlbument is an AutoML tool that learns image augmentation policies from data using the [Faster AutoAugment algorithm](https://arxiv.org/abs/1911.06987). It relieves the user from the burden of manually selecting augmentations and tuning their parameters. AutoAlbument provides a complete ready-to-use configuration for an augmentation pipeline.

The library supports image classification and semantic segmentation tasks. You can use [Albumentations](https://github.com/albumentations-team/albumentations) to utilize policies discovered by AutoAlbument in your computer vision pipelines.

The documentation is available at [https://albumentations.ai/docs/autoalbument/](https://albumentations.ai/docs/autoalbument/)

## Benchmarks

Here is a comparison between a baseline augmentation strategy and an augmentation policy discovered by AutoAlbument
for different classification and semantic segmentation tasks. You can read more about these benchmarks in the [autoalbument-benchmarks](https://github.com/albumentations-team/autoalbument-benchmarks) repository.

### Classification
| Dataset  | Baseline Top-1 Accuracy | AutoAlbument Top-1 Accuracy  |
|----------|:-----------------------:|:----------------------------:|
| [CIFAR10](https://github.com/albumentations-team/autoalbument-benchmarks#cifar-10-classification)  |          91.79          |           **96.02**          |
| [SVHN](https://github.com/albumentations-team/autoalbument-benchmarks#svhn-classification)     |          98.31          |           **98.48**          |
| [ImageNet](https://github.com/albumentations-team/autoalbument-benchmarks#imagenet-classification) |          73.27          |           **75.17**          |


### Semantic segmentation
| Dataset    | Baseline mIOU | AutoAlbument mIOU |
|------------|:-------------:|:-----------------:|
| [Pascal VOC](https://github.com/albumentations-team/autoalbument-benchmarks#pascal-voc-semantic-segmentation) |     73.34     |     **75.55**     |
| [Cityscapes](https://github.com/albumentations-team/autoalbument-benchmarks#cityscapes) |     79.47     |     **79.92**     |


## Installation
AutoAlbument requires Python 3.6 or higher. To install the latest stable version from PyPI:

`pip install -U autoalbument`

## How to use AutoAlbument

![How to use AutoAlbument](https://albumentations.ai/docs/images/autoalbument/how_to_use/autoalbument_usage.png)

1. You need to create a configuration file with AutoAlbument parameters and a Python file that implements a custom PyTorch Dataset for your data. Next, you need to pass those files to AutoAlbument.
2. AutoAlbument will use Generative Adversarial Network to discover augmentation policies and then create a file containing those policies.
3. Finally, you can use [Albumentations](https://github.com/albumentations-team/albumentations) to load augmentation policies from the file and utilize them in your computer vision pipelines.

You can read the detailed description of all steps at [https://albumentations.ai/docs/autoalbument/how_to_use/](https://albumentations.ai/docs/autoalbument/how_to_use/)

## Examples
The [`examples`](https://github.com/albumentations-team/autoalbument/tree/master/examples) directory contains example configs for different tasks and datasets:

### Classification
- [CIFAR10](https://github.com/albumentations-team/autoalbument/tree/master/examples/cifar10)
- [SVHN](https://github.com/albumentations-team/autoalbument/tree/master/examples/svhn)
- [ImageNet](https://github.com/albumentations-team/autoalbument/tree/master/examples/imagenet)

### Semantic segmentation
- [Pascal VOC](https://github.com/albumentations-team/autoalbument/tree/master/examples/pascal_voc)
- [Cityscapes](https://github.com/albumentations-team/autoalbument/tree/master/examples/cityscapes)

To run the search with an example config:

```
autoalbument-search --config-dir </path/to/directory_with_dataset.py_and_search.yaml>
```
