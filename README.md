# FOTS-Scene-Text-Parsing
This Repository contains implementation of FOTS research paper in Tensor flow  version 2

Here we have shown Model Training, Model Inference, Model Post Training Quantization and Deployment via StreamLit too.
Note := All notebooks given in this repository are from Google Colaboratory.

DataSet used:
1. ICDAR 2015 Dataset :- This dataset includes 1000 training images and 500 testing images. These images are captured by Google glasses without taking care of position.
                         This Dataset is organized as following directory:-<br/>
                         a.ch4_training_images:- This directory contain all 1000 images that we have used for training out text detection branch.<br/>
                         b.ch4_training_localization_transcription_gt:- This directory contains 1000 files of type gt_img_<img_no> which contians coordinate as well as words                                                                         that are present in that particular train image. Some words here are marked as ### to denote Don't                                                                             Care Words in that image.<br/>
                         c.ch4_training_word_images_gt:- This directory contains 4468 word images and 2 files names coords.txt and gt.txt. coords.txt contains coordinate of                                                            exact text in images present in this directory and gt.txt contains particular English word for corresponding image in                                                          this directory.<br/>
                         d.ch4_test_images:- This directory contains 500 test images.<br/>

2. SyntText Dataset :- To Avoid overfitting in Text Recognition Branch because of small set of 4468 images in ICDAR 2015 dataset we have also make use of 130000 images from                          SyntText Dataset
Here we have 2 notebooks:-<br/>
1. FOTS_Scene_Text_Parsing.ipynb<br/>
2. FOTSModelDeployment.ipynb

<b>FOTS_Scene_Text_Parsing.ipynb</b><br/>
This Notebook contains entire Implementation of FOTS Model.




This FOTS Model consists of 3 branches:<br/>
1. Text Detection Branch : - This branch is used to Detect Text regions that are present in our images.In this branch we mainly predict 2 things:<br/><br/>
                             a. Score Map :- These denotes wheter each pixel in input image is text region or not text region.<br/> <br/>
                             b. Geo Map :- It is a 5 channel data. First 4 channels contains distances to top, bottom, left, right sides of the bounding box that contains text                                            region pixel given by score map and last channel contains orientation of bounding box<br/><br/>
2. ROI Rotate: - This branch is used to convert Score Map and Geo Maps given by Text Detection branch to  coordinates of boxes where images are present.<br/><br/>

3. Text Recognition Branch :- This branch is used to convert all Text Regions given by detection and ROI Branch to English words.<br/><br/>

Here we have trained both Text Detection and Text Recognition branch seperately and Finally after Training them have have  created Final Inference pipeline which include all Text Detection branch, Text Recognition branch and ROI Rotate Branch.<br/>


In This Notebook we have also  discussed about Several Post Training Quantization that we have done for out Model and how these Quantization techniques impact on model size, latency of model etc.

<b>FOTS_Scene_Text_Parsing.ipynb</b><br/>
In This Notebook I have written code to make Our Model Deployment by using streamlit in google colaboratory.

References For Code:-<br/>
[1]. https://github.com/Pay20Y/FOTS_TF <br/>
[2]. https://github.com/yu20103983/FOTS <br/>
[3]. https://github.com/Masao-Taketani/FOTS_OCR <br/>
