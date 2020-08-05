# MaskTheFace - Convert face dataset to masked dataset
![cover_photo](images/MaskTheFace.png)
## What is MaskTheFace?
MaskTheFace is computer vision based scripts to mask faces in images.
It provides a number of masks to select from. It is difficult to collect mask dataset under various conditions. MaskTheFace can be used to convert any existing face dataset to masked-face dataset.
MaskTheFace identifies all the faces within an image, and applies the user selected masks to them taking into account various limitations such as face angle, mask fit, lighting conditions etc.  
A single image, or entire directory of images can be used as input to code.
![cover_photo](images/example1.png)

## How to install MaskTheFace
It’s advisable to [make a new virtual environment](https://towardsdatascience.com/setting-up-python-platform-for-machine-learning-projects-cfd85682c54b) and install the dependencies. Following steps can be taken to download get started with MaskTheFace
### Clone the repository
```
git clone https://github.com/aqeelanwar/MaskTheFace.git
```

### Install required packages
The provided requirements.txt file can be used to install all the required packages. Use the following command

```
cd MaskTheFace
pip install –r requirements.txt
```

This will install the required packages in the activated python environment.

## How to run MaskTheFace

```
cd MaskTheFace
# Generic
python mask_the_face.py --path <path-to-file-or-dir> --mask_type <type-of-mask> --verbose

# Example
python mask_the_face.py --path 'data/office.jpg' --mask_type 'N95' --verbose
```
![cover_photo](images/run.png)
### Arguments
|    Argument    |                                                                                                       Explanation                                                                                                       |
|:--------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|      path      |                                                                            Path to the image file or a folder containing images to be masked                                                                            |
|    mask_type   | Select the mask to be applied. Available options are 'N95', 'surgical_blue', 'surgical_green', 'cloth', 'empty' and 'inpaint'. The details of these mask types can be seen in the image above. More masks will be added |
|     pattern    |                                 Selects the pattern to be applied to the mask-type selected above. The textures are available in the masks/textures folder. User can add more textures.                                 |
| pattern_weight |                                   Selects the intensity of the pattern to be applied on the mask. The value should be between 0 (no texture strength) to 1 (maximum texture strength)                                   |
|      color     |                                                         Selects the color to be applied to the mask-type selected above. The colors are provided as hex values.                                                         |
|  color_weight  |                                      Selects the intensity of the color to be applied on the mask. The value should be between 0 (no color strength) to 1 (maximum color strength)                                      |
|      code      |                                                              Can be used to create specific mask formats at random. More can be found in the section below.                                                             |
|     verbose    |                                                                          If set to True, will be used to display useful messages during masking                                                                         |


## Frequently Asked Questions (FAQ)
Click (here)[faq.md] to troubleshoot errors faced while installing and running MaskTheFace

## Supported Masks:
### Mask Types:
Currently MaskTheFace supports the following 4 mask types
1. Surgical
2. N95
3. KN95
4. Cloth
5. Gas

![mask_types](images/mask_types.png)

New masks are being added. Users, can also add custom masks following the guidelines provided.

### Mask Variations:
Each of the mask types mentioned above can varied in the following terms to create even more masks
#### 1. Textures/Patterns variations:
MaskTheFace provides 24 existing patterns that can be applied to mask types above to create more variations of the graph. Moreover, users can easily add custom patterns following the guidelines provided.
![mask_textures](images/textures.png)
#### 2. Color varations:
MaskTheFace provided script to modify existing mask types in terms of colors to generate variations of existing graphs.
![mask_colors](images/colors.png)
####  3. Intensity varations:
MaskTheFace provided script to modify existing mask types in terms of intensity to generate variations of existing graphs.
![mask_colors](images/intensities.png)


## Features:
### Support for multiple mask types
![cover_photo](images/example1.png)
### Support for both single and multi-face images:
![cover_photo](images/multiface.png)
### Wide face angle coverage
![cover_photo](images/angle.png)
### Brightness corrected mask application
![cover_photo](images/brightness.png)
### Bulk masking on datasets
![cover_photo](images/dataset.png)

## Example usage

### 1. Face recognition with masks
Face recognition trained to usual face images have proven to give good accuracy.In the recent ongoing outbreak of Covid19, people have been advised to use face masks. With majority of people using face masks, the face recognition system fails to perform. Due to limited mask images, there is not enough masked data available to train a new system. MaskTheFace can be used to create masked data set from unmasked dataset which is then used to either fine-tune an existing or train a new face recognition system.

#### Example
A face recognition system consisting of 20 different classes was considered. A VGG16 network was trained on these 20 different classes of un-masked faces from VGGFace2 dataset for face recognition. The network achieved an accuracy of 68.3% on un-masked test dataset. When the same network was tested on the masked test images (obtained from MaskTheFace) gave an accuracy of only 36.6% (about half of that of before)

MaskTheFace was used to convert the training dataset from previous problem to masked dataset. Both the unmasked and masked dataset was made a part of training set. The network trained on this dataset
gave test accuracy of 70.7% on un-masked, while 65.5% on masked dataset.

Not only the accuracy of masked dataset was improved, but the system also performed better on masked faces.

![cover_photo](images/face_recognition.png)



### 2. Monitoring if people are using masks
MaskTheFace generated datasets can be used to monitor if people are using face masks.

#### Example
The detector above was trained on 2000 images (1000 mask, 1000 without mask) from the VGGface2 dataset. The masked images contained 4 different types of masks. A VGG16 network was trained on these images which achieved a 98.9% accuracy on test dataset.

![cover_photo](images/mask_no_mask.png)

## Citation
If you find this repository useful, please use following citation
```
https://github.com/aqeelanwar/MaskTheFace
```
