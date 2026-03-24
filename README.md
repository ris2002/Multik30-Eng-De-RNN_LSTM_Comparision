# Multi30k(Eng-De)_Dataset_RNN_LSTM
This is my 11th project. In this project, I plan to construct a seq to seq models using LSTMs and Vanilla RNN and show the difference in performance between them.
## Problem Analysis
* Type-Sequence-to-Sequence Prediction
* Business Goal - The business goal is to identify and translate English sentences into German using LSTMs and Vanilla RNNs and compare the performance difference between them using the same baseline hyperparameters. There will be 1 run for each of the architecture due to time and resource connstraint
* LSTM/RNN Objective - LSTMs need to perform better than RNN in the baseline trim, which proves that LSTMs are better experimentally.
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
## LSTMS
1.  Why was LSTM invented?
* LSTMs were invented as a means to counter the weaknesses in  RNNs, which are Vanishing Gradients.
2.  Cell state vs hidden state
* Cell state is basically like long-term memory or a summary of the sentence context, and hidden states remember what each word came before. Yes, compared to FFNN, in RNN, hidden states are said to store the context of the sentence, but that has limitations due to vanishing gradients. Cell state acts like a secondary memory which tries to remember the whole context of the paragraph in addition to the hidden state. The cell states have limited linear interactions, unlike the hidden state from RNN and will be updated only using the 4 gates. The hidden state is updated using the output gate and the updated cell state 
3.  Four gates — what each does
  * 1. Forget gate (ft)-Basically is used to decide what input  to forget and what to remember and update that inn the cell state
    2. Input gate   → decides how much new info to add
    3. Cell gate    → calculates what new info to add (tanh)
    4. Output gate  → decides what part of ct becomes ht
4.  Why does it solves RNN problem mathematically
* In RNN:  dnext = dz @ Whh  → fixed matrix → uncontrolled shrinking
* In LSTM: dnext = dct × ft  → learned gate → controlled by model
* ft is learned → model can set ft ≈ 1 to preserve gradients
5.  Why it still has limitations
* Even though LSTMs can outlast the RNN in terms of remembering the memory of long sentences, since they use derivatives to update the weights, they at some point of time start exhibiting the vanishing gradient problems  
6.  Why was the transformer invented next
* Transformers were invented to tackle the limitations posed by the LSTMS. Transformers use an attention mechanism — every word 
attends to every other word directly — no sequential 
processing — no forgetting at all.
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
### BLEU
* It measures how similar the predicted translation results are to the actual translation.
     * 0-10 Useless
     * 10-20 Hard to understand
     * 20-30 Understandable
     * 30++ Very Good 

## Hypothesis Formulation
Null Hypothesis - LSTM and RNN perform similarly
Alternative     - LSTM performs better than RNN
## Experimentations
### Hyper Parameters
* INPUT_FEATURES    = 128, I wanted to keep it as low and simple as possible, but not too low
* OUTPUT_FEATURES   = 128
* INPUT_NEURONS     = 128, I wanted to keep it as low and simple as possible, but not too low
* OUTPUT_NEURONS    = 128
* NUM_LAYERS        = 1, didn't want to complicate, and increasing the number of layers might reduce the overall BLEU score for both the architectures 
* NUM_DROPOUT       = 0, wanted to compare both the architectures in their baseline trim
* NUM_EPOCHS        = 100, not too low or high, which might cause overfitting
* BATCH_SIZE        = 128, felt for 29k senntences 128 was optimum
* LEARNING_RATE     = 0.001
#### Scores
* Vanilla RNN- BLEU Score- 0.0944, Total Params-2,830,211
* LSTM - BLEU Score- 0.1422, Total Params-3,028,355
## Result
Alternative Hypothesis is accpeted 
## Conclusion 
Even though the BLEU score of LSTM(0.1422) is low, its 50% better than Vanilla RNN, the low score was expected as there were lack of more experimenta;l runs due to time and resource constraint. My next project will be a add on to this project where in I try try to acheive a BLEU score of atleast in the range of 25-30 using LSTM as this experiment has proven that they are much better than Vanilla RNNs. 
## What I Learned
- Built seq2seq from scratch
- Understood why LSTM outperforms RNN
- Understood vanishing gradients mathematically




