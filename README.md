# Instagram Image Analysis - Text Analytics (Project II)

Is a Picture Worth a Thousand Words?

![alt text](https://github.com/snithin13/Instagram-Image-Analysis/blob/master/Images/100M_CelebrationPanda%2Bcopy.jpg)

**Image Analytics on National Geographic's (natgeo) instagram page**

## Project Objectives:

1. Use [instaloader](https://instaloader.github.io/index.html) package in python to extract image URLs, post caption, #likes and #comments of the photos posted on natgeo's instagram page. Further, using these image URL's, obtain image labels from Google Vision cloud.
2. Measure engagement of these photos with the followers.
3. Use a model to identify if wwe can predict high or low engagement with just the image labels. Further, see whether the accuracy increases if post captions are also used.
4. Perform topic modeling (LDA) on the image labels and indetify topics that dominate highest and lowest engagement scored pictures
5. Based on inferences, formulate advice for National Geographic if it wants to increase engagement on its Instagram page.

## Contributors:

* Namita Ramesh 
* Karan Palsani 
* Nithin Saseendran 
* Prathik Ullur 
* Rachel Meade

## Approach:

* Used instaloader package in python to extract image URLs, post caption, #likes and #comments. Filtered out the video links.
* To measure engagement, created a metric by using a weighted sum of # likes and # comments. For this, we first normalized # likes and # comments.
* Created an engagement score = .4*# likes (normalized) + .6*# comments (normalized). Defined High (1) and Low (0) engagement based on whether the engagement score is above or below the median value.
* Ran a logistic regression with Engagement (binary) as the dependent variable, and the image labels as independent variables. Obtained an accuracy of 78%. Further, using both caption and labels, we get an improved accuracy of 82%.
* Ran LDA using the bag of words model. Identified number of topics s 4 to be ideal. Obtained the following results:

![alt text](https://github.com/snithin13/Instagram-Image-Analysis/blob/master/Images/insta_lda.JPG)

![alt text](https://github.com/snithin13/Instagram-Image-Analysis/blob/master/Images/insta_top10_lda.JPG "Top-10 words loaded for each topic")

* To measure engagement across different topics, we took the quartiles with highest and lowest engagement scores and measured the differences in the average topic weights of pictures across the two quartiles. Below are the results:

![alt text](https://github.com/snithin13/Instagram-Image-Analysis/blob/master/Images/insta_lda_engagement.JPG)

## Inference and Advice:

Based on the topic modeling findings, if National Geographic wants to increase engagement, they should focus on posting pictures of animals, especially terrestrial animals. The posts which exhibit lower engagement on average are pictures of people, while the posts which exhibit higher engagement on average are posts of animals.

The top ten key words associated with the topic which generated the highest engagement were “wildlife”, “animal”, “plant”, “terrestrial”, “photography”, “vertebrate”, “tree”, “bird”, “elephant”, and “mammal”. Perhaps there is so much content of people on Instagram that National Geographic differentiates itself through pictures of wildlife. This theory is further substantiated by the low engagement for posts that contain either people or more domestic content. The key words in the topic which generated the lowest engagement were “photography”, “fun”, “human”, “people”, “adaptation”, “event”, “dog”, “smile”, “child”, and “room”.

Currently, engagement can be successfully predicted by the content of the captions, suggesting their importance. However, no additional information is gained by including both the photo labels and the captions. This seems to indicate that National Geographic is typically reiterating the content in the photo again in the caption. The company could try some A/B Testing with captions that include other insights related to the picture without reiterating the photo’s content to see if there is an impact on engagement. However, this should be considered a secondary priority, as the effects on engagement are uncertain.

## Code:

https://github.com/snithin13/Instagram-Image-Analysis/blob/master/Instagram%20Natgeo%20Analysis%20Final.ipynb
