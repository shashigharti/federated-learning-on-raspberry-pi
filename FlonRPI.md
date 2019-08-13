Title: Federated Learning on Raspberry Pi

Author: Jess

**Overview**

The purpose of using federated learning on a Raspberry Pi (RPI) is to build the model on the device so that data does not have to be moved to a centralized server.  In addition to increased privacy, FL works well for Internet-of-Things applications because training can be done on the device instead of having to pass data between devices and a centralized server.  

This project, which implements the OpenMined tutorial (linked below) simulates the process using 2 RPIs to classify a person's surname with its most likely language of origin.

**Federated Learning**

Using federated learning, it's possible to train multiple RPIs without passing any data between them or a centralized server.  For example, this could be used to develop a secure, RPi-based "smart home" system.  The model is trained on the RPIs and the data is encrypted using secure aggregation, which adds zero-sum masks to obscure the training results.  Then, the encrypted training results (not the actual data) are sent to the server.  The encrypted results from the RPIs are combined and the server can only decrypt the aggregated result.  

Testing is also done on the RPIs.  The server uses the aggregated result to build a better model, then sends that improved model back.  Each RPI tests the updated model on its own data (without it ever leaving the device).  Once the test results are deemed good enough, the new model can be pushed out from the server to all RPIs.  

The main advantage of federated learning is that data never leaves each RPI while they each receive an improved model based on their aggregated data.  One thing to remember is that the improved model sent back to the devices is static- it won't be updated until the entire process occurs again to build a sufficiently accurate, updated model. 

**Resources**

* [Federated Learning of a RNN on Raspberry Pi](https://blog.openmined.org/federated-learning-of-a-rnn-on-raspberry-pis/)


Link to article in Wiki: https://github.com/shashigharti/federated-learning-on-raspberry-pi/wiki/Article:-Federated-Learning-on-Raspberry-Pi,-written-by-Jess
