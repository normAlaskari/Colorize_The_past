Colorizing the Past project
by Fabian Aguilar Gomez, Noor Alaskari, Ivan Rivera
------------------------------------------------------------------------------------------
Required Libraries:
These are the required libraries needed to run the code in no particular order
- python-resize-image: to resize images
- Keras: Layers for the model and create the model
- TensorFlow: Same as Keras
- Skimage: image manipulation
- cv2: same as Skimage
- os: traverse the google directory
- random: standard python random
- sys: no real use imported just incase of use
- PIL: same are cv2 and skimage
- matplotlib: plot images
- google.colab: file access in google drive
-------------------------------------------------------------------------------------------------
Latest TensorFlow version was used as we are assuming the imported tensorflow and keras are the lastest.
--------------------------------------------------------------------------------------------------
Links to datasets used:
Flickr: https://www.kaggle.com/hsankesara/flickr-image-dataset
Japanese Anime Scenes: https://www.kaggle.com/weiwangk/japanese-anime-scenes
Art Images: https://www.kaggle.com/thedownhill/art-images-drawings-painting-sculpture-engraving

--------------------------------------------------------------------------------------------------
Overview:
The code reads in images and resizes the images that will be used to train the model. The images
are stored in a google drive and thus the code requires the dataset to be in the google drive 
for the code to be used. Additionally, after mounting the google drive there must be a folder 
labeled "Train" that contains the dataset that will be used to train the model (e.g. Flickr dataset).
We read the image paths and store them in a path and resize the images. We have a code snipped with 
specific instructions to only run the code once in order to have a file to save the images that will be resized
this can be ignored as we found a better solution to resizing the images just run the cells.
Afterwards, we read the data in the "Train" directory and split it into a training & testing sets. Once the data
is ready to go we create the model. We print both the model summary aswell as a visualization to help see what 
the model is. Then we create a training loop which for this project was only ran for 1000 epochs with a batch size
of 50. This is because Google Colab kept on running out of memory and we could never finish our initial testing parameters
as originally we wanted to test the model running 100,000 epochs and a batch size of 256 buy after 8 hours the model crashed
due to out of memory issues with colab. We then divided the epochs by half after much testing and decreased the batch size and 
kept getting out of memory issues that resulted in us having such a low traning loop epochs and batch size. So moving forward
we definetly don't want to use Google Colab to train our projects as it's just a mess to deal with the whole out of memory issue
and the GPUs. After training we plot some graphs and save the model. Saving the model is new as a way to get around saving it would be 
to load the model prior to training but we didn't think about doing that until the end, and quite honestly it would've been tedious 
as finishing our loop took an average of 3:30 hrs. So it was not feasible to just save the model and load the weights and retrain.
We then create a result directory and load the weights as we came back to the code later to run the model on some images we pulled 
from the internet and converted them to grayscale prior to using them. The results can be found in the "results" folder in this folder.
We then have section to compare legacy black and white images as well as RGB images. For this section we just downloaded random images from
the internet to test it on the Colorful model and our model. The colorful model was ran on our machines and we only saved the image that it produced
to run the Colorful model the GitHub provides instructions on how to do so: https://github.com/richzhang/colorization. So we loaded the image from the
Colorful model and our proposed model with different images and calcualted the percentage of multiple images as we can just change the parameters in the
functions with the images we wish to test. The images shown in the notebook are the lastest images we tested the model on. We then calculate the 
per pixel value difference % between the images and printed them out. 

----------------------------------------------------------------------------------------------------------------------------------------------------------
Organization of the code is seperated for readability in the notebook itself but the sections are as follows:
1. Imports - import the necessary libraries
2. Read the data - Read the data from the google drive
3. Model - create and print the model summary
4. Train - training loop for the model
5. Test the model - test the model on the images in the "Test" directory
6. Compare Results - compare the result to the colorful model.
------------------------------------------------------------------------------------------------------------------------------------------------------------------
How to run:
1. Ensure you are running the code on google colab as we don't know how it would behave anywhere else.
2. Mount google drive
3. Have a "Train", "Test", "output", and "result" directory in your google drive
4. Have the dataset MUST ONLY BE IMAGES NO DIRECTORIES to train the model on the "Train" folder
5. Have the images to colorize in the "Test" folder ONLY IMAGES NO DIRECTORIES
6. Run the code
Optional:
7. Run the Colorful model in a seperate machine to attain the picture
8. Save the picture and read in the compare results cv2.imread that is first
9. Read the same image that is located in the "result" folder
10. Compare results.
------------------------------------------------------------------------------------------------------------------