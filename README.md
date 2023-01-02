## 本项目为天津大学神经网络与深度学习课程大作业



### 实验环境

conda==4.10.3

easydict==1.9

librosa==0.9.2

lmdb==1.3.0

nltk==3.7

opencv-python==4.6.0.66

Pillow==8.3.2

scikit-image==0.19.3

### 数据集下载

Download [bird](http://www.vision.caltech.edu/visipedia/CUB-200-2011.html) dataset and extract the images to `data/birds/`

### 运行方式

#### [DAMSM](https://github.com/taoxugit/AttnGAN) model includes a text encoder and an image encoder

- Pre-train DAMSM model for bird dataset:

```
python pretrain_DAMSM.py --cfg cfg/DAMSM/bird.yml --gpu 0
```

#### Our Model

- Train the model for bird dataset:

```
python main.py --cfg cfg/train_bird.yml --gpu 0
```

`*.yml` files include configuration for training and testing. To reduce the number of parameters used in the model, please edit DF_DIM and/or GF_DIM values in the corresponding `*.yml` files.

#### Pretrained DAMSM Model

- [DAMSM for bird](https://drive.google.com/file/d/1n-qKR7K4V-4oVC1GaGeIHLTQfIzPsTsE/view?usp=sharing). Download and save it to `DAMSMencoders/`

#### Pretained Lightweight Model 

- [Bird](https://drive.google.com/file/d/1ojDzj4zak0-L9tG48hSfN9FxibwjsS6V/view?usp=sharing). Download and save it to `models/`

### Testing

- Test our model on bird dataset:

```
python main.py --cfg cfg/eval_bird.yml --gpu 0
```

### Evaluation

- To generate images for all captions in the testing dataset, change B_VALIDATION to `True` in the `eval_*.yml`. 

### Code Structure

- code/main.py: the entry point for training and testing.
- code/trainer.py: creates the networks, harnesses and reports the progress of training.
- code/model.py: defines the architecture.
- code/attention.py: defines the spatial and channel-wise attentions.
- code/VGGFeatureLoss.py: defines the architecture of the VGG-16.
- code/datasets.py: defines the class for loading images and captions.
- code/pretrain_DAMSM.py: trains the text and image encoders, harnesses and reports the progress of training. 
- code/miscc/losses.py: defines and computes the losses.
- code/miscc/config.py: creates the option list.
- code/miscc/utils.py: additional functions.

## 实验结果

![image-20230102230526812](C:\Users\99345\AppData\Roaming\Typora\typora-user-images\image-20230102230526812.png)

​																												原始图片

 

​                                                         ![img](file:///C:\Users\99345\AppData\Local\Temp\ksohtml36768\wps2.jpg)			 

​													 this bird is white, black and yellow in color, with a small pointed beak.

 

​                                                          ![img](file:///C:\Users\99345\AppData\Local\Temp\ksohtml36768\wps3.jpg)                                               

​							this bird has a yellow crown all the way down to its back with a white underbelly and black tipped wings.