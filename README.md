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
*Image 1. Proposed pipeline.*
  
The input to piple consists of series of DICOM images from CT scan. Whole scan is parted into series of N sized chunks. Each chunk is loaded and preprocessed before being passed to organ detector and ACE/BOWEL estimator.
The outputs from those models are then aggregated giving respectively organ patches for liver, spleen and kidneys and state of Bowel and active extravasation. Finally extracted organs are processed again and passed to organ extractor. All of the mentioned models were trained separately. 

## Organ detector
For the task of organ detection we decided to choose Ultralytics YoloV8 model[2]. Dataset for organ detetion was created by using segmentations provided in competition dataset. Doing this we have to bear in mind that 
the original segmentations were created with TotalSegmentator model and not expert labeled. This already limits our organ detector to being at best as good as the segmantator model.  
  
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/109d069e-4aeb-4013-a3ad-1f2b3cbd6760)  
*Image 2. Simplified flowchart of organ detector training*  
  
Prepared model was designed for only liver, spleen, left kidney and right kidney detection. The ultralytics package requires us to prepare data in COCO style dataset for training. To achive this, our first step was to
extract boxes from segmentation map for every DICOM image in provided, already segmented subset of CT scans. After assigning boxes to every avaliable image we splited whole set into training and validation set, and then converted every image into png format. Every dicom image was loaded with windowing function. Finally the images and boxes data were saved with COCO dataset structure in mind.  
  
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/cccc6ec9-0840-4093-b418-1643402e33a2)  
*Image 3. Example of windowed DICOM images with affixed boxes.*  

For this project two YOLOv8 models were trained. First was small sized version and the second medium sized version. Results are included in OrganDetector folder. 

## Organ estimator

## ACE/BOWEL detector

## Training

## Results

# Thoughts and conclusion
---
[1]. Kaggle competition: https://www.kaggle.com/competitions/rsna-2023-abdominal-trauma-detection
[2]. Ultralytics YoloV8: https://github.com/ultralytics/ultralytics
