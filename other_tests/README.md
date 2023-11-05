# Leftover from test and experiments

## RSNA_injury_classification 
Here we've tried to estimate injury in single image based on labels informing about bowel injury or ace visible in frame. For this test metaformer architecture was used. Dataset used for this model was created with data imbalance between healthy and injured images in mind. To solve this we tried to sample the set of healthy images based on distribution of injured samples apperance in proportion to ct scan length. The code used for this datased is included in "RSNA_injury_classification_dataset.ipynb". 
