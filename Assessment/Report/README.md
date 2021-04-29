# Human Facial emotion detection model

Junzhe Gan

## Introduction
The inspiration of this project is from PwC Game-based Assessment. One of their tasks is asking candidates to match human face showing leftwards with correct emotion showing on the right.
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/pwc.png)

This has motivated me to use deep learning techniques building a model which can swiftly detect human facial emotions. This could be used on analysis of audience feeling as the online meeting via zoom and other platform has replaced the traditional face-to-face meeting during the pandemic of covid-19. Through research online, similar technique has been widely applied in retail business. As Vihar suggested, knowing campaign effectiveness through facial behavioural analytics with AI enabled camera on digital signage has enhanced customers’ experience. Facial recognition with deep learning algorithms help retailers to understand different moods and expressions of shoppers in response to various discounts and promotional offers, so they can design better promotional campaigns. Nevertheless, Walmart has also adopted this technology, it classifies facial expressions of customers at checkout lines with AI-based algorithms measuring the service satisfaction index. Moreover, Iva Djukić, a marketing specialist has found that business spokesperson with positive emotions will make their brand more appealing to customers. Thus, it is very essential to use deep learning model to study human emotions. 

## Research Question
Can I build a facial emotion detection model to determine whether the target is happy or sad?

## Application Overview
The project is completed with Edge Impluse and Web cam on smart phone or computer.   

## Data
The data is derived from Kaggle Emotion Detection dataset. The dataset originally have images categorised into seven feelings group, for simplicity, only data showing happy and sad emotions are used. Moreover, 189 pictures containing people with different race, age and gender are carefully selected from thousands of happy images to use as training data for "happy" category and 24 pictures are used as testing data. The same happened for choosing training and test data for "sad". The dataset used is showing below:
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/happy.png)
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/sad.png)
These data was then imported to Edge-impulse with labelled "happy" or "sad". The image data was further squashed to a size of 96 * 96.

## Model
The model is completely build using basic functions on edge impulse. The Transfer Learning block in is selected at create impulse stage as it is recommended for image classification purpose, and the output features will be the two categories, “happy” and “sad”. For the image processing, grayscale is selected to avoid the light issue, followed by the generation of features of 378 training data. As the figure shown below, the “happy” data and “sad” data are quite separated from each other.
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/g.png)




## Experiments
What experiments did you run to test your project? What parameters did you change? How did you measure performance? Did you write any scripts to evaluate performance? Did you use any tools to evaluate performance? Do you have graphs of results? 

*probably ~300 words and graphs and tables are usually good to convey your results!*

## Results and Observations
Synthesis the main results and observations you made from building the project. Did it work perfectly? Why not? What worked and what didn't? Why? What would you do next if you had more time?  

*probably ~300 words and remember images and diagrams bring results to life!*

## Bibliography


1. Iva, Djukić. (July 21, 2020). Using artificial intelligence and emotion recognition for PR City published. 
   available at: https://www.sotrender.com/blog/2020/07/ai-emotion-recognition/

2. Vihar, Soni. (Aug 8, 2020). Facial Recognition in Retail - Enhance In-store Customer experience and Improve Retailer Operations. 
   available at: https://www.einfochips.com/blog/facial-recognition-in-retail-enhance-in-store-customer-experience-and-improve-retailer-operations/

----

## Declaration of Authorship

I, Junzhe Gan, confirm that the work presented in this assessment is my own. Where information has been derived from other sources, I confirm that this has been indicated in the work.


*Junzhe Gan*

29-April-2021

## Appendix
