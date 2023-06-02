---
title: "How to prep data for 3DUnet"
date: 2023-03-31 
categories: [Tutorial]
tags: []
---

# To prep data for 3DUNet you'll need to do follow these steps:

1. Copy the prepared 3dunet dir if you haven't already:

    `$ cp -R /home/kaegin63/aneurysm/3dunet-aneurysm .`

    This dir in theory should contain the basic things you need to get 3dunet up and training.
    as well as prepare data for 3dunet to use.   

    > Don't forget to run `source 3dunet-env/bin/activate` to activate the python virtual environment.  

2. Convert a nii dataset to a h5 dataset :

    Initially the 3dunet-aneurysm dir will have two folders of nii files. base_3d_aorta_scans has the original full dataset, and clean_dir has a subset of the nii files from base_3d_aorta_scans deemed to be cleaner than the rest.   

    To make a new h5 dataset for the training scripts. open nii_formatting.py in the editor of your choice and adjust the following variables as needed.

    ```python 
    data_path = './clean_dir' # the dir with the nii files you want to use
    output_dir = '80_20_64_images' # the dir that you want your finial h5 dataset to be in
    split = .80 # how much of the finial dataset will be for training or testing
    size_of_the_output_set = 64 # how many samples you from the original test set you want to be in your final dataset
    ```

    You then needed to run `python nii_formatting.py` to produce your desired h5 dataset

3. Point the training config file to the new data dir :

    Now that you have your h5 dataset you need to adjust your training config file. 

    In your 3dunet-aneurysm dir open `config_files/3DUnet_aneurysm/train_config.yml` in the editor of your choice.

    Then do ctrl - f for `train:` to find training data loader subsection, and under `file_paths:` add `- <PATH-TO-YOUR-DATASET>/train/`.
    
    you will also need to repeat this for the validation dataloader. 

    Do ctrl - f for `val:` to find validation data loader subsection, and under `file_paths:` add `- <PATH-TO-YOUR-DATASET>/test/`.

    When you run the training scripts they will try to load all the data you list in each dir that specify under file_paths. 

    > They can also do single h5 files if you specify the path down to a single file. 
