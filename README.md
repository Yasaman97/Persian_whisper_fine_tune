# Fine tune Whisper for Persian

Course: ID2223-Scalable Machine Learning and Deep Learning

Contributor:
<a href="https://github.com/yasaman97">Yasaman Pazhoolideh</a>


## About

This project focuses on fine tuning <a href="https://huggingface.co/openai/whisper-small">OpenAI's Whisper model</a> for Persian automatic speech recognition. the Persian dataset from <a href="https://huggingface.co/datasets/mozilla-foundation/common_voice_11_0">Common Voice dataset</a>, is used for training.


## Implementation

In order to implement the system, first, the feature-pipeline.py should be run. This loads the dataset, keeps 60% of it, due to constrains on memory. Then, it lapplys feature extractor and tokenizer ad prepares the dataset for training. The dataset is then saved as a zip file on Google Drive, so we can skip the previous steps while training. 
Second, training-pipeline.py, which loads the data previously created, and a pre-trained Whisper checkpoint. The word error rate (WER) metric, and the 'de-facto' metric for assessing ASR systems. 
Lastly, a Gradio application is written to create the user interface on HuggingFace, where they can speak into the microphone, upload an audio file, or paste the URL to a vieo.

## Possible model Performance Improvements

The most relevant parameters we used are:
- The model predictions and checkpoints are written on Google Drive to be able to recover them and restart the training from the latest checkpoint in case of a crash. And, the evaluation of WER metric is calculated every 100 steps.


a) model-centric approach:

We can use the medium or large pre-trained whisper checkpoints, however, Google colab will run out of available RAM and crash.
The number of training epochs can be set to higher than only once, wich would help with underfitting to a certain degree, however, this will increase the runtime, and cause problems with Google Colab GPU time.

b) data-centric approach: 
- While it is possible to tweak the hyperparameters and get a better performance out of our model, the more important factor, arguably, is the dataset. I have tried multiple variations of dataset size, and in the end kept 60% of it, because it was the highest amount that would not crash.

## Hugging Face spaces

The Hugging Face <a href="https://huggingface.co/spaces/Yasaman/whisper_fa">space</a>

