# Audio-Sep-from-Huggin-Face-
## Separate "Anything" You Describe
This work is be take from [Audio Sep](https://github.com/Audio-AGI/AudioSep) and a [demo HF](https://huggingface.co/spaces/Suniilkumaar/AudioSep) of the same model.
# NOTE: This is an anofficial implementation of [Audio Sep](https://github.com/Audio-AGI/AudioSep), but this work without Miniconda :)

![results](https://github.com/user-attachments/assets/b4b82f04-8cbe-4ddb-a45e-3cdcba4d74a3)

## Setup
Clone the repository:
```shell
git clone https://github.com/Brodvd/Audio-Sep---from-Huggin-Face---.git
```
Install the dependences (I used Python 3.10, but I think is the same):
```shell
pip install -r requirements.txt 
```

Create the folder `/checkpoint` and download the checkpoint in the folder from [here](https://huggingface.co/spaces/BroDvd/AudioSep/tree/main/checkpoint)
## Using
### For the pipiline
* run the file  `pipiline.py`  changing the files path
  * the file input should be in 32000 KHz, format  `.wav`
  * the file output will be in mono format

NOTE: this model use lot of memory of the computer, so for the old laptop like me if you give a input file > 1 minute it won't work.
### Demo Gradio
* run the file  `app.py`
* copy the link that will be appear in the debug on a browser
* use the model online (like Huggin Face)
## My personal valutation
### Description of the model
Audio Sep is a big model for the separation audio with natural language queries :

![image](https://github.com/user-attachments/assets/f383bf96-5c91-4fd7-9e2e-4be340eb5f47)

The model has two checkpoint, one for the text query and the other for the suorce separation, the first in  `.pt` and the second in  `.ckpt` .
### Discussion about the quality of the output
#### Using for songs and soundtrack (Voice and instruments)
I tested Audio Sep in a lot of cases even the same audio and I found myself in front of a really strange model. I included in my evaluation both songs and soundtracks with reverbs and other effects while trying to understand how the structure of the text query works best. So I tried to work a song with the usual stems (vocals, drums, bass, guitar) and typing "vocals" what I got was a bad result even if the voice unlike the other instruments remained unchanged, indeed emphasized. Then I tried on the same track to separate the guitar and he separated it very well. I then went to the soundtracks, I tested a track with percussion, violins and other things, I typed "percussion" and I did not get a clear separation but I tried with the same track to type "piano" and had better results on the percussion instrument. then I separated also tracks simpler with a bell and violins and typing "bell" did a great job. Finally I tried to separate the first seconds of "A Fistful of Dollars" and both the guitar and the whistle were separated very effectively.
## Conclusion
This model seems work with easy mixiture or also like a "denoiser", because it don't make destortion.
