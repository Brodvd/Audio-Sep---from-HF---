# Audio-Sep-from-Huggin-Face-
## Separate "Anything" You Describe
This work is be take from [Audio Sep](https://github.com/Audio-AGI/AudioSep) and a [demo HF](https://huggingface.co/spaces/Suniilkumaar/AudioSep) of the same model.
# NOTE: This is an anofficial implementation of [Audio Sep](https://github.com/Audio-AGI/AudioSep), but this work without Miniconda :)

![results](https://github.com/user-attachments/assets/b4b82f04-8cbe-4ddb-a45e-3cdcba4d74a3)

## Setup
Go to command prompt, navigate like this:
```shell
cd documents
```
and clone the repository:
```shell
git clone https://github.com/Brodvd/Audio-Sep---from-Huggin-Face---.git
```
Install the dependences in the file `requirements.txt`  (I used Python 3.10, but I think is the same):
```shell
pip install -r requirements.txt 
```

Create the folder `/checkpoint` and download the checkpoints in the folder from [here](https://huggingface.co/spaces/BroDvd/AudioSep/tree/main/checkpoint).
## Using
### For the pipiline
* run the file  `pipiline.py`  changing the files path and the text query
  * the file input should be in 32000 KHz, format  `.wav`
  * the file output will be in mono format

NOTE: this model use lot of memory of the computer, so for the old laptop like me (Windows 10 Home) if you give a input file > 1 it will work only with the chunk-based inference that have a few less quality:

```shell
inference(model, audio_file, text, output_file, device, use_chunk=True)
```

### Demo Gradio
* run the file  `app.py`
* copy the link that will be appear in the debug on a browser
* use the model online (like Huggin Face)

Obviously the same of the chunk-based inference if you want to have more speed.
## My personal valutation
### Description of the model
Audio Sep is a big model for the separation audio with natural language queries :

![image](https://github.com/user-attachments/assets/f383bf96-5c91-4fd7-9e2e-4be340eb5f47)

The model has two checkpoint, one for the text query and the other for the suorce separation, the first in  `.pt` and the second in  `.ckpt` .
### Discussion about the quality of the output
#### Files used for the evatulation 
You can see the [demo-page](https://audio-agi.github.io/Separate-Anything-You-Describe/) of the original project and [here](https://github.com/Brodvd/Audio-Sep---from-HF---/tree/Exemples-.wav/examples/My%20examples) you can find other examples in  `.wav`  that I tested.
#### Behaviour for songs and soundtrack (Voice and instruments)
I tested Audio Sep in a lot of cases even the same audio and I found myself in front of a really particular model. I included in my evaluation both songs and soundtracks with reverbs and other effects while trying to understand how the structure of the text query works best. 

So I tried to work a song with the usual stems (vocals, drums, bass, guitar) and typing "vocals" what I got was a bad result even if the voice unlike the other instruments remained unchanged, indeed emphasized. Then I tried on the same track to separate the guitar and he separated it very well. 

I then went to the soundtracks, I tested a track with percussion, violins and other things, I typed "percussion" and I did not get a clear separation from the other suorces but the percussion remained similar; instead I tried with the same track to type "piano" and had better results on the percussion instrument. 
Then I separated also tracks simpler with a bell and violins and typing "bell" did a great job. 
Finally I tried to separate the first seconds of "A Fistful of Dollars" and both the guitar and the whistle were separated very effectively.

![image](https://github.com/user-attachments/assets/95d9abae-df97-4bbf-9512-39d3cf41220f)

#### Behaviour for ambient sounds
For the ambient sounds instead I tried to reproduce with other cases the examples of the official [demo](https://audio-agi.github.io/Separate-Anything-You-Describe/), I started for example with a simple recording in the open air containing the verse of a pheasant mixed with noise and wanted to separate the pheasant. From here I understood immediately one thing: I typed "pheasant" and did not recognize the corresponding pattern but, since the sound is similar to the verse of a rooster, I typed "bantam" and separated it well working as an excellent denoiser.

Then I switched to a similar recording but with the presence of other sound sources (farm noises) along with the pheasant’s verse and had difficulty separating the sound because it was not prevalent over the rest. Finally I went to tracks of people talking recorded with the phone and I took the opportunity to see if indeed the model can separate sound events described in succession.

I must say that overall the only problem is the sharpness of the separation, for the rest it can recognize the tone of the person (whether it is man or woman) and recognize events in succession only if they are described in detail by associating an event with a single sound on the spectrogram.

![image](https://github.com/user-attachments/assets/0a56c3dc-de00-4ac7-99ca-8698627dd704)

#### How to give and use the text query of Audio Sep?

## Conclusion
Audio Sep has been trained on thousands of tagged YouTube clips, so on tracks that handle the open domain but definitely simpler than a soundtrack. In fact this model has great capacity of separation on audio tracks recorded in environment (typical case with some sound source prevailing and mixed noise in the background) But the training also explains that it is not focused on separating voices or musical instruments strictly as they need (voice especially) very detailed training files for each musical instrument .

What I found in my tests is that Audio Sep is a model that relies heavily on the spectrum of audio sources, so it looks more at their spectrographic form by matching training patterns to those present in the input audio. 

What is promising, however, is that, except in extreme cases where through special effects two different musical instruments have the same spectrum, Audio Sep never removes the pattern described in the text query and does not create large distortions but finds difficulties especially in complex tracks with many different sound sources when trying to separate the required pattern but fails to do so clearly and therefore often includes other sound sources together to the pattern of the text query.

### Audio Sep could with more focused training manage musical instruments better?
Nice question, the pre-trained model today in the case of a recording with 4 different patterns more or less constant separates the required pattern quite well even if not clearly, but if we take this talk about musical instruments is a bit different: Musical instruments are not an open domain, or rather they are not infinite as ambient sounds, so the way of training also changes.

 My answer is yes, because taking all the musical instruments it could each look for many audio tracks to cover many different situations and mix them together so that the training is focused on the separation of an orchestra, like the training done for a stems-separation model.
 
Small addition: the output file of this model is in mono format but if you break with audacity the stereo file into two mono channels and have them processed separately to Audio Sep, recomposing them you get back the separate stereo file.


## Cite the work done by Audio-Agi

If you found this tool useful, please consider citing
```bibtex
@article{liu2023separate,
  title={Separate Anything You Describe},
  author={Liu, Xubo and Kong, Qiuqiang and Zhao, Yan and Liu, Haohe and Yuan, Yi, and Liu, Yuzhuo, and Xia, Rui and Wang, Yuxuan, and Plumbley, Mark D and Wang, Wenwu},
  journal={arXiv preprint arXiv:2308.05037},
  year={2023}
}
```
```bibtex
@inproceedings{liu22w_interspeech,
  title={Separate What You Describe: Language-Queried Audio Source Separation},
  author={Liu, Xubo and Liu, Haohe and Kong, Qiuqiang and Mei, Xinhao and Zhao, Jinzheng and Huang, Qiushi, and Plumbley, Mark D and Wang, Wenwu},
  year=2022,
  booktitle={Proc. Interspeech},
  pages={1801--1805},
}
```



