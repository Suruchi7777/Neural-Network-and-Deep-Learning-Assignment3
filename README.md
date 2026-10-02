# CNN Programming Assignment

## Overview

This repository contains my solutions for two CNN programming questions. In the first question, I implemented 2-D convolution from scratch using NumPy. In the second question, I used transfer learning with a pretrained ResNet50 model and compared freezing the model with fine-tuning part of it.

I completed the programs in Python using Google Colab.

## Question 1: Implementing Convolution from Scratch

For this question, I created a 2-D convolution program without using any built-in convolution function. I stored the given input matrix and filter as NumPy arrays and moved the filter across every valid part of the input matrix.

At each position, the program multiplies the filter and the selected input region element by element. It then adds the results to produce one value in the output feature map.

The program uses:

- A `5 x 5` input matrix
- A `3 x 3` filter
- Stride of `1`
- Padding of `0`

The output feature map is:

```text
[[4 3 4]
 [2 4 3]
 [2 3 4]]
```

The output shape is:

```text
(3, 3)
```

I also examined what happens when the stride changes from `1` to `2`. With stride `2`, the filter moves two positions at a time, so it checks fewer regions of the input. Because of this, the output shape becomes `(2, 2)`.

## Question 2: Transfer Learning — Freeze vs. Fine-Tune

For this question, I used a pretrained ResNet50 model to classify cats and dogs from the CIFAR-10 dataset. I completed two experiments to compare feature extraction and fine-tuning.

### Experiment A: Frozen Feature Extractor

In the first experiment, I loaded ResNet50 with weights learned from ImageNet and removed its original classification layer. I froze the convolutional base so that its pretrained weights would not change. I then added and trained a new binary classifier for the cat-and-dog dataset.

### Experiment B: Fine-Tuned Network

In the second experiment, I started with the model weights learned during Experiment A. I kept the earlier ResNet50 layers frozen but unfroze the final convolutional block. This allowed the final block and the new classifier to adjust their weights for the cat-and-dog classification task.

I used a small learning rate during fine-tuning so that the model would not make large changes to the useful features it had already learned. I also kept the Batch Normalization layers frozen to make training more stable.

For a fair comparison, I used the same dataset, image size, batch size, and number of epochs in both experiments. For each model, I recorded:

- Number of trainable parameters
- Training time
- Test accuracy
- Training loss

## Results

The final results from the notebook can be added to the following table:

| Method | Trainable Parameters | Training Time (seconds) | Test Accuracy |
|---|---:|---:|---:|
| Frozen Feature Extractor | Add result | Add result | Add result |
| Fine-Tuned Network | Add result | Add result | Add result |

The notebook also includes graphs of the training and validation losses for both experiments.

## What I Learned

The frozen feature extractor has fewer trainable parameters because it only updates the new classification layer. This usually makes it faster to train and can help prevent overfitting when the dataset is small. The fine-tuned network takes longer because it updates both the classifier and the last convolutional block. However, fine-tuning can improve accuracy because the higher-level features can adapt to the new dataset. Its performance depends on factors such as the learning rate, number of epochs, and amount of training data.

## Technologies and Libraries Used

- Python
- Google Colab
- NumPy
- Pandas
- Matplotlib
- TensorFlow 2.20.0
- Keras
- ResNet50
- CIFAR-10

## How to Run the Notebook

1. Open the notebook in Google Colab.
2. Go to **Runtime > Change runtime type**.
3. Select a GPU if one is available.
4. Run the cells in order from top to bottom.
5. Allow the CIFAR-10 dataset and pretrained ResNet50 weights to download.
6. Review the final comparison table and loss graphs.

## Repository Contents

```text
.
├── README.md
└── assignment_notebook.ipynb
```

The notebook file contains the complete code, results, comparison table, and loss plots for both questions.
