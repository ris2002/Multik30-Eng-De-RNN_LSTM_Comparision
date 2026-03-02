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
spaCy is a fast, production-ready Python library for Natural Language Processing (NLP).
It helps computers understand and analyze text.
Think of it like a toolkit that converts raw text into structured data that your application can use.
It is mainly used to tokenise the text and for linguistic analysis.
Two separate tokenisers are used — en_core_web_sm for English and de_core_news_sm for German.
### Torchtext Vocabulary 
Torchtext is part of pytorch library, what it does is it assigns IDs to the tokenized text before passing it to the embedding layer of the RNN/LSTM.
Four special tokens are added to each vocabulary: <unk> for unknown words, <pad> for padding sequences to equal length, <sos> for start of sentence, and <eos> for end of sentence.
### Data Loading
## Evaluation Metric
## Brief Concepts of LSTMs
## Hypothesis Formulation
## Experimentations
### Vanilla RNNS (15 Runs)
### LSTMS (15 Runs)



