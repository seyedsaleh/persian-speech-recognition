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

  <h3 align="center">word-recognition</h3>

  <p align="center">
    Simple word recognition using CNN on Raspberry Pi board 🗣
    <br />
    <a href="https://github.com/seyedsaleh/word-recognition"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://colab.research.google.com/drive/1T7FZd5krcsOHAki55z0GL2jeNbS7GuTq?usp=sharing">Demo Music Generation (Google Colab)</a>
    ·
    <a href="https://colab.research.google.com/drive/1bxy2XzbMsUhgLSDcQH_ElKL7K-dGGjD-?usp=sharing">Demo Multi-Instrument Music Generation (Google Colab)</a>
    .
    <a href="https://github.com/seyedsaleh/word-recognition/issues">Report Bug & Request Feature</a>
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
    <li><a href="#datasets">Datasets</a></li>
    <li><a href="#refereces">Refereces</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

<p> <img src="https://user-images.githubusercontent.com/47852354/141186269-d31ec094-8061-4edc-b862-8e1deb3da46f.png" width="600"> </p>  Generative adversarial networks have been proposed as a way of efficiently training deep generative neural networks. We propose a generative adversarial model that works on continuous sequential data, and apply it by training it on a collection of classical music. We conclude that it generates music that sounds better and better as the model is trained, report statistics on generated music, and let the reader judge the quality by downloading the generated songs.

Recently, generative neural networks have taken the stage for artistic pursuits, such as image generation and photo retouching. Another area where these deep learning networks are beginning to leave a mark is in music generation. In this project, our goal is to explore the use of **LSTM** and **GAN neural networks** to generate music that seems as if it were human-made.
By treating the notes and chords within **MIDI** files as discrete sequential data, we were able to train these two models and use them to generate completely new MIDI files. 

Listen to our results! :smile:

<p align="right">(<a href="#top">back to top</a>)</p>


### Built With

Major frameworks/libraries used to this project:

* [Python 3.8](https://www.python.org/)
* [Tensorflow , Keras](https://www.tensorflow.org/)
* [Midi2audio](https://github.com/bzamecnik/midi2audio)
* [Music21](https://web.mit.edu/music21/)
* [Numpy](https://numpy.org/)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- PARTS -->
## Parts

**MIDI format**
an acronym for Musical Instrument Digital Interface, a technical standard that describes a communications protocol, digital interface, and electrical connectors that connect a wide variety of electronic musical instruments, computers.


**Music21** is a powerful library in python whose tools are very helpful for creating, analysis and processing of audio files like songs, melodies and etc..
In this project, we have used this library for our purposes of converting the MIDI files into notes, categorizing of notes for preparing the training data, and choosing the playing instruments for the output of our GAN and converting it back to MIDI.


**MIDI Class:**
- Parser
- sequence preparation
- MIDI creation

**Parsing MIDI file and preparing the training data and preparing data for C-RNN-GAN network**
<p> <img src="https://user-images.githubusercontent.com/47852354/141293958-b829dce5-64e2-439b-b45b-4667608d13b6.png" width="650"> </p> 

**Model Class:**
- Discriminator
- Generator
- Train
- Plot loss function
- Save model

**Generative Adversarial Network (GAN) vs. LSTM**
<p> <img src="https://user-images.githubusercontent.com/47852354/141293644-9504c1c3-1713-4533-a91d-8e4637edd961.png" width="350">
<img src="https://user-images.githubusercontent.com/47852354/141293667-67f8be01-d6ad-4a91-8058-bb928048a771.png" width="250"> </p> 

**C-RNN-GAN Network Structure**
<p> <img src="https://user-images.githubusercontent.com/47852354/141293801-1402eb14-6e05-4ff4-a2eb-5af0abcbf239.png" width="400"> </p> 


The project has been done with aid of GPU Computing and the use of NVIDIA cuDNN and NVIDIA CUDA Toolkit. It helped us to use Tensorflow with GPU support for computing and learning with more compatibility.
The model has been trained on an **NVIDIA GeForce GTX 1080Ti GPU**.
**CUDA** is a parallel computing platform interface that allows software developers to use GPUs for ML computing.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- RESULTS -->
## Results
<p> <img src="https://user-images.githubusercontent.com/47852354/141289514-87b11009-2835-407f-8cf3-dc99ed860811.png" width="300"> </p> 

https://user-images.githubusercontent.com/47852354/141285440-be56d13f-abb4-4956-9ae3-c6845ed1fd12.mov

https://user-images.githubusercontent.com/47852354/141285431-a525b350-857f-470a-9465-7935a80a06d6.mov


<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- DATASETS -->
## Datasets


We will use our own dataset which we have collected for this project.
This database has been collected by **Telegram** messengers (social network), thanks its voice recording.
First we record voice data from about 250 different people varrying the sex, age and save these data, then we categorized each voice data to its specific group (labeling) and did the task of data cleaning and converting its format from **.ogg** to **.wav**. This dataset has been prepared after several days of efforts by a group of 10 people.


Each folder contains approximately 250 audio files for each word. The name of the folder is actually the label of those audio files. You can play some audio files randomly to get an overall idea.


<p align="right">(<a href="#top">back to top</a>)</p>




<!-- REFERENCES -->
## Refereces

[1] *Mogren, Olof. (2016). C-RNN-GAN: Continuous recurrent neural networks with adversarial training. [arXiv:1611.09904](https://arxiv.org/abs/1611.09904).* 

[2] *“Generating Music with GANs—An Overview and Case Studies” at ISMIR 2019 (November 4th at Delft, The Netherlands). [salu133445.github.io/ismir2019tutorial](https://salu133445.github.io/ismir2019tutorial/).* 

[3] *Goodfellow, Ian & Pouget-Abadie, Jean & Mirza, Mehdi & Xu, Bing & Warde-Farley, David & Ozair, Sherjil & Courville, Aaron & Bengio, Y.. (2014). Generative Adversarial Nets.  [ArXiv](https://arxiv.org/abs/1406.2661).* 

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Seyedmohammadsaleh Mirzatabatabaei - [@seyedsaleh](https://github.com/seyedsaleh) - seyedsaleh.edu@gmail.com


Project Link: [https://github.com/seyedsaleh/music-generator](https://github.com/seyedsaleh/word-recognition)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [x] Multi-instrument by partitioning and joining each part (Music21 Instrument package)
- [ ] Use offset, duration, velocity with pyPianoroll package
- [ ] UI mobile and desktop application to create music
- [ ] using CGANs network to avoid falchs

See the [open issues](https://github.com/seyedsaleh/word-recognition/issues) for a full list of proposed features (and known issues).

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
[contributors-shield]: https://img.shields.io/github/contributors/seyedsaleh/word-recognition.svg?style=for-the-badge
[contributors-url]: https://github.com/seyedsaleh/word-recognition/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/seyedsaleh/word-recognition.svg?style=for-the-badge
[forks-url]: https://github.com/seyedsaleh/word-recognition/network/members
[stars-shield]: https://img.shields.io/github/stars/seyedsaleh/word-recognition.svg?style=for-the-badge
[stars-url]: https://github.com/seyedsaleh/word-recognition/stargazers
[issues-shield]: https://img.shields.io/github/issues/seyedsaleh/word-recognition.svg?style=for-the-badge
[issues-url]: https://github.com/seyedsaleh/word-recognition/issues
[license-shield]: https://img.shields.io/github/license/seyedsaleh/word-recognition.svg?style=for-the-badge
[license-url]: https://github.com/seyedsaleh/word-recognition/blob/master/LICENSE.txt

