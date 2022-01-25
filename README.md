# Severless-Image-Classifier
E2E Deep Learning: Serverless Image Classifier
A Personal Data Science Capstone Project (inspired by Jovian.ai).

Build an end-to-end deep learning model to classify real-world clothes images using TensorFlow, TensorFlow Lite, Docker, and AWS Lambda with API Gateway.

Author:Derek Kweku Degbedzui
Email: derekjr560@gmail.com
Social Media: LinkedIn, Twitter

Project Summary
Imagine we need to deal with lots of real-world clothes images and your responsibility is to create an automated image classifier for an e-commerce company. As a result, the challenge is not only to build a robust deep learning model, but also to deploy it as a serverless app. We can combine the AWS Lambda and API Gateway for hosting this serverless APIs.

In this project, we will learn together how to:

train a deep learning model to classify images using TensorFlow.
convert the model into a more size-efficient format using TensorFlow Lite.
deploy the model locally on our machine using Docker.
deploy the model as a REST API using AWS Lambda and API Gateway.
Datasets
The dataset contains 3781 clothes images with the top 10 most popular categories, divided into the train, test, and validation sets. We can access the data here.

Label	Dataset Size	Train Size	Test Size	Validation Size
dress	288	241	15	32
hat	149	123	12	14
longsleeve	576	455	72	49
outwear	246	184	38	24
pants	559	468	42	49
shirt	345	290	26	29
shoes	297	198	73	26
shorts	257	202	30	25
skirt	136	112	12	12
t-shirt	928	795	52	81
TOTAL	3781	3068	372	341
The image samples from each class are shown below:



The Proposed Deep Learning Model
We will build a deep learning model using the transfer learning method and image augmentation to achieve a good performance and prevent overfitting. The pre-trained model we use is InceptionV3, but feel free to experiment with another model as well.

You can see the process in 1_Model_Training.ipynb

The sample result of an image being augmented is shown below.


Model training:

Classification accuracy on test dataset: 90.59%
Gap accuracy between test and training dataset: 3.04% (test acc > training acc)
Test loss: 0.273
Avoid overvitting: YES

Test the Model:



Model Conversion with TensorFlow Lite
After we build the model using TensorFlow, we will soon notice that the file size is too large and not optimized for deployment, especially on mobile or edge devices. This is where TensorFlow Lite (TFLite) comes into play. TFLite will help us convert the model to a more efficient format in .tflite. This will generate a small binary-sized model that is lightweight, low-latency and having a minor impact on accuracy.

You can see the process in 2_Model_Conversion.ipynb

Model Deployment
In this final step, we will deploy the model using Docker, AWS Lambda, and AWS API Gateway. You can see the process in 3_Model_Deployment.ipynb

Deploy on Local Machine with Docker
Here are the screenshots of running the model locally with Docker:  

Deploy on AWS Lambda and API Gateway
The URL to make an HTTP API call: https://xw2bv0y8mb.execute-api.us-east-1.amazonaws.com/test/predict
Image data to be sent as a POST request:
{
    "url": "https://tinyurl.com/clothes-t-shirt"
}
To make a prediction, we can use Postman app, Reqbin, or via terminal (i.e. Git Bash):


$ curl -d '{"url": "https://tinyurl.com/clothes-t-shirt"}' \
-H "Content-Type: application/json" -X POST \
https://xw2bv0y8mb.execute-api.us-east-1.amazonaws.com/test/predict


Conclusion
Conducting an end-to-end deep learning project can be challenging due to the many procedures to follow. However, thanks to the rich features of TensorFlow, we can build and deploy the model with ease. The presence of services such as Docker and AWS helps data scientists to quickly deliver the app either offline or online to solve business problems.

Using the serverless clothes image classifier as an example, I hope this project gives you a basic idea of how to deal with a similar case in the future. Keep inspiring!

Thank you,

Derek Kweku
