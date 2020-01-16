# Cervical Cancer Detection from PAP-Test(smear) results using DL
### Overview 
A deep learning framework for cervical cancer classification to allow improved accuracy for PAP smear test 
<table style="border:0px">
   <tr>
       <td><img src="official collage.png" frame=void rules=none></td>
   </tr>
</table>

### Brief Summary
As part of an ETH project a deep learning framework is developed for cervical cancer detection and classification based on microscopics images of cells from PAP smear results. The purpose of this project is to provide another tool for doctors to rapidly detect if a patient has developed or is in danger of developing cervical cancer.It consitutes a rapid tool for detection and prognosis of cervical cancer for female patients. 

### Dataset
The model will be trained on the [Sipakmed](https://www.researchgate.net/figure/The-boundaries-of-the-cytoplasm-and-the-nucleus-of-each-cell-in-images-of-cell-clusters_fig1_327995161) which is a new Dataset for Feature and Image Based Classification of Normal and Pathological Cervical Cells in Pap Smear Images . The dataset can be downloaded [here](http://www.cs.uoi.gr/~marina/sipakmed.html)
The dataset has 5 cervical cell classification categories: 
a) Dyskeratotic 
b) Koilocytotic
c) Metaplastic
e) Parabasal
f) Superficial-Intermediate
As a result this project focuses on a 5 classes categorical classification based on whole slide microscopic cell images (not just cropped cell images, but whole slided)


### Procedure
1. Download the Sipakmed dataset
2. The Sipakmed dataset structure needs to be similar to the structure below.Use the "implementation_DatasetDivision.py" to reform the sipakmed dataset structure to the desired dataset structure, with training_size = 0.6, validation_size=0.2 and testing_size=0.2:

- **Sipakmed Dataset**
  ```
  sipakmed
  ├── train
  │   ├── im_Dyskertotic
  │   ├── im_Koilocytotic 
  │   ├── im_Metaplastic 
  │   ├── im_Parabasal  
  │   └── im_Superficial-Intermediate
  ├── val
  │   ├── im_Dyskertotic
  │   ├── im_Koilocytotic 
  │   ├── im_Metaplastic 
  │   ├── im_Parabasal  
  │   └── im_Superficial-Intermediate
  ├── test
  │   ├── im_Dyskertotic
  │   ├── im_Koilocytotic 
  │   ├── im_Metaplastic 
  │   ├── im_Parabasal  
  │   └── im_Superficial-Intermediate
  └── models
  ```
3. Install the fastai library and all its dependencies, as well as the torch library.

4. To train the Resnet50 pretrained network on the Sipakmed dataset use the "R50.py". Initially specificy in the file, the path to the sipakmed (Formatted) dataset. Then choose appropriate hyperparameters (Epoch = 50 , Batch = 10 , Learning rate = 0.001) and start training.

5. After training is completed the model weights are saved and the whole model is exported.You can specify beforehand in the "R50.py", the path to the storage location to which you want the model weights(.pth) and the whole model(.pkl) to be saved

6. In case you have trained your model up to a certain checkpoint and you save it, you can reload the model weigths by specifying path to the model weights file(.pth)  ---> "model_path" variable in "R50.py"

7. After completing a simple training of the Sipakmed (Formatted) dataset, the results can be further analyzed with the aid of an inference file "Inference_FastAI.py". The inference file will load the model pickle file (.pkl) and will perform classification on any given dataset. It will predict any sample cell microscopic image. The inference file, is set up to evaluate the performance of the model on the testing dataset from the Sipakmed. However it can be carried out on any set of images or single image.The user needs to specify the "test_dataset_path" and the "model_path" with paths to where the testset and the model file are respectively. The inference file will output the accuracy, recall,precision values and the confusion matrix for the various cell categories.

## Further training

The main procedure for training a Resnet50 model on the Sipakmed dataset is described above. Nevertheless for improving results usually further training is requierd and hence the methods of data augmentation, triple transfer learning and feature combinations are used and described below.

**Data Augmentation**

1. For applying data augmentation to the sipakmed dataset, the "implementation_DataAugmentation_Extension.py" file is executed. Specify in the file the target directory path of the sipakmed dataset (or any other dataset you want to apply data augmentation). set the path of the directory through the variable ---> "target_directory"

2. After executing the file, 14 new augmented images will be generated for each image of the Sipakmed dataset. The data augmentations carried out include affine transformations,filter response, color channels tweaking and etc.The generated images are saved automatically in the same location with the original image.

**Triple Transfer Learning**
TTL(Trisple Transfer Learning) means that the mode was trained on the 3 datasets in total. Initially the model is trained on the Extended DA dataset, which is the formatted sipakmed dataset after data augmentation has been carried out (procedure described in the above section). After training of the model is completed, the new weigths are saved in a .pth file. Afterwards the model is trained on the Herlev dataset which is a 


![#f03c15](https://placehold.it/15/f03c15/000000?text=+) 
**In general all python files are detailed with many descriptive and helpful comments that will guide you to any step described in the above procedures**  ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) 
 

