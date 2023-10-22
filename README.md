# Meta3DCNN

Personal project on detection and identification of potential injuries in CT scans of trauma patients. The idea was based on Kaggle competition issued by RSNA [1].
## Data
Data used in project is solely taken from dataset provided by Radiological Society of North America for issued competition [1]. The dataset includes: 
- CT scans (around 3000)
- Information about state of patient organs:
  - liver, spleen, kidneys - healthy/low injury/high injury
  - bowel - healthy/injured
- Active extravasation visible on CT scan (True/False)
- Segmentation map for organs provided for around 200 CT scans.

Additionaly in case of bowel injury or active extravasation occuring on CT scan, frames on which they are visable are provided.  
The images are provided in DICOM format and segmantations in NII format.

# Model
The proposed pipeline consists of three models- organ detector, organ estimator and active extravasation/bowell injury detector. 
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/5bb846ad-ea01-4356-828f-5e75ddb9dbab)
The input to piple consists of series of DICOM images from CT scan. Whole scan is parted into series of N sized chunks. Each chunk is loaded and preprocessed before being passed to organ detector and ACE/BOWEL estimator.
The outputs from those models are then aggregated giving respectively organ patches for liver, spleen and kidneys and state of Bowel and active extravasation. Finally extracted organs are processed again and passed to organ extractor.

## Organ detector

## Organ estimator

## ACE/BOWEL detector

## Training

## Results

# Thoughts and conclusion
---
[1]. Kaggle competition: https://www.kaggle.com/competitions/rsna-2023-abdominal-trauma-detection
