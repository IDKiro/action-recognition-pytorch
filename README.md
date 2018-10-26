# Action Recognition PyTorch

The network are based on CNNs and LSTMs.

[简体中文](docs/README-zh.md)

## Environment

Python 3.6.5 (Anaconda 5.2.0):

[https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)

pytorch 0.4.1 (CUDA 9.0):

[https://pytorch.org/](https://pytorch.org/)

## Data

The training dataset structure:

```
~/
  data/
    train_data/
      .../ (directories of class names)
        .../ (directories of video names)
          ... (jpg files)
    valid_data/
      .../ (directories of class names)
        .../ (directories of video names)
          ... (jpg files)
    save_model/
      save_100.pth
```

The test dataset structure:

```
~/
  test_data/
    .../ (directories of class names)
      .../ (directories of video names)
        ... (jpg files)
```

The data structure of the video training dataset:

```
video_data/
      .../ (directories of class names)
        ... (avi files)
```

Use `video2jpg.py` under the `utils` folder to convert avi to jpg:

```
python video2jpg.py video_root_directory image_root_directory
```

Use `split_data.py` to move some of the training dataset to a validation dataset:

```
python split_data.py train_root_directory valid_root_directory
```

## Start

Use the following command to train the model:

```
python train.py data
```

Optional parameters of command:

```
--model DIR           path to model
--arch ARCH           model architecture (default: alexnet)
--lstm-layers LSTM    number of lstm layers (default: 1)
--hidden-size HIDDEN  output size of LSTM hidden layers (default: 512)
--fc-size FC_SIZE     size of fully connected layer before LSTM (default:
                      1024)
--epochs N            manual epoch number (default: 100)
--lr LR               initial learning rate (default: 0.001)
--optim OPTIM         optimizer (default: sgd)
--momentum M          momentum (default: 0.9)
--lr-step LR_STEP     learning rate decay frequency (default: 30)
--batch-size N        mini-batch size (default: 1)
--weight-decay W      weight decay (default: 1e-4)
--workers N           number of data loading workers (default: 8)
```

Use the following commands to test:

```
python test.py data/save_model/model_best.pth.tar test_data
```

## Network

This project is based on CNNs and LSTMs. 

<div align="center">
  <img src="imgs/lstm.jpg">
</div>

## Reference

[https://github.com/chaoyuaw/pytorch-coviar.git](https://github.com/chaoyuaw/pytorch-coviar.git)
