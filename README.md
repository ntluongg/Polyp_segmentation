# User instruction


## On kaggle:
```python
import requests
import os

url = 'https://drive.google.com/uc?export=download&id=11pIkiEQkJXYxiSR5xHBj09KGmIPtDObh'
save_dir = '/kaggle/working/'

try:
    response = requests.get(url)
    response.raise_for_status()  # Raise an exception if the GET request was unsuccessful
except requests.exceptions.RequestException as err:
    print(f"Error occurred: {err}")
else:
    try:
        with open(os.path.join(save_dir, 'unet_model.pth'), 'wb') as f:
            f.write(response.content)
    except IOError as e:
        print(f"Couldn't write to file: {e}")
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

