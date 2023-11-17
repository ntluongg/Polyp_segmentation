# User instruction


## On kaggle:
```python
import requests
import os

url = 'https://drive.google.com/file/d/1zlmb432PJ5STHWt4owwgZOMcDxIUFI18/view?usp=share_link'
# Directory to save model
save_dir = '/kaggle/working/'

response = requests.get(drive_url)

with open(os.path.join(save_dir, 'unet_model.pth'), 'wb') as f:
    f.write(response.content)
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

