---
title: "How to run 3DUNet"
date: 2023-04-07
categories: [Tutorial]
tags: []
---


# To run 3DUNet you'll need to do follow these steps:

1. Copy the prepared 3dunet dir :

    `$ cp -R /home/kaegin63/aneurysm/3dunet-aneurysm .`

    This dir in theory should contain the basic things you need to get 3dunet up and training.
    as well as prepare data for 3dunet to use. 

    > random tip : Since programers are lazy by nature your standard linux terminal has a number of short cuts for you to use. 
    >  a `.` by its self is bash short hand for this current directory 

    >so `$ cp -R /home/kaegin63/aneurysm/3dunet-aneurysm .` actually means `$ cp -R /home/kaegin63/aneurysm/3dunet-aneurysm <this current dir>`


2. Activate the virtual environment :

    `$ source 3dunet-env/bin/activate`

    In this python virtual environment you should find all the libraries necessary to run 3dunet.
    as well as the bash commands to start training

3. (optional) Auto activate the environment :

    you can have your have this environment activate automatically upon logging.

    first open ~/.bashrc in the editor of your choice. Then add following to the end of your .bashrc

    `source <path-to-3dunet-env>/3dunet-env/bin/activate` 

4. Start model training :

    `$ train3dunet --config <CONFIG>`

    This command will start training a 3DUNet model using a specified training.yaml config file. 
    Within each config file contains the settings for the models training.

    > The latest config file I used for training was in 3DUnet_aneurysm - nico 




