# User instruction
## Some note:
First you need to use Kaggle notebook with GPU T4 x2 enabled because this model is "data-parallel"ed.
And you also need to add the BKAI-IGH NeoPolyp dataset to your kaggle notebook (https://www.kaggle.com/competitions/bkai-igh-neopolyp/overview).
## guide:
```python
!pip install gdown
```
```python
import gdown
#latest model: 0.74 point
url = 'https://drive.google.com/uc?export=download&id=11pIkiEQkJXYxiSR5xHBj09KGmIPtDObh'
gdown.download(url, 'unet_model.pth', quiet=False)
```
```python
!git clone https://github.com/ntluongg/Polyp_segmentation.git
```
```python
!mkdir predicted_mask 
```
```python
!python /kaggle/working/Polyp_segmentation/infer.py --checkpoint '/kaggle/working/unet_model.pth' --test_dir '/kaggle/input/bkai-igh-neopolyp/test/test' --mask_dir '/kaggle/working/predicted_mask'

# parse args checkpoint, test_dir (please add data of competition), mask_dir

