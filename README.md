## Deep Speaker: An End-to-End Neural Speaker Embedding System.
Unofficial Keras implementation of Deep Speaker | [Paper](https://arxiv.org/pdf/1705.02304.pdf) | [Pretrained Model](https://drive.google.com/open?id=18h2bmsAWrqoUMsh_FQHDDxp7ioGpcNBa) | [Supplementary](https://youtu.be/HI8MzpY8KMI)

### Sample Results

### Overview

Deep Speaker is a neural speaker embedding system that maps utterances to a hypersphere where speaker similarity is measured by cosine similarity. The embeddings generated by Deep Speaker can be used for many tasks, including speaker identification,
verification, and clustering.

## Getting started
### Install dependencies
#### Requirements
```
pip install -r requirements.txt
```

### Training

To train the models by yourself, you need a computer with at least 32GB of memory and a GPU such as 1080Ti.
```
./deep-speaker download_librispeech
./deep-speaker build_mfcc
./deep-speaker build_model_inputs
./deep-speaker train_softmax
./deep-speaker train_triplet
```

### Test instruction using pretrained model
- Download the trained models
 

 *Model name* | *Used datasets* | *Num speakers* | *Model Link* | 
 | :--- | :--- | :--- | :--- |
ResCNN Softmax trained  | LibriSpeech train-clean-360 | 921 | [Click](https://drive.google.com/open?id=1wCeoa99XfO5r0OX1K5VjJUaCbpvEx9cc)
ResCNN Softmax+Triplet trained  | LibriSpeech all | 2484 | [Click](https://drive.google.com/open?id=1SJBmHpnaW1VcbFWP6JfvbT3wWP9PsqxS)

* Run with pretrained model

``` (with python 3.7)
$ export CUDA_VISIBLE_DEVICES=0; python cli.py test-model --working_dir /home/philippe/ds-test/triplet-training/ --
checkpoint_file ../ds-test/checkpoints-softmax/ResCNN_checkpoint_102.h5
f-measure = 0.789, true positive rate = 0.733, accuracy = 0.996, equal error rate = 0.043
```

```
$ export CUDA_VISIBLE_DEVICES=0; python cli.py test-model --working_dir /home/philippe/ds-test/triplet-training/ --checkpoint_file ../ds-test/checkpoints-triplets/ResCNN_checkpoint_175.h5
f-measure = 0.849, true positive rate = 0.798, accuracy = 0.997, equal error rate = 0.025
```
