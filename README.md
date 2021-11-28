<div id="top"></div>


<!-- PROJECT SHIELDS -->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
<!-- PROJECT LOGO -->
<br />
<div align="center">

  <h3 align="center">persian-speech-recognition</h3>

  <p align="center">
    Simple single persian word speech recognition using CNN on Raspberry Pi board 🗣
    <br />
    <a href="https://github.com/seyedsaleh/persian-speech-recognition"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://colab.research.google.com/drive/1mlSL36sGjiHFRqwwSazPifH6K6O7bxf4?usp=sharing">Demo persian word speech recognition (Google Colab)</a>
    .
    <a href="https://github.com/seyedsaleh/persian-speech-recognition/issues">Report Bug & Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary> 
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li><a href="#parts">Parts</a></li>
    <li><a href="#results">Results</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#dataset">Dataset</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## About The Project

<p> <img src="https://user-images.githubusercontent.com/47852354/143776840-15ead278-2b95-4718-9751-b57c5a18693f.png" width="600"> </p>  


In this project, everything starts from a spoken speech from which features are extracted to recognize which word was said (which turns into a classification task). The end goal is to accurately identify a set of predefined words from short audio clips.

There are six classes to recognize. There is no problem adding as much as you may wish. You should change the number of model category output and input dataset labels a bit.

For instance, the task in this project will be to classify audio between six words in the Farsi language (words meaning in the bracket):
*   Garm [Hot]
*   Sard [Cold]
*   Roshan [Bright]
*   Tarik [Dim]
*   Khodkar [Automatic]
*   Dasti [Manual]

Although single word speech recognition is not suitable for continuous speech recognition, it could be used to build a voice assistant or bot. To show this capability, we have implemented the algorithm on the Raspberry Pi board.

Look at our result! :smile:

<p align="right">(<a href="#top">back to top</a>)</p>


### Built With

Major frameworks/libraries used to this project:

* [python 3.8](https://www.python.org/)
* [tensorflow , keras](https://www.tensorflow.org/)
* [gpiozero]( https://gpiozero.readthedocs.io/en/stable/)
* [librosa](https://librosa.org/doc/latest/index.html)
* [numpy](https://numpy.org/)
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- PARTS -->
## Parts

**Data preparation and augmentation**

Due to the lack of data in the collected database, we will add some *noise* to each data and use it as new data for network training. The extra noise power is calculated according to the power of each signal so that the audio signal is not completely damaged.

In this way, we will have about **500** data for each word to train our word recognition network.
We will use one audio channel (mono) to read each voice. Thus, for each sound, we will have a signal with a specific sampling frequency; the sampling frequency of the input dataset signals is **54,000 Hz,** which we did not change.

To clear the data, we read the zero values ​​after reading the audio signals from both sides. (trimming)

Finally, we sorted data by numbers, and the original audio and the noise files are stored in a folder with the word name as the label.


**Pre-processing**

<p> <img src="https://user-images.githubusercontent.com/47852354/143778553-c23df68f-26c6-49c4-a922-e246680864c7.png" width="500"> </p> 

We have two critical problems for preparing data to feed into the neural network.

1.   We can't just feed an audio file to a CNN. That's outrageous!
2.   We need to prepare a fixed size vector for each audio file for classification.

> What's the solution?

1.   We could use embedding to overcome this problem. An embedding is a mapping from discrete objects, such as words vectors of real numbers.
There are a lot of techniques and python packages for audio feature extraction. We use the most obvious and simple one, **MFCC encoding**, which is super effective for working with speech signals.

2.   To overcome this problem, all we need to do is pad the output vectors with a constant value of 0.
MFCC vectors might vary in size for different audio inputs; CNN can't handle sequence data, so we need to prepare a fixed size vector for all audio files.


*MFCC (Mel Frequency Cepstral Coefficients): In short, In sound processing, the Mel-frequency cepstrum (MFC) represents the short-term power spectrum of a sound, based on a linear cosine transform of a log power spectrum on a nonlinear Mel scale of frequency.*

**Process**

We will process the signal and get its **MFCC**, so finally, we are pooling signal with 0 to the size of predefined *max_width*. Then, we read all sound files from each labeled directory and do the mfcc transform, then save the mfcc created matrices in a .npy file named after the name of the label to use for the training network.


**Model**

We use a Convolutional Neural Network (CNN) with one-dimensional convolutions on the raw audio waveform to classify samples. 

<p> <img src="https://user-images.githubusercontent.com/47852354/143780016-d9ce88f3-19bf-4c09-9b04-2daf39e9c5d3.png" width="500"> </p> 



**Raspberry Pi code**

<p> <img src="https://user-images.githubusercontent.com/47852354/143778569-0be4680f-28d1-4984-909a-b0af11f01423.png" width="500"> </p> 


<p align="right">(<a href="#top">back to top</a>)</p>


<!-- RESULTS -->
## Results

The model achieves **99.73%** accuracy on the validation set. The results show that the model can predict samples of words it has seen during training with high accuracy. Still, it somewhat struggles to generalize to terms outside the training data scope and extremely noisy samples.

<p> <img src="https://user-images.githubusercontent.com/47852354/143778330-22752161-0207-4610-950b-5f59015621ef.png" width="300"> </p> 


<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- DATASETS -->
## Dataset


We will use our own dataset which we have collected for this project.
This database has been collected by **Telegram** messengers (social network), thanks its voice recording.
First we record voice data from about 250 different people varrying the sex, age and save these data, then we categorized each voice data to its specific group (labeling) and did the task of data cleaning and converting its format from **.ogg** to **.wav**. This dataset has been prepared after several days of efforts by a group of 10 people.

Each folder contains approximately 250 audio files for each word. The name of the folder is actually the label of those audio files. You can play some audio files randomly to get an overall idea.


<p align="right">(<a href="#top">back to top</a>)</p>




<!-- CONTACT -->
## Contact

Seyedmohammadsaleh Mirzatabatabaei - [@seyedsaleh](https://github.com/seyedsaleh) - seyedsaleh.edu@gmail.com


Project Link: [https://github.com/seyedsaleh/persian-speech-recognition](https://github.com/seyedsaleh/persian-speech-recognition)

<p align="right">(<a href="#top">back to top</a>)</p>


---
<div align="center">
<p>
 <img src="https://user-images.githubusercontent.com/47852354/138564509-b5dffb4e-f48b-4db5-b8a4-1385ef2b22c8.png" width="110">
 <img src="https://user-images.githubusercontent.com/47852354/138607395-e18bfc7a-204c-495a-914f-bd5cf8436ca4.jpg" width="70">
</p>
</div>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/seyedsaleh/persian-speech-recognition.svg?style=for-the-badge
[contributors-url]: https://github.com/seyedsaleh/persian-speech-recognition/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/seyedsaleh/persian-speech-recognition.svg?style=for-the-badge
[forks-url]: https://github.com/seyedsaleh/persian-speech-recognition/network/members
[stars-shield]: https://img.shields.io/github/stars/seyedsaleh/persian-speech-recognition.svg?style=for-the-badge
[stars-url]: https://github.com/seyedsaleh/persian-speech-recognition/stargazers
[issues-shield]: https://img.shields.io/github/issues/seyedsaleh/persian-speech-recognition.svg?style=for-the-badge
[issues-url]: https://github.com/seyedsaleh/persian-speech-recognition/issues
[license-shield]: https://img.shields.io/github/license/seyedsaleh/persian-speech-recognition.svg?style=for-the-badge
[license-url]: https://github.com/seyedsaleh/persian-speech-recognition/blob/master/LICENSE.txt

