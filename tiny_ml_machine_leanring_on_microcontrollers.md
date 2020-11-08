# TinyML: Using Machine Learning on Microcontrollers to Recognize Speech
Shawn Hymel
@shawnhymel
Project page: https://hackaday.io/project/175078-remoticon-tiny-ml

Code: https://github.com/ShawnHymel/ei-keyword-spotting

STM32 demo but he said he had gotten the code to work on an Arduino Uno

TinyML.org is a community for embedded machine learning

Classification, prediction, and decision making with little or no internet connection
Voice activation, object detection, anomaly detection, etc.

Example: Amazon Echo devices are waiting for their keyword entirely locally. They use simple microcontrollers. The more difficult ML work is piped to the cloud.

You can follow the code using the Google Colab link he provides https://colab.research.google.com/github/ShawnHymel/ei-keyword-spotting/blob/master/ei-audio-dataset-curation.ipynb#scrollTo=c06YDTU0c0-H
It's also in the repo

Very interesting - he was experimenting with classifying the audio spectrograms with image recognition techniques with some success. The code we ran however uses the MFCCs.

Used edgeimpulse.com for the actual training which was very cool, it's an online tool where you can push your data and adjust hyperparameters.