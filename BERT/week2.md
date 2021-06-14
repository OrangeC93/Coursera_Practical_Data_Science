## Train and Debug a Custom Machine Learning Model
![image](pic/train_debug_custom_ml_model.png)
![image](pic/train_model.png)

## Pre-trained models 
#### pre-trained vs build in
We learned how to use built in algorithms, for example the blazing text algorithm to quickly train a model. The built-in algorithm provided all required code to train the text classifier. We just point the algorithm to the prepared training data.

We'll work with pre trained models. The main difference here is that the model has already been trained on large collections of text data. we will provide the product previous data to adapt the model to your text domain and also provide your custom model training code.
![image](pic/build_in_vs_pre_trained.png)

#### model pre-training and fine tuning
Pre-trained and all key models have been trained on large text corpus such as large book collections or Wikipedia. In this **unsupervised learning** step, the model builds vocabulary of tokens from the training data and learns the vector representations. You can also pre train MLP models on specific language data.

Fine Tuning: we can use those pretrained models and simply adapt them to our specific data set, which is similar with the concept of transfer learning, which has become popular in computer vision. It's a machine learning technique where a model is trained on one task and then repurposed on a second related task.
- For example: If you work with English product reviews as your training data, you can use an English language model, pre trained, for example on Wikipedia and then find unit to the English product reviews. The assumption here is that the majority of words used in the product reviews have been learned already from the English Wikipedia
- Also we can train the model on your **specific NLP task**. In the product reviews example, adding a text classifier layer to the pre trained model that classifies the reviews into positive, neutral and negative sentiment classes.

Fine tuning is generally **faster** than pre training as the model doesn't have to learn millions or billions of BERT vector presentations. Also note that fine tuning is a **supervised learning** step as you fit the model using labeled training data. 

#### Some popular pretrained model
- Such as PyTorch, TensorFlow and Apache mxne have dedicated model where you can find pre trained models.
- The open source NLP project hugging face also provides an extensive model Hub with over 8000 pre trained NLP models. 

#### JumpStart: use SageMaker JumpStart to get easy access to pre trained text and vision models.
- JumpStart works with PyTorch Hub and TensorFlow Hub and lets you deploy supported models in one click into the SageMaker model hosting environment. JumpStart provides access to over a 100 pre trained vision models such as inception V3, ResNet 18 and many more. JumpStart also lists over 30 pre trained text models from PyTorch Hub and TensorFlow Hub, including a variety of BERT models.
-  JumpStart also provides a collection of solutions for popular machine learning use cases, such as for example fraud detection in financial transactions, predictive maintenance, demand, forecasting and prediction and more. When you choose a solution, JumpStart provides a description of the solution and the launch button, there is no extra configuration needed. Solutions launch all of the resources necessary to run the solution including training and model hosting instances. After launching the solution, JumpStart provides a link to a notebook that you can use to explore the solutions features
-  If you don't find a suitable model via a JumpStart, you can also pull in other pre trained models via custom code.

## BERT model pre-training and fine tuning
#### pre-training: unsupervised training, the input data is large collections of unlabeled text
- MLM: The model masks 15 percent of the words in each sentence. BERT then predicts the masked words and corrects itself, meaning it updates the model weights when it predicts incorrectly.
- NSP: BERT randomly chooses 50 percent of the sentence pairs and replaces one of the two sentences with a random sentence from another part of the document. BERT then predicts if the two sentences are a valid sentence pair or not.

#### fine-tuning: supervised training
In the fine-tuning step, we need configure the model for the actual NLP task, such as question and answer, text classification, or a named entity recognition. Fine-tuning is implemented as supervised learning and no masking or next sentence prediction happens. As a result, fine-tuning is very fast and requires a relatively small number of samples or product reviews.
![image](pic/RoBERTa_model.png)


