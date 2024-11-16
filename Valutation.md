## My personal valutation (still in progress)
### Discussion about the quality of the output of this checkpoint 
#### Files used for the evatulation 
You can see the [demo-page](https://audio-agi.github.io/Separate-Anything-You-Describe/) of the original project and [here](https://github.com/Brodvd/Audio-Sep---from-HF---/tree/Exemples-.wav/examples/My%20examples) you can find other examples in  `.wav`  that I tested.
#### Behaviour for songs and soundtrack (Voice and instruments)
I tested Audio Sep in a lot of cases even the same audio and I found myself in front of a really particular model. I included in my evaluation both songs and soundtracks with reverbs and other effects while trying to understand how the structure of the text query works best. 

So I tried to work a song with the usual stems (vocals, drums, bass, guitar) and typing "vocals" what I got was a bad result even if the voice unlike the other instruments remained unchanged, indeed emphasized. Then I tried on the same track to separate the guitar and he separated it very well. 

I then went to the soundtracks, I tested a track with percussion, violins and other things, I typed "percussion" and I did not get a clear separation from the other suorces but the percussion remained similar; instead I tried with the same track to type "piano" and had better results on the percussion instrument. 
Then I separated also tracks simpler with a bell and violins and typing "bell" did a great job. 
Finally I tried to separate the first seconds of "A Fistful of Dollars" and both the guitar and the whistle were separated very effectively.

![image](https://github.com/user-attachments/assets/95d9abae-df97-4bbf-9512-39d3cf41220f)

![image](https://github.com/user-attachments/assets/dac570b8-a9db-433d-aa68-2fb0506b9457)


#### Behaviour for ambient sounds
For the ambient sounds instead I tried to reproduce with other cases the examples of the official [demo](https://audio-agi.github.io/Separate-Anything-You-Describe/), I started for example with a simple recording in the open air containing the verse of a pheasant mixed with noise and wanted to separate the pheasant. From here I understood immediately one thing: I typed "pheasant" and did not recognize the corresponding pattern but, since the sound is similar to the verse of a rooster, I typed "bantam" and separated it well working as an excellent denoiser.

Then I switched to a similar recording but with the presence of other sound sources (farm noises) along with the pheasant’s verse and had difficulty separating the sound because it was not prevalent over the rest. Finally I went to tracks of people talking recorded with the phone and I took the opportunity to see if indeed the model can separate sound events described in succession.

I must say that overall the only problem is the sharpness of the separation, for the rest it can recognize the tone of the person (whether it is man or woman) and recognize events in succession only if they are described in detail by associating an event with a single sound on the spectrogram.

![image](https://github.com/user-attachments/assets/0a56c3dc-de00-4ac7-99ca-8698627dd704)

#### How to give and use the text query of Audio Sep?
The text query can vary a lot, from simple "guitar" to more complex requests like "a door that slams and then closes", and there isn't generally a right and wrong, each case is a bit 'to itself. 

The operation of the model is definitely influenced by the training since every track has been tagged but obviously the text query of Audio Sep cannot be compared to Chat Gpt.
Moreover, although it was trained on large datasets to simulate the open domain, it was “basic” training since the model works best if you generalize the text query (e.g. instead of “owl” write “bird” or instead of “gong” write “percussion” or “bell”).

In summary the best method to use Audio Sep is to generalize the text query based on the spectrophogram characteristics.

## Conclusion
Audio Sep has been trained on thousands of tagged YouTube clips, so on tracks that handle the open domain but definitely simpler than a soundtrack. In fact this model has great capacity of separation on audio tracks recorded in environment (typical case with some sound source prevailing and mixed noise in the background) but the mistake one can make when using this model is to regard it as a popular stem separator, but this is not the same thing, infact the training also explains that it is not focused on separating voices or musical instruments strictly as they need (voice especially) very detailed training files for each pattern.

What I found in my tests is that Audio Sep is a model that relies heavily on the spectrum of audio sources, so it looks more at their spectrographic form by matching training patterns to those present in the input audio. 

What is promising, however, is that, except in extreme cases where through special effects two different musical instruments have the same spectrum, Audio Sep never removes the pattern described in the text query and does not create large distortions but finds difficulties especially in complex tracks with many different sound sources when trying to separate the required pattern but fails to do so clearly and therefore often includes other sound sources together to the pattern of the text query.

### Audio Sep could with more focused training manage musical instruments better?
Nice question, the pre-trained model today in the case of a recording with 4 different patterns more or less constant separates the required pattern quite well even if not clearly, but if we take this talk about musical instruments is a bit different: Musical instruments are not an open domain, or rather they are not infinite as ambient sounds, so the way of training also changes.

So maybe yes, because taking a lot of the musical instruments it could each look for many audio tracks to cover many different situations and mix them together so that the training is focused on the separation of an orchestra, like the training done for a stems-separation model.
 
Small addition: the output file of this model is in mono format but if you break with audacity the stereo file into two mono channels and have them processed separately to Audio Sep, recomposing them you get back the separate stereo file.
