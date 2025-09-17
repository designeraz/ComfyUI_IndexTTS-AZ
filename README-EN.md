[中文](README.md) | [English](README-EN.md) 

# IndexTTS Voice Cloning Node for ComfyUI

Very high voice cloning quality, extremely fast, supports Chinese and English, and custom voice tones.

## 📣 Updates

[2025-09-17]⚒️: Fixed the dependency issue with transformers

[2025-05-30]⚒️: Released v1.2.0. **Supports two-person dialogue, speaker preview, normal pynini installation on Windows, no longer a crippled TTS version!**

`IndexTTS 正式发布1.5 版本了，效果666,晕XUAN4是一种GAN3觉,我爱你！,I love you!,“我爱你”的英语是“I love you”,2.5平方电线,共465篇，约315万字,2002年的第一场雪，下在了2003年.`

https://github.com/user-attachments/assets/b67891f2-0982-4540-8c3b-1a870305466f

[2025-05-14]⚒️: Supports v1.5. Download and rename models to the `ComfyUI\models\TTS\Index-TTS` path:
- https://huggingface.co/IndexTeam/IndexTTS-1.5/blob/main/bigvgan_generator.pth  → `bigvgan_generator_v1_5.pth`
- https://huggingface.co/IndexTeam/IndexTTS-1.5/blob/main/bpe.model → `bpe_v1_5.model`
- https://huggingface.co/IndexTeam/IndexTTS-1.5/blob/main/gpt.pth → `gpt_v1_5.pth`

[2025-05-02]⚒️: DeepSpeed acceleration available, requires DeepSpeed installation. For Windows, see [DeepSpeed Installation](https://github.com/deepspeedai/DeepSpeed/blob/master/blogs/windows/08-2024/chinese/README.md). Acceleration is not significant.

[2025-04-30]⚒️: Released v1.0.0.

## Usage

Important parameter descriptions (other less important parameters will not be introduced one by one):
- `max_mel_tokens`: Controls the length of the generated speech. This parameter needs to be increased for long texts.
- `max_text_tokens_per_sentence`: Maximum number of tokens per sentence. Smaller values lead to faster inference speed, but consume more memory and might affect quality.
- `sentences_bucket_max_size`: Maximum capacity for sentence bucketing. Larger values lead to faster inference speed, but consume more memory and might affect quality.
- `fast_inference`: Enable fast inference.
- `custom_cuda_kernel`: Enable custom CUDA kernel. The CUDA kernel extension will be built automatically on the first run.
- `dialogue_audio_s2`: The second audio for two-person dialogue. If this audio is input, dialogue mode will be automatically enabled. In dialogue mode, the input text must be as follows ([S1] indicates the first speaker, [S2] indicates the second speaker):
```
[S1] 轻喘像风掠过耳畔， 
[S2] 你靠近时，连呼吸都慢了半拍。
[S1] 指尖在我锁骨上游移， 
[S2] 仿佛试探一扇未曾开启的门。
```

- Loading Audio:

![image](https://github.com/billwuhao/ComfyUI_IndexTTS/blob/main/images/2025-04-30_19-22-46.png)

- Preview Speaker:

I will unify all speaker audios for TTS nodes into the `ComfyUI\models\TTS\speakers` path. These nodes include `IndexTTS, CSM, Dia, KokoroTTS, MegaTTS, QuteTTS, SparkTTS, StepAudioTTS`, etc.

![image](https://github.com/billwuhao/ComfyUI_IndexTTS/blob/main/images/2025-05-30_22-30-05.png)

- Two-person Dialogue:

![image](https://github.com/billwuhao/ComfyUI_IndexTTS/blob/main/images/2025-05-30_22-15-23.png)

## Installation

- **Windows**: First, install the following dependencies:

Download the pynini wheel for the corresponding Python version from [pynini-windows-wheels](https://github.com/billwuhao/pynini-windows-wheels/releases/tag/v2.1.6.post1).

Example:
```
D:\AIGC\python\py310\python.exe -m pip install pynini-2.1.6.post1-cp3xx-cp3xx-win_amd64.whl
D:\AIGC\python\py310\python.exe -m pip install importlib_resources
D:\AIGC\python\py310\python.exe -m pip install WeTextProcessing>=1.0.4 --no-deps
```

- **Linux**, **Mac**, **Windows**:
```
cd ComfyUI/custom_nodes
git clone https://github.com/billwuhao/ComfyUI_IndexTTS.git
cd ComfyUI_IndexTTS
pip install -r requirements.txt

# python_embeded
./python_embeded/python.exe -m pip install -r requirements.txt
```

## Model Download

- Models need to be manually downloaded to the `ComfyUI\models\TTS\Index-TTS` path:

The [Index-TTS](https://huggingface.co/IndexTeam/Index-TTS/tree/main) structure is as follows:

```
bigvgan_generator.pth
bpe.model
gpt.pth
```

## Acknowledgements

- [index-tts](https://github.com/index-tts/index-tts)
