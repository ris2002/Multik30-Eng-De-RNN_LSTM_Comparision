# Multi30k(Eng-De)_Dataset_RNN_LSTM
This is my 11th project. In this project, I plan to construct a seq to seq models using LSTMs and Vanilla RNN and show the difference in performance between them.
## Problem Analysis
* Type-Sequence-to-Sequence Prediction
* Business Goal - The business goal is to identify and translate English sentences into German using LSTMs and Vanilla RNNs and compare the performance difference in their base configuration.
* LSTM/RNN Objective - LSTMs needs to be better at performance in their base configurations.
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
### Vocabulary
It is a dictionary of words stored, and all words are unique. Previously,  a vocabulary was created using torchtext, the current industry standard, which uses Hugging Face Transformers. In this project, it was manually created using Counter

## Seq2Seq Architecture Components
A quick breakdown of the core pillars used in Neural Machine Translation and LLMs.
### 1. Encoder
**The "Reader"**  
The **Encoder** processes the raw input sequence (like an English sentence) and converts it into a series of mathematical representations. It scans the input token by token, updating its internal state to capture the meaning, order, and relationship between words.
### 2. Context Vector
**The "Bridge"**  
The **Context Vector** is a fixed-size numerical summary of the entire input sequence. It acts as the final output of the Encoder and the starting point for the Decoder. Think of it as a "compressed thought" that contains all the essential information needed to generate a response.
### 3. Decoder
**The "Writer"**  
The **Decoder** takes the Context Vector and unfolds it into a new sequence (like a Spanish translation). It generates the output one step at a time, using the information from the context vector and its own previously generated words to predict what comes next.
## Evaluation Metric
## Brief Concepts of LSTMs
## Hypothesis Formulation
Null Hypothesis - The LSTM translation model is much better than the vanilla RNN in its base configuration.
## Experimentations
### Vanilla RNNS (15 Runs)
### LSTMS (15 Runs)



