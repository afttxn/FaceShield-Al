<h1 align="center">Face Mask Detection using PyTorch</h1>

<h5 align="center">
  A simple Face Mask Detection Model created using PyTorch and OpenCV. 
</h5>

<hr>

## :page_with_curl: Installation

1. Clone the repo
```
$ git clone https://github.com/rakshit087/facemaskDetectorPytorch.git
```
2. Now, cd the cloned repo and install the dependencies by (You can use virtualenv for this purpose)
```
cd /YOUR_PATH/facemaskDetectorPytorch
$ pip3 install -r requirements.txt
```
<hr>

## :computer: Usage

:small_blue_diamond:The faceExtractor can be used to extract face images from pictures. This is what I used to improve my dataset. 
Put your Images in the 'Images' folder and all the Extracted faces will saved in the 'saved' folder after running the app.py

```
$cd /YOUR_PATH/facemaskDetectorPytorch/Face_Extractor 
$python app.py
```
:small_blue_diamond:You can train your own model, but for that first you need your own dataset. The dataset must have the following structure-

```
.Train_Model
├── data                       # your dataset folder
│   ├── train                  # to train your data
│       ├── mask
│       └── no_mask
│   └── test                   # to test your model
│       ├── mask
│       └── no_mask
└── Train_Model.py 
```

After creating the dataset you can train your model by using 'Train_Model.py', after training the model, if you are satisfied by the results you can save the model when asked. The trained model will be saved in the same directory.

```
$cd /YOUR_PATH/facemaskDetectorPytorch/Train_Model 
$python Train_Model.py
```
:small_blue_diamond: You can use a pretrained model with the help of 'faceDetect.py', by default it will load the model I trained. 
```
$cd /YOUR_PATH/facemaskDetectorPytorch/Use_Model 
$python faceDetect.py
```
<hr>

## :file_folder: Dataset Used

I created a custom dataset by mixing images from various sources.
<br>
:small_blue_diamond:<a href = "https://github.com/cabani/MaskedFace-Net">Cabani's Dataset</a> - I used it to get images of people wearing mask<br>
:small_blue_diamond:<a href = "https://www.kaggle.com/ciplab/real-and-fake-face-detection">Real vs Fake Face </a> - I used it to get images of people not wearing a mask.<br>
:small_blue_diamond:I also some some personal images of my friends and family and extracted faces with the help of 'Face_Extractor'

<hr>

## :brain: Model Details

The model used Transfer Learning using MobileNetv2 (The parameters were freezed) as the base and I changed the classifier to - 


<h5 align="center">Linear Layer (input - 1280 | output - 256 | Activation - ReLU)</h5>
<h5 align="center">:arrow_down:</h5>
<h5 align="center">Linear Layer (input - 256 | output - 128 | Activation - ReLU | Dropout = 0.4)</h5>
<h5 align="center">:arrow_down:</h5>
<h5 align="center">Linear Layer (input - 128 | output - 64 | Activation - ReLU)</h5>
<h5 align="center">:arrow_down:</h5>
<h5 align="center">Linear Layer (input - 64 | output - 32 | Activation - ReLU | Dropout = 0.4)</h5>
<h5 align="center">:arrow_down:</h5>
<h5 align="center">Linear Layer (input - 32 | output - 2 | Activation - SoftMax)</h5>
    
<hr>    

## :warning: Issues and Limitations

:small_blue_diamond: The model is having a hard time to detect dark masks, I tried to improve it by adding some dark mask images but somhow, the model started giving false positive to by beard face. :stuck_out_tongue:


 
