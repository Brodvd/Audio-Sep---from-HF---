# Training
To training Audio Sep you shall install this dependences:

```shell
pip install tensorboard pyloudnorm
```

So to utilize your audio-text paired dataset:

1. Format your dataset to match our JSON structure in  `datafiles/template.json` , you have need of the pattern audio and the prompt of the pattern, like this:

```yaml
{
    "data": [
     {
      "wav": "path_to_audio_file",
      "caption": "textual_desciptions"
     }
    ]
}
```

2. Update the `config/audiosep_base.yaml` file by listing your formatted JSON data files under `datafiles` if you used more  `.json` . For example:

```yaml
data:
    datafiles:
        - 'datafiles/your_datafile_1.json'
        - 'datafiles/your_datafile_2.json'
        ...
```

Train AudioSep from scratch:
  ```python
  python train.py --workspace workspace/AudioSep --config_yaml config/audiosep_base.yaml --resume_checkpoint_path checkpoint/ ''
  ```

Finetune AudioSep from pretrained checkpoint:
  ```python
  python train.py --workspace workspace/AudioSep --config_yaml config/audiosep_base.yaml --resume_checkpoint_path path_to_checkpoint
  ```
A folder  `workspace`  will be create where you find the results of the training.
