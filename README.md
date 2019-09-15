## Kaggle APTOS Blindness 2019 Competition

This is a submission for the Kaggle data science competition: [APTOS Blindness 2019](https://www.kaggle.com/c/aptos2019-blindness-detection)

The code can be found in the Jupyter notebook in this repo. This was my first Kaggle competition after spending 6 months studying Fast.ai's video courses.

I'm proud to say that I finished 153rd out of 2943 in the competition, landing in the Top 6% and earning a bronze medal.

![Ranking](https://github.com/DannyMac180/APTOS-Blindness-2019/blob/master/aptos-2019-ranking.png)

# Model

I initially started with a simple Resnet34/50 model but it performed poorly. Than I came upon this relatively new model that was developed by Google in June 2019 called EfficientNet. EfficentNet has outperformed all other Deep Neural Networks on the ImageNet image classification tasks while having a much smaller number of parameters.

![EfficientNet Graph](https://raw.githubusercontent.com/tensorflow/tpu/master/models/official/efficientnet/g3doc/params.png)

