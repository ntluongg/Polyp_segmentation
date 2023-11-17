# User instruction
First you need to use Kaggle notebook with GPU T4 x2 because this model is "data parallel"-ed

## On kaggle:
```python
!pip install kaggle
#!kaggle datasets download -d imnotluong/unetpp67 #for 0.67 model
#better one: 0.74
!kaggle datasets download -d imnotluong/unetplusplus
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

