Retrieving Sequential Information for Non-Autoregressive Neural Machine Translation
==================================
PyTorch implementation of the models described in the paper [Retrieving Sequential Information for Non-Autoregressive Neural Machine Translation
](https://arxiv.org/abs/1906.09444 "Retrieving Sequential Information for Non-Autoregressive Neural Machine Translation
").

Dependencies
------------------
### Python
* Python 3.6
* PyTorch 0.4
* Numpy
* NLTK
* torchtext
* torchvision
* revtok
* multiset
* ipdb

### GPU
* CUDA (we recommend using the latest version. The version 8.0 was used in all our experiments.)

### Related code
* This code is based on [dl4mt-nonauto](https://github.com/nyu-dl/dl4mt-nonauto "dl4mt-nonauto"). We mainly modified the [`model.py`](https://github.com/ictnlp/RSI-NAT/model.py "model.py") (line 1103-1199).

Downloading Datasets
------------------
The original translation corpora can be downloaded from ([IWLST'16 En-De](https://wit3.fbk.eu/), [WMT'16 En-Ro](http://www.statmt.org/wmt16/translation-task.html), [WMT'14 En-De](http://www.statmt.org/wmt14/translation-task.html)). We recommend you to download the preprocessed corpora released in [dl4mt-nonauto](https://github.com/nyu-dl/dl4mt-nonauto/tree/multigpu "dl4mt-nonauto").

Before you run the code
------------------
Set correct path to data in `data_path()` function located in [`data.py`](https://github.com/ictnlp/RSI-NAT/data.py):

Training New Models
------------------
Train a NAT model using the cross-entropy loss. This process usually takes about 10 days.
#### IWSLT
```bash
$ sh train_iwslt.sh
```

#### WMT14 En-De
```bash
$ sh rf_wmt.sh
```
Finetuning (RF-NAT)
------------------
Take a checkpoint pre-trained non-autoregressive model and finetune the checkpoint using the RF-NAT algorithm. This process usually takes about 1 days.
If you want to use the origin REINFORCE, change the flag `--nat_finetune` to `--rf_finetune`.
#### IWSLT
```bash
$ sh rf_iwslt.sh
```

#### WMT14 En-De
```bash
$ sh rf_wmt.sh
```
Training the Length Prediction Model
------------------
Take a finetuned checkpoint and train the length prediction model. This process usually takes about 1 day.
#### IWSLT
```bash
$ sh tune_iwslt.sh
```

#### WMT14 En-De
```bash
$ sh tune_wmt.sh
```
Decoding
------------------
Decode the test set. This process usually takes about 20 seconds.
#### IWSLT
```bash
$ sh decode_iwslt.sh
```

#### WMT14 En-De
```bash
$ sh decode_wmt.sh
```
Citation
------------------
If you find the resources in this repository useful, please consider citing:
```
@article{Shao:19,
  author    = {Chenze Shao, Yang Feng, Jinchao Zhang, Fandong Meng, Xilin Chen, Jie Zhou},
  title     = {Retrieving Sequential Information for Non-Autoregressive Neural Machine Translation},
  year      = {2019},
  journal   = {arXiv preprint arXiv:1906.09444},
}
```
