# DINet: Deformation Inpainting Network for Realistic Face Visually Dubbing on High Resolution Video (AAAI2023)
![在这里插入图片描述](https://img-blog.csdnimg.cn/178c6b3ec0074af7a2dcc9ef26450e75.png)
[Paper](https://fuxivirtualhuman.github.io/pdf/AAAI2023_FaceDubbing.pdf) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     [demo video](https://www.youtube.com/watch?v=UU344T-9h7M&t=6s)  &nbsp;&nbsp;&nbsp;&nbsp; Supplementary materials


# 🤔 How to achive this boost in inference latency?

To achieve this, several changes were implemented:
- Removed DeepSpeech and utilized wav2vec for instant feature extraction, leveraging the speed and power of torch.
- Trained a lightweight model to map the wav2vec features to DeepSpeech, maintaining the existing process.
- Enhanced frames extraction for improved speed.
- These adjustments contribute to a reduction of up to 60% in inference latency compared to the original implementation, all while maintaining quality.

Additionally, Docker has been introduced to facilitate faster, simpler, and more automated facial landmarks extraction.

Tested on:
- Windows 11
- Python version >= 3.9

# 📖 Prerequisites
To get started, follow these steps:

- Download the resources (asserts.zip) n [Google drive](https://drive.google.com/file/d/1FHpYJqGrIKsItG313aokXes03qJxFyxg/view?usp=share_link). Unzip the file and place the directory in the current directory (./). This zip file includes the model for mapping wav2vec to deepspeech, beside all other models.


## Install Instructions

Set up a Conda environment by executing the following commands.

```
  conda create -n dinet python=3.9
  conda activate dinet
```

Clone repository

```
  git clone https://github.com/illeng/DINet_optimized_Win.git
  cd DINet
```

Install Dependencies

```
  pip install -r requirements.txt
```

Install tensorflow 2.5.0

```
  pip install tensorflow==2.5.0
```

Installing pysoundfile

```
  conda install -c conda-forge pysoundfile
```


# 🚀 Inference

## Run inference with example videos: 

```
python inference.py --mouth_region_size=256 --source_video_path=./asserts/examples/testxxx.mp4 --source_openface_landmark_path=./asserts/examples/testxxx.csv --driving_audio_path=./asserts/examples/driving_audio_xxx.wav --pretrained_clip_DINet_path=./asserts/clip_training_DINet_256mouth.pth 
```

Use [OpenFace](https://github.com/TadasBaltrusaitis/OpenFace) to detect smooth facial landmarks of your custom video..


## Acknowledge
The AdaAT is borrowed from [AdaAT](https://github.com/MRzzm/AdaAT). The deepspeech feature is borrowed from [AD-NeRF](https://github.com/YudongGuo/AD-NeRF). The basic module is borrowed from [first-order](https://github.com/AliaksandrSiarohin/first-order-model). Thanks for their released code.
