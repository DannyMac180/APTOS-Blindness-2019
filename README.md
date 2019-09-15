## Kaggle APTOS Blindness 2019 Competition

This is a submission for the Kaggle data science competition: [APTOS Blindness 2019](https://www.kaggle.com/c/aptos2019-blindness-detection)

The code can be found in the Jupyter notebook in this repo. This was my first Kaggle competition after spending 6 months studying Fast.ai's video courses.

I'm proud to say that I finished 153rd out of 2943 in the competition, landing in the Top 6% and earning a bronze medal.

![Ranking](https://github.com/DannyMac180/APTOS-Blindness-2019/blob/master/aptos-2019-ranking.png)

# Model

I initially started with a simple Resnet34/50 model but it performed poorly. Than I came upon this relatively new model that was developed by Google in June 2019 called EfficientNet. EfficentNet has outperformed all other Deep Neural Networks on the ImageNet image classification tasks while having a much smaller number of parameters.

![EfficientNet Graph](https://raw.githubusercontent.com/tensorflow/tpu/master/models/official/efficientnet/g3doc/params.png)

I scaled up the B6 version of the model, but had to use a very small batch size so the Kaggle GPU didn't run out of memory during training. I found a balance in the end between the more powerful model and speed/efficiency by using EfficientNetB6.

# Training

I used a pretrained EfficientNetB6 model. I then trained it for 16 epochs on data from a previous APTOS Blindness competition in 2015. There was a larger amount of training data from that competition, about 30,000 images in total. After pretraining I used the current competitions data to once more fine tune the model. This is the transfer learning method I learned from watching Jeremy Howard's Fast.ai courses.

One more trick I used was data resizing. I used a few different image sizes in order to create more training data to increase performance. I started out with 128 x 128 pixel images, then 256 X 256 and finally 528 x 528.

# Results

The scoring statistic for this competition was Quadratic Weighted Kappa - defined by this equation:

Cohen's kappa measures the agreement between two raters who each classify N items into C mutually exclusive categories. The definition of {\textstyle \kappa }{\textstyle \kappa } is:

{\displaystyle \kappa \equiv {\frac {p_{o}-p_{e}}{1-p_{e}}}=1-{\frac {1-p_{o}}{1-p_{e}}},\!}{\displaystyle \kappa \equiv {\frac {p_{o}-p_{e}}{1-p_{e}}}=1-{\frac {1-p_{o}}{1-p_{e}}},\!}
where po is the relative observed agreement among raters (identical to accuracy), and pe is the hypothetical probability of chance agreement, using the observed data to calculate the probabilities of each observer randomly seeing each category. If the raters are in complete agreement then {\textstyle \kappa =1}{\textstyle \kappa =1}. If there is no agreement among the raters other than what would be expected by chance (as given by pe), {\textstyle \kappa =0}{\textstyle \kappa =0}. It is possible for the statistic to be negative,[6] which implies that there is no effective agreement between the two raters or the agreement is worse than random.

My final submission achieved a QWK score of 

