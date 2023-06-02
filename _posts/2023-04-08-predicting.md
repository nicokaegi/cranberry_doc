---
title: "How to generate predictions with 3dunet"
date: 2023-03-31 
categories: [Tutorial]
tags: []
---

# To generate a new aorta prediction from 3dunet do the following

1. prepare your test config file :

    > if you haven't already see the data prep tutorial to see how to 
    > how to prep data into h5 files for 3dunet to use.

    So in the editor of your choice open up `config_files/3DUnet_aneurysm/test_config.yml`. You're are going to need to edit at least two lines.

    First edit `model_path:` with the path to your desired model weights that your model produced during training. 

    Second edit `file_paths:` with the your data dir of your choice. 

    > you may also want to edit `output_dir: OUTPUT_DIR` to something more meaningful

2. Predict with the model :

    Similar to `train3dunet`, `predict3dunet` requires  a test.yaml config file in order to know what to do.
    so to get the predictions run 

    `$ predict3dunet --config <CONFIG>`

3. Turn h5 files to nii images : 

    The current training scripts output into h5 files, so in order to get viewable h5 files run the following in 3dunet-aneurysm.

    `python nii_h5.py <path to your h5 dir>/*`

    What this script is doing is it takes all the h5 files in your chosen dir and turn them into nii files. 

    > random tip : The star at the end of `<path to your h5 dir>/*` is bash short hand for all the files in a dir.  
    > for more info on bash short hand go [here](https://www.baeldung.com/linux/bash-globbing)


    Optionally you can also do something like `python nii_h5.py -t .5 <path to your h5 dir>/*` to impose a threshold unto your images. 

