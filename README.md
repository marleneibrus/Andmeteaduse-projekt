# Stanford Ribonanza RNA Folding (Kaggle)
#### Authors: Marlene Ibrus, Pärl Pind

Creating a model that predicts the structures of any RNA molecule

## Goal of the project
Our project is from the Kaggle competition Stanford Ribonanza RNA Folding. The aim of our project is to predict the chemical reactivity at each position of an RNA molecule. Furthermore, the results could help better understand how RNA works, how to manipulate it, predict RNA structure. We also had the goal of trying to enter our submission into the Kaggle competition, however, since training the model and predicting the results took longer than expected, we missed the deadline by a very close margin. 

## Guide of the repository
Kaggle provided us with the training and testing data, as well as a filtered and cleaned training data (train_data_QUICK_START). However, since the train and test csv files were too large, we had to convert them into the Parquet format, which would make the sizes smaller and also speed up loading times. Therefore, the datasets in our repository are files test_sequences.parquet, train_data.parquet, train_data_QUICK_START.csv.

File E9_report.pdf explains our datasets and goals further.

We have three jupyter notebook files: CVStoTFRecord.ipynb, Inference.ipynb and "projekt !.ipnyb".

CVStoTFRecord.ipynb converts our train_data_QUICK_START.csv file to TFRecords. This helps us train the model more efficiently, since TFRecords' binary format is more efficient to read than the text in the original csv file. The TFRecords files are in the tfrfile folder. There are 164 of them, because that's how many shards we decided to split the dataset into.

The "projekt !.ipnyb" notebook is where the training of our model happens. First we are decoding the TFRecord files, then using transformer blocks for the model. The trained model is written into the model_weights folder. 

Inference.ipynb is where we predict the results for the test dataset based on our trained model. Predicted results are written into a file called "submission.csv". The final submission file is not uploaded to GitHub, due to the huge file size of nearly 9 GB-s.

## How to get the same results
The same results can be achieved when downloading train_data_QUICK_START.csv and test_sequences.csv from here https://www.kaggle.com/competitions/stanford-ribonanza-rna-folding/data.
Then using the code from notebook CVStoTFRecord the train data should be converted to TFRecord files. Training the model with the "projekt !.ipnyb" notebook with the parameters we have used and predicting the results on the test data will give the same results we have achieved with our project. 
