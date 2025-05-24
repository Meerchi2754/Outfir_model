# 𝑶𝒖𝒕𝒇𝒊𝒕_𝒎𝒐𝒅𝒆𝒍
This model is designed to classify images of people based on their subject ID using a pre-trained convolutional neural network (MobileNetV2) and a custom classification layer. It's trained to distinguish between different individuals based on their facial features or appearance in the provided image dataset. 

𝐇𝐞𝐫𝐞, 𝐢𝐬 𝐭𝐡𝐞 𝐬𝐮𝐦𝐦𝐚𝐫𝐲 𝐨𝐟 𝐭𝐡𝐢𝐬 𝐦𝐨𝐝𝐞𝐥::

1. 𝑫𝒂𝒕𝒂 𝑳𝒐𝒂𝒅𝒊𝒏𝒈 𝒂𝒏𝒅 𝑷𝒓𝒆𝒑𝒓𝒐𝒄𝒆𝒔𝒔𝒊𝒏𝒈:
  The Dataset contains several images of  object in different location, different size. 
  It loads image details from CSV files.
  It loads subject and image ID relationships.
  It attempts to load and preprocess images from a local directory.
  It reads skin tone data from another CSV file and merges it with the image details.
  Images are loaded, resized, and normalized.
  Subject IDs are encoded into numerical labels and then converted into a one-hot encoded format.


2. 𝑴𝒐𝒅𝒆𝒍 𝑨𝒓𝒄𝒉𝒊𝒕𝒆𝒄𝒕𝒖𝒓𝒆:

    It uses a 𝐩𝐫𝐞-𝐭𝐫𝐚𝐢𝐧𝐞𝐝 𝐌𝐨𝐛𝐢𝐥𝐞𝐍𝐞𝐭𝐕𝟐 model as the base.
    The weights of the MobileNetV2 base are frozen, meaning they won't be updated during training.
    A custom classification head is added on top of the MobileNetV2 output, consisting of a Flatten layer, a Dense layer with ReLU activation, a Dropout layer for regularization, and a final Dense layer with softmax activation for classification.
    The number of units in the final Dense layer is set to the number of unique subject IDs (which is 19 based on the print statement).

3. 𝑴𝒐𝒅𝒆𝒍 𝑻𝒓𝒂𝒊𝒏𝒊𝒏𝒈:

  The model is compiled using the Adam optimizer, categorical cross-entropy loss, and accuracy as a metric.
  The dataset is split into training and testing sets.
  The model is trained on the training data for 10 epochs, with validation on the testing data.
  
4. 𝑴𝒐𝒅𝒆𝒍 𝑬𝒗𝒂𝒍𝒖𝒂𝒕𝒊𝒐𝒏:
  
  The model's performance is evaluated on the test set to report the final loss and accuracy.
  Training history (accuracy and validation accuracy) is plotted to visualize the training progress.
  
5. 𝑴𝒐𝒅𝒆𝒍 𝑻𝒆𝒔𝒕𝒊𝒏𝒈 (𝑷𝒓𝒆𝒅𝒊𝒄𝒕𝒊𝒐𝒏):

  A function predict_subject is defined to take an image path, the trained model, and the label encoder as input.
  It preprocesses the input image.
  It uses the trained model to predict the subject based on the image.
  It converts the predicted class index back to the subject ID using the label_encoder.
  It attempts to retrieve the subject ID from the df DataFrame based on the predicted subject name, although there's a potential issue if the predicted subject name from the model doesn't exactly match the 'subject_name' in the DataFrame.

In essence, this model is designed to classify images of people based on their subject ID using a pre-trained convolutional neural network (MobileNetV2) and a custom classification layer. It's trained to distinguish between different individuals based on their facial features or appearance in the provided image dataset. The ultimate goal, as indicated by the markdown cells, seems to be part of an "Outfit Matcher: AI Classified Skin Tone and Outfit Recommender," where this model potentially serves as a step to identify the person in the image, which could then be used to infer their skin tone for outfit recommendations.


Here, is the accuracy graph and Epoch:
![Image](https://github.com/user-attachments/assets/dcd67ff4-23f9-44bb-ac13-af3479f5132c)

Here, is the visualization of Model:
![Image](https://github.com/user-attachments/assets/d430bce6-28bb-4af9-9fef-a79f8a7b33ea)
