# Liver_tumor_segmentation
Using ResUnet to segment liver tumors from CT scan images. Refer to this [report](https://github.com/1998anwesha/Liver_tumor_segmentation/blob/main/Liver_tumor_segmentation_using_ResUNet.pdf) for details regarding methodology, loss metrics, results and future work.

We have used Google Colab pro for this project. The training code can also work on normal Colab using T4 GPU and memory space of less than 30 GB. 

## File and dataset extraction
First, extract the file content onto one folder "imageprocessing" in google drive "MyDrive". Now, this folder should have multiple folders and Colab files  
Download dataset Liver segmentation [3D-IRCADb-01](https://www.ircad.fr/research/data-sets/liver-segmentation-3d-ircadb-01/).  This is a zip file of size 806 MB.
Create a new folder called "Dataset" in "imageprocessing" and place this zip file there.

Next, open dataset_generation.ipynb in Google Colab. Follow the instructions in it. 
On running this, "train" folder will be created in “imageprocessing”. Total time taken for data extraction will be around 2 hours.

## Training Liver and Tumor segmentation models
Now open liver_segmentation.ipynb file and run it for training ResUnet with pre-processed CT scan images and their corresponding liver masks. It will generate the models folder. There are already three pre-trained models trained on 25%, 50% and 100% data in the models folder. We get following epochs.

Epoch 1/30
581/581 [==============================] - 7156s 12s/step - loss: 0.6114 - acc: 0.9795 - dice_coef: 0.3977 - val_loss: 0.8145 - val_acc: 0.9328 - val_dice_coef: 0.1855
Epoch 2/30
581/581 [==============================] - 907s 2s/step - loss: 0.4629 - acc: 0.9928 - dice_coef: 0.5361 - val_loss: 0.7656 - val_acc: 0.9513 - val_dice_coef: 0.2344
....
....
....
Epoch 28/30
581/581 [==============================] - 53s 91ms/step - loss: 0.4518 - acc: 0.9946 - dice_coef: 0.5482 - val_loss: 0.4034 - val_acc: 0.9954 - val_dice_coef: 0.5966
Epoch 29/30
581/581 [==============================] - 52s 89ms/step - loss: 0.4004 - acc: 0.9950 - dice_coef: 0.5996 - val_loss: 0.4399 - val_acc: 0.9945 - val_dice_coef: 0.5601
Epoch 30/30
581/581 [==============================] - 63s 108ms/step - loss: 0.3707 - acc: 0.9956 - dice_coef: 0.6293 - val_loss: 0.4633 - val_acc: 0.9954 - val_dice_coef: 0.5367


Run Liver_segmentation_results.ipynb to view the outputs. Run models in models folder or using your trained version. We see the results and evaluation metric information there.

Then run Tumor_segmentation.ipynb file for training ResUnet for with the tumor segmentation masks and segmented liver images. This gives following results:
![image](https://private-user-images.githubusercontent.com/39149911/295389035-18f12e52-0777-4252-b4cd-31f9964a8c26.jpeg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDQ4NTA5NjIsIm5iZiI6MTcwNDg1MDY2MiwicGF0aCI6Ii8zOTE0OTkxMS8yOTUzODkwMzUtMThmMTJlNTItMDc3Ny00MjUyLWI0Y2QtMzFmOTk2NGE4YzI2LmpwZWc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTEwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExMFQwMTM3NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mY2ZlOTA2YmM2NjM1OTg3ZmEyNDZkNzZlODBiYTkzMjNmZGNiYjkwMmNiNWU2N2FhMjNiNWVhNTdmMmMxMTcwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.roZ6JC7RUy_CGlh-ZgkX1A4K4C40sEZOsxkfPrEiTeM)

Run Tumor_segmentation_result.ipynb to view final output. You can choose any segmentation model from the 'models' folder and try running the visualization codes.

Run on 25% of the data for faster training. You may run Tumor_segmentation.ipynb on 100 epochs for more accurate results.

