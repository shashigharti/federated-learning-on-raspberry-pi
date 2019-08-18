Project based on https://blog.openmined.org/federated-learning-of-a-rnn-on-raspberry-pis/

This README contains information about my process to run the project.

## My Setup
 - Windows 10 Pc
 - Raspberry Pi Model 3B
 - Mouse
 - Tv and HDMI cable
 - Local WiFi Network
 
## PySyft on the Raspberry
 - ### Initial setup
   - Download and boot the Raspberry with the latest Raspbian image. I installed Raspbian Buster with desktop which comes with Python 3.7.3
   - I did not have a keyboard to setup the WiFi on the Raspberry, just a mouse, so I changed my WiFi password to "webstore", which is a word that you can copy/paste if you open Chromium and click on the store :v.
   With that you will be able to connect to your WiFi network and enable SSH and VNC.
   - Connect through SSH and install a virual keyboard on the Raspberry just in case:
  https://raspberrypi.stackexchange.com/questions/41150/virtual-keyboard-activation
 - ### Python
    - If your Python3 version is higher than 3.6.7, there is no need to download and build Python as the guide mentions.
 - ### Pytorch 1.0.0
    - You can download an build Pytorch 1.0.0 if you have a good SD card and luck.
      I had a lot of troubles trying to build Pytorch so I was able to find a wheel for Raspberry:
      
      https://github.com/pytorch/pytorch/issues/22898
      
      Also @Suparna S Nair uploaded the file to her drive:
      
      https://drive.google.com/drive/folders/1anJ-P-IAbMFdB9D1LEH6Tx7fBW7MP8DU
    - You can open the links in Chromium on the Raspberry or you can SSH and download the files with curl -O <file_url>.
    Then just pip3 install <wheel_file>
    - Once you have pytorch installed you have to install Torch vision 0.2.2.post3 as well:
    
      pip3 install torchvision==0.2.2.post3
 - ### PySyft 0.1.13a1
    - Now for PySyft the trick is to install it without dependencies:
      
      pip3 install syft==0.1.13a1 --no-dependencies
    - Then install the missing dependencies mentioned in the PySyft GitHUb project, in requirements.txt:
      
      https://github.com/OpenMined/PySyft/blob/dev/requirements.txt
       
      pip3 install Flask flask-socketio lz4 websocket-client websockets zstd msgpack
      
   You should be good to go on the Raspberry by now, just be sure to validate the correct installation of each component as the guide mentions.
 - ### Running the worker servers on the Raspberry
    - One important thing is that the project guide makes a mistake calling run_websocket_client.py to start a websocket server.
    The obvious correct step is to run run_websocket_server.py instead.
        
## PySyft on Windows Pc
The Python, Pytorch, TorchVision and PySyft versions must match the ones that you installed on the Raspberry
 - ### Python
    - Just download Python 3.7.3 from the official page. This versions comes with pip.
 - ### Pytorch
    - Download the correspondent wheel from the official page and install it with pip:
      
      https://pytorch.org/get-started/previous-versions
      
      https://download.pytorch.org/whl/cpu/torch_stable.html
      
      For my machine I used torch-1.0.0-cp37-cp37m-win_amd64.whl
    - As for the Raspberry, install torchvision:
      pip3 install torchvision==0.2.2.post3
 - ### PySyft 0.1.13a1
    - Same as before:
      
      pip3 install syft==0.1.13a1 --no-dependencies
      
      pip3 install Flask flask-socketio lz4 websocket-client websockets zstd msgpack
    * The installation of zstd asked me to download Build Tools for Visual Studio from the official page:
      https://visualstudio.microsoft.com/downloads/
 - ### Central coordinator
     - Follow the guide, download the PySyft repo and open the Federated Recurrent Neural Network.ipynb notebook
     - In this GitHub folder I uploaded my notebook, which is almost a copy of the original one.

     * I had some problems connecting to the Raspberry websockets because of an error that said that TIMEOUT_INTERVAL was too large.
       
       So I modified C:/Python37/Lib/site-packages/syft/workers/websocket_client.py
       
       I set TIMEOUT_INTERVAL from 9_999_999 to 999_999 and added "import os"
     * While running the Notebook you may have to install some dependencies, but it is okay. If the notebook throws the same error after installing the dependency, try restarting the kernel.
  
  Connecting to the websockets took around 20 min and the trainning with 2 workers took 4hr 15 min.
      
    

    
 
   
