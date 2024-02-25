# Group 6 Stunning Animations from Still Images

## Team Members
|Name|Degree|Email|
|:---|:---:|---:|
| Rahul Govindkumar | Graduate Student | rusha@uncc.edu<br/>|
| Swapnil Hoskatti | Graduate Student | shoskatt@uncc.edu<br/>|
| Neha Dhamele | Graduate Student | ndhamele@uncc.edu<br/>|
| Nicolas Izquierdo | Undergraduate Student | nizquier@uncc.edu<br/>|
| Aiden Galloway | Undergraduate Student | agallo22@uncc.edu<br/>|

## Description

Character animation is a challenging task that requires a high degree of skill and expertise in traditional animation techniques. Recent advances in deep learning-based techniques have enabled the creation of realistic and flexible character animations from still images or videos. However, there are challenges to be addressed in terms of scalability and ethical concerns around the potential misuse of these technologies. In this paper, we explore state-of-the-art technique(s) for character animation using deep learning, including deepfakes and image animators, and identify their strengths and limitations.

## Architecture

![Architecture](https://github.com/swapnil-hoskatti/stunning-animations-from-still-images/blob/16c4d84ad5eaf1665e71db241d2b1252df8b30d9/Architecture.png?raw=true)

(Top) Training: Our model uses a pose detector P to create pose stick figures from video frames of the target subject.
We learn the mapping G alongside an adversarial discriminator D which attempts to distinguish between the “real” correspondences
(xt, xt+1),(yt, yt+1) and the “fake” sequence (xt, xt+1),(G(xt), G(xt+1)) . (Bottom) Transfer: We use a pose detector P to obtain
pose joints for the source person that are transformed by our normalization process Norm into joints for the target person for which pose
stick figures are created. Then we apply the trained mapping G

## Demo
Here, you can clearly see that the Rahul able to perform the same dance moves as Bruno Mars is doing in the Music Video " That's What I Like "
![demo](https://github.com/swapnil-hoskatti/stunning-animations-from-still-images/blob/16c4d84ad5eaf1665e71db241d2b1252df8b30d9/Export.gif?raw=true)

## Installation
Create a virtual environment using Anaconda or virtual env.
For Anaconda:
```
conda env create -f requirements.yml
```
For pip:
```
pip install -r requirements.txt
```
Note: CUDA 11.7 along with supported toolkit is required to run with GPU.

Download PoseEstimation model weights using the following link: 
[pose_model.pth](https://drive.google.com/file/d/1eXVSKMcbxJER57jNXKwfm-JcBbhEINmI/view?usp=sharing)
Move the model to folder "src/PoseEstimation/network/weight/"

## Usage

### Make Source
* Place the source video `mv.mp4` in the `./data/source/`directory.

* Execute the `make_source.py` script to generate labeled images and record the head coordinates. The results will be saved in `./data/source/test_label_ori/` and `./data/source/pose_source.npy`

* If you prefer to capture video using a camera, simply run the `./src/utils/save_img.py` script.

### Make Target

* Place the target video `mv.mp4` in `./data/target/`

* Execute the `make_target.py`. this will generate `pose.npy` that will be saves in  `./data/target/`, which contain the coordinate of faces

### Train GAN

* Execute the `train_pose2vid.py`

* `./checkpoints/` will contain the the training progress

* To continue last training, set `load_pretrain = './checkpoints/target/` in `./src/config/train_opt.py`

### Normalization

* Run `normalization.py`. This will rescale the label images,

### Generate Output

* Run `transfer.py` and get results in `./result`

### Make MP4

* Run `make_mp4.py` to generate mp4 from the results

## Authors and acknowledgment
[Everybody Dance Now](https://arxiv.org/pdf/1808.07371.pdf)

[Any-Body-Can-Dance](https://github.com/aman-arya/Any-Body-Can-Dance)

## License
MIT License