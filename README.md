# Emotive Speech Analyzer

* The idea behind creating this project was to build a voice emotion detector that could detect emotions from audio from speech, as a way to support a way to advance _animals_ from its current stagnation.

## Analyzing audio signals
![image](images/joomla_speech_prosody.png?raw=true)
©joomla_speech_prosody
<br>

### Datasets:
Made use of two different datasets:
1. [RAVDESS](https://psychlabs.torontomu.ca/smartlab/resources/speech-song-database-ravdess/).
This dataset includes around 1500 audio file input from 24 different actors. 12 male and 12 female where these actors record short audios in 8 different emotions i.e 1 = neutral, 2 = calm, 3 = happy, 4 = sad, 5 = angry, 6 = fearful, 7 = disgust, 8 = surprised.<br>
Each audio file is named in such a way that the 7th character is consistent with the different emotions that they represent.

2. [SAVEE](https://personalpages.surrey.ac.uk/p.jackson/SAVEE/).
This dataset contains around 500 audio files recorded by 4 different male actors. The first two characters of the file name correspond to the different emotions that the potray. 

## Audio files:
Tested out the audio files by plotting out the waveform and a spectrogram to see the sample audio files.<br>
**Waveform**
![](images/wave.png?raw=true)
<br>
<br>
**Spectrogram**<br>
![](images/spec.png?raw=true)
<br>

## Feature Extraction
The next step involves extracting the features from the audio files which will help our model learn between these audio files.
For feature extraction we make use of the [**LibROSA**](https://librosa.github.io/librosa/) library in python which is one of the libraries used for audio analysis. 
<br>
![](images/feature.png?raw=true)
<br>
* The feature used to extract from are Mel-frequency cepstrum coefficients (MFCCs). This feature is used often used in voice recognition software because of the way MFCCs accurately envelope the the shape of the vocal tract. 
* While extracting the features, all the audio files have been sampled starting from 0.5 seconds and then timed for 3 seconds to get equal number of features.
* The sampling rate of each file is doubled to around 44 KHz. This allows each audio samples to get more features which will help classify the audio file while keeping noise at a minimum.
* The audio files were also seperated by emotion and sex.
<br>
The extracted features looks as follows:
<br>
<br>

![](images/feature2.png?raw=true)
<br>

These are array of values with lables appended to them. 

## Building Models

Since the project is a classification problem, **Convolution Neural Network** seems the obivious choice. We also built **Multilayer perceptrons** and **Long Short Term Memory** models but they under-performed with very low accuracies which couldn't pass the test while predicting the right emotions.
<br>
<br>
![](images/Model.PNG?raw=true)
<br>

Building and tuning a model is a very time consuming process. The idea is to always start small without adding too many layers just for the sake of making it complex. After testing out with layers, the model which gave the max validation accuracy against test data was little more than 70%
<br>
<br>
![](images/cnn.png?raw=true)
<br>

## Predictions

After tuning the model, tested it out by predicting the emotions for the test data. For a model with the given accuracy these are a sample of the actual vs predicted values.
<br>
<br>
![](images/predict.png?raw=true)
<br>

## Testing out with live voices.
In order to test out our model on voices that were completely different than what we have in our training and test data, we recorded our own voices with dfferent emotions and predicted the outcomes using the audiorecorder.ipynb. You can see the results below:
The audio contained a male voice which said **"This coffee sucks"** in a angry tone.
<br>
![](images/livevoice.PNG?raw=true)
<br>
<br>
![](images/livevoice2.PNG?raw=true)
<br>

**As you can see that the model has predicted the male voice and emotion accurately.**

## Conclusion

Building the model was a challenging task as it involved lot of trail and error methods, tuning etc. The model is very well trained to distinguish between male and female voices and it distinguishes with 100% accuracy. The model is still being tuned to detect emotions with more than 70% accuracy which is achievable by increasing the size of the dataset.

### Errata

Some advice on preparing this in a professional manner appears here.
