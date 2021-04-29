# Human Facial emotion detection model
Junzhe Gan
## Introduction
The inspiration of this project is from PwC Game-based Assessment. One of their tasks is asking candidates to match human face showing leftwards with correct emotion showing on the right.

![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/pwc.png)

This has motivated me to use deep learning techniques building a model which can swiftly detect human facial emotions. This could be used on analysis of audience feeling as the online meeting via zoom and other platform has replaced the traditional face-to-face meeting during the pandemic of covid-19. Through research online, similar technique has been widely applied in retail business. As Vihar suggested, knowing campaign effectiveness through facial behavioural analytics with AI enabled camera on digital signage has enhanced customers’ experience. Facial recognition with deep learning algorithms help retailers to understand different moods and expressions of shoppers in response to various discounts and promotional offers, so they can design better promotional campaigns. Nevertheless, Walmart has also adopted this technology, it classifies facial expressions of customers at checkout lines with AI-based algorithms measuring the service satisfaction index. Moreover, Iva Djukić, a marketing specialist has found that business spokesperson with positive emotions will make their brand more appealing to customers. Thus, it is very essential to use deep learning model to study human emotions. 

## Research Question
Can I build a facial emotion detection model to determine whether the target is happy or sad?

## Application Overview
The project is built through three main steps. The first step is data gathering. The initial data was sourced online with much more content than this project needs. Data selection has been carried out to ensure the image quailty and the general pattern among "happy" and "sad" are distinctive. The second step is imported data into Edge Impulse, which is a very convenient online source for traning and developing deep learning models. The image data was divided into training and testing based on purpose as well as "happy" and "sad" based on properties. The data was then studyed and trained by an pre-trained image classification model. The final model is derived by selecting the best performing model through the inital study and verify with the validation dataset(which just being separated from the training data). With the newly built model, live classification through web cam can be conducted to see how will the model performe with unfamiliar data. After the model studying new image, it will provide its identification of the image, and the output should fall within "happy", "sad", or "unknown". 

![image](https://github.com/JunzheGan/casa0018/blob/main/Assessment/Projects/Final%20Project/Pics/fl.png)

## Data
The data is derived from Kaggle Emotion Detection dataset. The dataset originally have images categorised into seven feelings group, for simplicity, only data showing happy and sad emotions are used. Moreover, 189 pictures containing people with different race, age and gender are carefully selected from thousands of happy images to use as training data for "happy" category and 24 pictures are used as testing data. The same happened for choosing training and test data for "sad". The dataset used is showing below:
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/happy.png)
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/sad.png)
These data was then imported to Edge-impulse with labelled "happy" or "sad". The image data was further squashed to a size of 96 * 96.

## Model
The model is completely build using basic functions on edge impulse. The Transfer Learning block is selected at create impulse stage as it is recommended for image classification purpose, and the output features will be the two categories, “happy” and “sad”. For the image processing, grayscale is selected to avoid the light issue, followed by the generation of features of 378 training data. As the figure shown below, the “happy” data and “sad” data are quite separated from each other.
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/g.png)

When it comes to setup the neural networks, 50 number of training cycles with learning rate at 0.006 are set. The minimum confidence rating is set at 55%. As for the Neural network architecture, MobileNetV2 0.35 with 10 neurons as fianl layer and the dropout rate being set at 0.2 are chosen to ensure performance quality and prevent overfitting.

![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/NNS.png)




## Experiments
Three experiments has been taken out to find the relationship between accuracy, loss rate and parameters about neural networking.
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/0001.png)

For the first set, there are only 20 training cycles with learning rate at 0.001.The minimum confidence rating is kept at 60% as default. The result is not very satisfying since the model's accuracy rate is only 66.3%, with a loss of 0.69.
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/0001_60_01.png)

For the second set, training cycles are increased to 50 and learning rate also rises to 0.006. The minimum confidence rating is decreased to 55% to reduce the "unknown" result.

![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/002.png)  

As expected, the accuracy rate improved significantly to 76.3%, with a loss of 0.98. This proves that increasing learning cycles and learning rate will improve the accuracy of the model. However, this can only be true under the assumption that the model is not overfitting.
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/02.png)

The third test takes exactly the same setting as the second one despite it is the fourth time retraining the model. This explains why there are 9216 features for input layer in test 3 but only 2304 features in test 2.
![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/003.png)

As the result below shows, the ultimate model has the highest accuracy rate (84.2%) and the lowest loss (0.41) among the three. This again proves that increasing learning cycles and rate will generally improve the model accuracy. However, we need to be very caution to avoid the overfitting problem when varying the setting for neural networks.

![image](https://github.com/JunzheGan/Chris_Burger/blob/main/pic/03.png)


## Results and Observations
The final validation result is shown below. The accuray rete for 48 test data is 83.33%, very close to 84.2% induced in the third experiment.

![image](https://github.com/JunzheGan/casa0018/blob/main/Assessment/Report/Pic/Screenshot%202021-04-29%20111832.png)

By looking at the validation results table, one interesting thing is that accuracy rate for detecting "happy" face is higher than detecting "sad" face. The model is more likely to interpret sad emotion as happy as the result suggesting there are 25% chance mis-identify the sad emotion. This could be some sad pictures contain their hands covering the face. The model will interpret hands as abnormal pattern and regard that as happy. Alternatively, some people express their sad feeling by crying. The opened mouth was meant to be crying but the model may accidently recongnise that as laughing. Sometimes, even the eyes will confuse the model. Generally, when people are happy or smiling, their eyes curved like a "n" shape, whereas when they are sad, eyes usually curved like an "u" shape. However, some people eyes are flattened even when they are sad, making the model very hard to decide.

![image](https://github.com/JunzheGan/casa0018/blob/main/Assessment/Report/Pic/im138.png) 
![image](https://github.com/JunzheGan/casa0018/blob/main/Assessment/Report/Pic/im38.png)
![image](https://github.com/JunzheGan/casa0018/blob/main/Assessment/Report/Pic/im91.png)

Since the edge impulse currently does not support deployment to Arducam, the model is tested using webcam on smart phone and laptop. There are two videos, one is using my face as experimental data, the other one is using public photographs on unsplash. The model performs quite well in both senarios. Hence, it is feasible to create a simple facial emotion detection model. 

https://github.com/JunzheGan/casa0018/blob/main/Assessment/Report/Videos/1.mp4
https://github.com/JunzheGan/casa0018/blob/main/Assessment/Report/Videos/2.mp4




## Bibliography


1. Iva, Djukić. (July 21, 2020). Using artificial intelligence and emotion recognition for PR City published. 
   available at: https://www.sotrender.com/blog/2020/07/ai-emotion-recognition/

2. Vihar, Soni. (Aug 8, 2020). Facial Recognition in Retail - Enhance In-store Customer experience and Improve Retailer Operations. 
   available at: https://www.einfochips.com/blog/facial-recognition-in-retail-enhance-in-store-customer-experience-and-improve-retailer-operations/

3. F. Agrafioti, D. Hatzinakos and A. K. Anderson, (March, 2012). "ECG Pattern Analysis for Emotion Detection," in IEEE Transactions on Affective Computing, vol. 3, no. 1, 
   pp.102-115, doi: 10.1109/T-AFFC.2011.28.    


## Declaration of Authorship

I, Junzhe Gan, confirm that the work presented in this assessment is my own. Where information has been derived from other sources, I confirm that this has been indicated in the work.

*Junzhe Gan*

29-April-2021

## Appendix
Edge Impulse Project-the latest public version is version 7, available here: https://studio.edgeimpulse.com/public/21886/latest

The code and data used can all be found at github repository: https://github.com/JunzheGan/casa0018/tree/main/Assessment/Projects/Final%20Project

