This folder contain all code used in training of organ detector model. 

## Box info
Box information was prepared in form of pandas data frame. Each row contained information about:
- Series id for identyfication
- Size of images in CT scan
- Frames in which liver, spleen or kidneys are visible
- Boxes for organ, in order corresponding to frames they occure
- Box in which all other boxes for selected organ are contained (named abox in example below)
   
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/36019d1b-3553-46c5-8de4-2da919d7d40f)

Organ placement can be seen after aggregating every box for given organ. Some outlayers can be seen, the reason being different sized of CT scan.
  
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/6776cab9-cb60-4b92-b41e-9ab3e32046a8) 

Example of boxes extracted from segmented CT scan.  

https://github.com/Benu13/Meta3DCNN/assets/39136856/794b9dd8-c2ba-406c-bdb1-324eb12f0f17
  
Code used for this process is included in rsna-box-preparation.ipynb file.  

## Dataset creation
Dataset for training Yolo model must be in COCO format. Images are resized to 256x256. All images from segmented CT scans are used, giving 29180 images with organs present and 
41361 backgrounds.  
Code used for this process is included in rsna-organ-detection-dataset.ipynb file.  

## Yolo Training
Code used for training YOLO detector is included in rsna-yolov8-od.ipynb.
## Results
Training metrics  
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/d23a4da4-9b5e-4b93-a00a-9c0530da42ae)  
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/cb685179-7f95-4122-be66-bb9f4077e961)  
![image](https://github.com/Benu13/Meta3DCNN/assets/39136856/00a7b5f6-e2f4-446a-a9dc-443b4e5c2496)  

