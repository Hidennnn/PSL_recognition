# Polish Sign Language  recognition

## What is it?
It is algorithm to detect 27 Polish Sign Language (PSL) static words from images.
In static words only hand shape is important - we do not care about movement.

## Technology
|    **Name**    | **Version** |
|:--------------:|:-----------:|
|    `Python`    |   3.8.13    |
|    `Keras`     |    2.9.0    |
| `scikit-learn` |    1.1.1    |
|    `pandas`    |    1.4.3    |
|    `numpy`     |   1.22.4    |
|  `matplotlib`  |    3.5.1    |
|   `seaborn`    |   0.11.2    |
|    `opencv`    |    4.6.0    |
|  `mediapipe`   |   0.8.10    |

## Results - test on "unknown" hand

| **Metric** |  **Result**  |
|:----------:|:------------:|
|  Accuracy  |    92.76%    |
|   Recall   |    92.64%    |
| Precision  |    92.90%    |

## Architecture

|        **Layer**         | **Activation**  | **Dropout** |
|:------------------------:|:---------------:|:-----------:|
| Input dense - 1035 nodes | LeakyReLU - 0.8 |     50%     |
|    Dense - 512 nodes     | LeakyReLU - 0.8 |     50%     |  
|     Dense - 64 nodes     | LeakyReLU - 0.8 |     50%     |
| Output dense - 27 nodes  |     Softmax     |     ---     |

## How does it work?
Firstly, the MediaPipe Holistic Solution detects characteristic points of hands and
pose. In the next steps only hands, elbows and shoulders points will be used. Then 
Euclidean distances between every point are calculated which are input for the Neural
Network.

## Which do signs be detected?
1. Digits (0-9)
2. Letters (a, b, c, e, i, l, m, n, o, s, t, v, w, x, y) 
3. Words (ja (I in Polish), ty (you in Polish), on/ona (he/she in Polish)

### Disclaimer
"0" and "o" is the same sign. "ty" means also "to jest" towards people 
(he is/she is). "on/ona" means also "to jest" towards things (it is).

## Modules

- augmentation.py - functions to make augmentation with flip, mirroring and resize.
- custom_exceptions.py - exceptions customized for project.
- custom_types.py - types customized for project.
- img_management.py - functions to make csv files with saved landmarks coordinates and distances.
- name_files.py - functions to rename photos and move to database.
- preprocessing.py - functions to make vectors and compute distances.
- utils.py - different functions to operate functions.

## How to use?
You just need to run program.py! On top of the program.py you can adjust configuration.

## Database
https://drive.google.com/drive/folders/1ffpiODeT87HVnRcQohv3iZg0k3i7kUay?usp=sharing - Google Drive where you can 
download vectors and distances which were used in projects. 

## Demo
![](https://github.com/Hidennnn/PSL_recognition/blob/main/demo.gif)

## Disclaimer
I'm aware that I should not use test set as validation set. I decided to that due to small amount of data, but nowadays,
I think it would be better to have smaller test set instead of not having validation set.
