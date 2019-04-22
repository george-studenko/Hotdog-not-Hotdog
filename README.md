# Hotdog not Hotdog image classifier
This my implementation of the famous Hotdog not Hotdog classifier from the Silicon Valley tv show, here is a [1 minute clip](https://www.youtube.com/watch?v=pqTntG1RXSY) to refresh your memory.

## How to run it
### Install requirements
To install the requirements just run   
``` pip install -r requirements.txt```
### The dataset
The image used for training is available to download publicly from kaggle [here](https://www.kaggle.com/dansbecker/hot-dog-not-hot-dog/data).
I modified it slightly to create a validation set, all images are inside the `dataset` folder.  
Each folder `train`, `test` and `valid` will contain 2 classes `0` for *Not Hotdog* and `1` for `Hotdog` each class is inside a folder, feel free to add your own images or delete any images from those folders.
### Dataset labels
The dataset labels are inside the [cat_to_name.json](https://github.com/george-studenko/Hotdog-not-Hotdog/blob/master/cat_to_name.json) file
### Train the model
To train a model you can use either Densenet or Resnet pre-trained models
* To use the ```--gpu``` to enable gpu when training if you have one
* Set the number of epochs to train with the ```--epochs``` parameter
* Set the pretrained network to use with the ```--arch``` parameter
### Train with GPU for 10 epochs using densenet
```python train.py dataset --gpu --epochs 10 --arch densenet```
### Train with GPU for 40 epochs using resnet
```python train.py dataset --gpu --epochs 40 --arch resnet```
### Model Checkpoints
I've included a checkpoint of a model trained with resnet in case you want to start to play with it without having to train it first.
There is a limitation of 100 MB per file on GitHub otherwise I could also include a checkpoint for Densenet, which in my opinion performs better at the moment.
### Inference
To run a prediction or infere if an image is a ```Hotdog``` or a ```Not Hotdog``` I've included some images that are not part of the dataset used previously inside the folder ```predict_img```
Inside that folder I created 2 subfolders, one for each class in order to get the true label printed out, but this is not necesarily a requirement.
### Making a prediction with the default checkpoint

Without GPU and True Label (only images inside the predict_img will print a true label)  
```python predict.py predict_img/0/nh1.jpg```  
  
With GPU and True Label  
```python predict.py predict_img/1/h1.jpg --gpu```  

Without GPU and without true label    
```python predict.py test_img1.jpg```    
```python predict.py test_img2.jpg```    



