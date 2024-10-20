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
### Demo Gradio
* run the file  `app.py`
* copy the link that will be appear in the debug on a browser
* use the model online
## My personal valutation
### Description of the model
Audio Sep is a big model for the separation audio with natural language queries :

![image](https://github.com/user-attachments/assets/f383bf96-5c91-4fd7-9e2e-4be340eb5f47)

The model has two checkpoint, one for the text query and the other for the suorce separation, so the interface will be like this:

![image](https://github.com/user-attachments/assets/06bd0faf-d5d1-4628-ab78-d7845d78e2d5)


### What is the quality of the output
## Conclusion
This model seems work with easy mixiture or also like a "denoiser", because it don't make destortion.
