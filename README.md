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

![image](https://private-user-images.githubusercontent.com/39149911/295383009-db91138e-5797-499e-99d5-499819b70a07.jpeg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDQ4NDk4MjIsIm5iZiI6MTcwNDg0OTUyMiwicGF0aCI6Ii8zOTE0OTkxMS8yOTUzODMwMDktZGI5MTEzOGUtNTc5Ny00OTllLTk5ZDUtNDk5ODE5YjcwYTA3LmpwZWc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTEwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExMFQwMTE4NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03ZWRmNjZiY2ZkZmE0YzdmN2VlZGU0NWFkY2NlYmE3YWZjNmQ4ZDY1OTFkZGU5ZmUzMmIwMTliMTU2MjYxMTUwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.hPjRv_G3MvzHTd4LSmgI3cx8yPIHpKTeFryvc1timMM)

Epoch 1/30
581/581 [==============================] - 7156s 12s/step - loss: 0.6114 - acc: 0.9795 - dice_coef: 0.3977 - val_loss: 0.8145 - val_acc: 0.9328 - val_dice_coef: 0.1855
Epoch 2/30
581/581 [==============================] - 907s 2s/step - loss: 0.4629 - acc: 0.9928 - dice_coef: 0.5361 - val_loss: 0.7656 - val_acc: 0.9513 - val_dice_coef: 0.2344
Epoch 3/30
581/581 [==============================] - 267s 460ms/step - loss: 0.5270 - acc: 0.9916 - dice_coef: 0.4644 - val_loss: 0.7977 - val_acc: 0.9343 - val_dice_coef: 0.2023
Epoch 4/30
581/581 [==============================] - 219s 377ms/step - loss: 0.5101 - acc: 0.9925 - dice_coef: 0.4899 - val_loss: 0.9870 - val_acc: 0.9924 - val_dice_coef: 0.0130
Epoch 5/30
581/581 [==============================] - 201s 347ms/step - loss: 0.5243 - acc: 0.9931 - dice_coef: 0.4757 - val_loss: 0.4896 - val_acc: 0.9922 - val_dice_coef: 0.5104
Epoch 6/30
581/581 [==============================] - 207s 354ms/step - loss: 0.5043 - acc: 0.9921 - dice_coef: 0.4957 - val_loss: 0.6307 - val_acc: 0.9937 - val_dice_coef: 0.3693
Epoch 7/30
581/581 [==============================] - 150s 258ms/step - loss: 0.5358 - acc: 0.9933 - dice_coef: 0.4642 - val_loss: 0.7332 - val_acc: 0.9754 - val_dice_coef: 0.2668
Epoch 8/30
581/581 [==============================] - 138s 238ms/step - loss: 0.4847 - acc: 0.9936 - dice_coef: 0.5153 - val_loss: 0.5356 - val_acc: 0.9947 - val_dice_coef: 0.4644
Epoch 9/30
581/581 [==============================] - 117s 202ms/step - loss: 0.4188 - acc: 0.9942 - dice_coef: 0.5812 - val_loss: 0.5315 - val_acc: 0.9950 - val_dice_coef: 0.4685
Epoch 10/30
581/581 [==============================] - 93s 161ms/step - loss: 0.4213 - acc: 0.9950 - dice_coef: 0.5787 - val_loss: 0.4630 - val_acc: 0.9907 - val_dice_coef: 0.5370
Epoch 11/30
581/581 [==============================] - 99s 171ms/step - loss: 0.4194 - acc: 0.9951 - dice_coef: 0.5806 - val_loss: 0.7948 - val_acc: 0.9338 - val_dice_coef: 0.2052
Epoch 12/30
581/581 [==============================] - 64s 110ms/step - loss: 0.4477 - acc: 0.9942 - dice_coef: 0.5523 - val_loss: 0.5682 - val_acc: 0.9946 - val_dice_coef: 0.4318
Epoch 13/30
581/581 [==============================] - 76s 131ms/step - loss: 0.4291 - acc: 0.9945 - dice_coef: 0.5709 - val_loss: 0.8306 - val_acc: 0.9930 - val_dice_coef: 0.1694
Epoch 14/30
581/581 [==============================] - 74s 126ms/step - loss: 0.4301 - acc: 0.9949 - dice_coef: 0.5699 - val_loss: 0.7898 - val_acc: 0.9452 - val_dice_coef: 0.2102
Epoch 15/30
581/581 [==============================] - 75s 129ms/step - loss: 0.4403 - acc: 0.9939 - dice_coef: 0.5597 - val_loss: 0.4954 - val_acc: 0.9901 - val_dice_coef: 0.5046
Epoch 16/30
581/581 [==============================] - 64s 111ms/step - loss: 0.3734 - acc: 0.9955 - dice_coef: 0.6266 - val_loss: 0.3792 - val_acc: 0.9951 - val_dice_coef: 0.6208
Epoch 17/30
581/581 [==============================] - 61s 105ms/step - loss: 0.4053 - acc: 0.9952 - dice_coef: 0.5947 - val_loss: 0.4727 - val_acc: 0.9947 - val_dice_coef: 0.5273
Epoch 18/30
581/581 [==============================] - 65s 112ms/step - loss: 0.4471 - acc: 0.9946 - dice_coef: 0.5529 - val_loss: 0.8006 - val_acc: 0.9314 - val_dice_coef: 0.1994
Epoch 19/30
581/581 [==============================] - 57s 98ms/step - loss: 0.3454 - acc: 0.9962 - dice_coef: 0.6546 - val_loss: 0.3290 - val_acc: 0.9961 - val_dice_coef: 0.6710
Epoch 20/30
581/581 [==============================] - 67s 116ms/step - loss: 0.3858 - acc: 0.9957 - dice_coef: 0.6142 - val_loss: 0.4628 - val_acc: 0.9954 - val_dice_coef: 0.5372
Epoch 21/30
581/581 [==============================] - 62s 107ms/step - loss: 0.4046 - acc: 0.9949 - dice_coef: 0.5954 - val_loss: 0.4041 - val_acc: 0.9953 - val_dice_coef: 0.5959
Epoch 22/30
581/581 [==============================] - 63s 108ms/step - loss: 0.3701 - acc: 0.9960 - dice_coef: 0.6299 - val_loss: 0.4366 - val_acc: 0.9955 - val_dice_coef: 0.5634
Epoch 23/30
581/581 [==============================] - 60s 103ms/step - loss: 0.3820 - acc: 0.9957 - dice_coef: 0.6180 - val_loss: 0.4485 - val_acc: 0.9954 - val_dice_coef: 0.5515
Epoch 24/30
581/581 [==============================] - 62s 107ms/step - loss: 0.3959 - acc: 0.9955 - dice_coef: 0.6041 - val_loss: 0.4716 - val_acc: 0.9911 - val_dice_coef: 0.5284
Epoch 25/30
581/581 [==============================] - 61s 106ms/step - loss: 0.4135 - acc: 0.9953 - dice_coef: 0.5865 - val_loss: 0.5361 - val_acc: 0.9943 - val_dice_coef: 0.4639
Epoch 26/30
581/581 [==============================] - 57s 98ms/step - loss: 0.4018 - acc: 0.9951 - dice_coef: 0.5982 - val_loss: 0.5750 - val_acc: 0.9886 - val_dice_coef: 0.4250
Epoch 27/30
581/581 [==============================] - 55s 95ms/step - loss: 0.3893 - acc: 0.9954 - dice_coef: 0.6107 - val_loss: 0.4037 - val_acc: 0.9930 - val_dice_coef: 0.5963
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

