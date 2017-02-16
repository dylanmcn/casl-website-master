---
layout: post
title: Coral Classification
subtitle: By Nick Cortale
root: {{site.baseurl}}
---


Here we explore tensorflow (a python package for neural nets) as a way to classify a benthic photomosiac into two categories: Group 1 (coral, algae, etc...a total of 45 species) or Group 2 (sand, cca, etc...). In the future, this analysis will be expanded to multiple classes (species).

To do this, we chunk up a 10,000 x 10,000 pixel photomosaic from FR13 into 40,000 randomly sampled, 64 x 64 images. An example of the raw mosaic, the hand classified mosaic, and 20 64x64 images are shown below. The top row of the 64 x 64 images are Group 1 (0) and the bottom is Group 2 (1).

![fr 13]({{ site.url }}/assets/coral/fr13.png){: .center-image }

![fr 13]({{ site.url }}/assets/coral/fr13_sub.png){: .center-image }


The model was trained for 9 hours before the error leveled off. At this point the model had achieved 99% accuracy on the training set. To make sure that the model had not simply memorized all the training images, we tested the model on different locations.

## Palmyra - FR 14

The first test was another region from Palmyra, FR 14. The photomosaic, classified mosaic, and 64 x 64 sub images are shown below.

![fr 14]({{ site.url }}/assets/coral/fr14.png)

![fr 14]({{ site.url }}/assets/coral/fr14_sub.png)

Even with massive differences in the white balances between the two zones, the model was still able to achieve an accuracy of 93.5%. The testing set was 40,000 64 x 64 subsampled images.

## Kiribati - KIR B1

Next we checked out kiribati.

![kir b1]({{ site.url }}/assets/coral/kir_b1.png)

![kir b1]({{ site.url }}/assets/coral/kir_b1_sub.png)

The model was not able to generalize to this zone. Most likely because it had never seen sand before and this kind of algae. The model achieved an accuary of only 9.7%. Either we must include Kiribati in the training set or maybe train a different model to classify kiribati. More generally, each island might need its own fine tuned model instead of one model that can classify all regions.

## Fanning - FAN B6

Next we checked out fanning island.

![fan b6]({{ site.url }}/assets/coral/fan_b6.png)

![fan b6]({{ site.url }}/assets/coral/fan_b6_sub.png)

The model was able to achieve 90.3% accuracy on this region. This is encouraging as it was a different island and was able to achieve more than 90% accuracy.

## Summary

We trained a convolutional neural network on 64 x 64 sub-sampled regions of FR13 and attempted to classify them as either Group 1 (coral, algae, etc.) or Group 2 (dead coral, sand, etc.). We then took our trained model and attempted to classify other zones. The accuracy is shown in the table below. The accuracy for FR 13 is on out of sample images that the model had never seen before.

| Zone    | Accuracy |
|---------|----------|
| KIR B1  | 9.7%     |
| KIR B5  | 39.9%    |
| FAN B6  | 90.3%    |
| FR 4    | 96.3%    |
| FR 13   | 98.5%    |
| FR 14   | 93.5     |

The results here are very encouraging. To improve the accuracy of Kiribati, we will include training images from the zone, or we will train an entirely seperate model. Future experiments will determine which is better.

[kaggle-site]: https://www.kaggle.com/
[kaggle-ml]:   https://www.kaggle.com/c/march-machine-learning-mania-2016
[pandas]: http://pandas.pydata.org/
[rpi-wiki]: https://www.wikiwand.com/en/Rating_Percentage_Index
[ml-paper1]: http://arxiv.org/abs/1310.3607
[alex-nn]: https://github.com/SkidanovAlex/march-ml-mania-2015
[my-github]: https://github.com/NickC1/kaggle_ncaa_2016
