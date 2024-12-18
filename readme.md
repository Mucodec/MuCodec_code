# MuCodec: Ultra Low-Bitrate Music Codec


This is the official repository for the paper titled "MuCodec: Ultra Low-Bitrate Music Codec," submitted to ICME 2025. Due to the anonymous review process, we have temporarily kept the repository anonymous. In the meantime, you can find a demo page [here](https://mucodec.github.io/Mucodec/).

In this repository, we provide the Mucodec model, inference scripts, and the checkpoint that has been trained on the Million Song Dataset. Specifically, we have released the model and inference code corresponding to the lowest bitrate of 0.35 kbps as mentioned in the paper, to demonstrate the effectiveness of our work.


MuCodec supports 48kHz, dual-channel (stereo) audio reconstruction. If the original audio is in a different format, it will first be converted to 48kHz, dual-channel audio.

## Installation

You can install the necessary dependencies using the `requirements.txt` file with Python 3.8.12:

```bash
pip install -r requirements.txt
```

Due to storage limitations, we have saved the model checkpoints on Hugging Face at https://huggingface.co/MuCodec/mucodec/tree/master. You can easily download the models from Hugging Face and save them in the following directories:

- Save `audioldm_48k.pth` in the `tools` folder.
- Save `muq.pt` in the `muq_dev` folder.
- Save `mucodec.pt` in the `ckpt` folder.

Please note that all three checkpoints must be downloaded completely for the model to load correctly. The final file paths should be:

```
tools/audioldm_48k.pth
muq_dev/muq.pt
ckpt/mucodec.pt
```


## Inference

To run inference, use the following command:

```bash
python3 generate.py
```

We have provided a sample song `test.wav`, randomly sampled from the Million Song Dataset, in the `test_wav` folder. The default input path is `test_wav/test.wav`, and the output path for the reconstructed audio is `reconstruct/test.wav`.

In the `generate.py` file, we have implemented several functions to facilitate the music compression and reconstruction process. You can easily obtain compressed tokens from audio using the `sound2code` function, and reconstruct the audio from tokens using the `code2sound` function.

## Note

Please note that the open-sourced model was trained solely on the Million Song Dataset. Considering the quality issues of this dataset, the open-sourced model may not achieve the same performance as demonstrated in the demo. Unfortunately, due to copyright restrictions, we are unable to release the checkpoints trained on additional datasets. However, you can use your own dataset to further train the model and achieve better results.

## License

The code in this repository is released under the MIT license as found in the [LICENSE](LICENSE) file.

The model weights (muq.pt, mucodec.pt) in this repository are released under the CC-BY-NC 4.0 license, as detailed in the [LICENSE_weights](LICENSE_weights) file. 
