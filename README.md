# Segmentation of Brain Tumors from MRI Images using Deep Learning
## Instruction on running the Project

1. Open the python file "brain_tumor_segment.py" in any python code editor
2. Edit the file paths to reflect the location of the pre-trained weights in your local directory.
	1. weights-core-best.h5
	2. weights-ET-best.h5
	3. weights-full-best.h5
	```python
		model = unet_model()
		model.load_weights('/home/weights-full-best.h5')
	```
        ```python
		model_core = unet_model_nec3()
		model_core.load_weights('/home/weights-core-best.h5')
		model_ET = unet_model_nec3()
		model_ET.load_weights('/home/weights-ET-best.h5')
	```
3. The python file contains code to automatically fetch the BRATS Brain IMage Dataset. You have to change the path in code to a destination of your local disk.
```python
import os
if not (os.path.exists('MICCAI_BraTS_2018_Data_Training.zip') or os.path.exists('/home/data/HGG/')):
    !curl -LO "https://www.cbica.upenn.edu/sbia/Spyridon.Bakas/MICCAI_BraTS/2018/MICCAI_BraTS_2018_Data_Training.zip"
    if not os.path.exists("/home/data/"):
        os.makedirs("/home/data/")
    !unzip "MICCAI_BraTS_2018_Data_Training.zip" -d "/home/data/"
```
4. Change the path in code to point the above fetched dataset in the "Training" part of code.
```python
pul_seq = 'flair'
Flair = create_data_onesubject_val('/home/data/HGG/', '**/*{}.nii.gz'.format(pul_seq), count, label=False)
```
5.   ####One has to install certain libraries for the proper functioning of the code:
	1. Tensorflow
	2. numpy
	3. matplotlib
	4. keras
	5. SimpleITK
	6. SciKit-Image
#####The above libraries have to be downloaded and installed on a command line interface using the following command:
```python
pip install SimpleITK
```

###The link of the BRATS dataset used in this Project:
[BRATS DATASET](https://www.cbica.upenn.edu/sbia/Spyridon.Bakas/MICCAI_BraTS/2018/MICCAI_BraTS_2018_Data_Training.zip "BRATS DATASET")
> Kindly note that he dataset is very big. Size ~ 2 GB.
