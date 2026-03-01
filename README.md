# Multi30k(Eng-De)_Dataset_RNN_LSTM
This is my 11th project. This project will be done in a similar style to my 9th project (https://github.com/ris2002/Adult-Census-Income-MLE-NN). I am only going to involve RNN and LSTM, as I am learning those techniques to apply them to sequence-to-sequence  tasks. For each technique, I will run 30 experiments (15 runs each).
## Problem Analysis
* Type-Sequence-to-Sequence Prediction
* Business Goal - The business goal is to identify and translate English sentences into German.
* LSTM/RNN Objective - It needs to get an overall BLEU score of around 30.
## Dataset Overview
* The dataset was exported from Hugging Face (https://huggingface.co/datasets/bentrevett/multi30k). It consists of 31,014 rows of English and German sentences; that is the only column. Each item in the dataset is a tuple of (English sentence, German sentence), so there is no need to convert it into a dataframe.
* Train_data=29000 rows
* Test_data=1000
* Valid_data=1014
## Pre_Process Strategy
### Data Cleaning
* We lower the text.
* We next remove the unnecessary symbols and characters from the text.
* We remove the white spaces, using strip().
* German special characters (ä, ö, ü, ß, Ä, Ö, Ü) are preserved during cleaning.
### Spacy Tokenisation
### Torchtext Vocabulary 
### Data Loading
## Evaluation Metric
## Brief Concepts of LSTMs
## Hypothesis Formulation
## Experimentations
### Vanilla RNNS (15 Runs)
### LSTMS (15 Runs)



