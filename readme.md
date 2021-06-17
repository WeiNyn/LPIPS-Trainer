# LPIPS Trainer

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

The source code for training LPIPS (perceptual similarity) in jnd type dataset, including

- Model and DataModule wrapper in pytorch lightning
- Training function with earlystoping, tensorboard support

## Requirements

- Torch
- Pillow
- numpy
- Torchvison
- Pytorch lightning

## Setting

Class Setting() stores all the training setting

```python
class Setting:
    model=dict(
        net='alex',
        version='0.1',
        lr=0.01,
        step_size=30,
        gamma=0.1,
        beta=0.5
    ) #LPIPS initiation params
    data_module=dict(
        # folder='/home/HuyNguyen/AITest/120_samples_database_cut',
        train_folder='train/',
        test_folder='test/',
        train_batch_size=64,
        test_batch_size=64,
        train_len=1000,
        test_len=240,
        random_size=(150, 512),
        resize_size=256
    ) #DataModule params
    checkpoint = dict(
        save_top_k=3,
        monitor='val_loss'
    )
    logger = dict(
        name='pattern'
    )
    early_stopping = dict(
        enable=True,
        monitor='val_loss',
        patience=10
    )
    trainer=dict(
        max_epochs=10000,
        gpus=1,
        profiler='simple'
    )
```

## Usage

Change the train_folder and test_folder in Setting class, the folder must follow the ImageFolder dataset format.

You can change the train souce code for replacing the resnet18 with resnet50, se source code implementation for mor details

Tensorboard log stored at __lightning_logs/__

Checkpoint stored at __checkpoints/__

Run training code by:

```sh
python src/train/trainer.py
```

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
