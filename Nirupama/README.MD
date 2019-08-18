
CLASSIFYING NAMES WITH A CHARACTER-LEVEL RNN :: We will be building and training a basic character-level RNN to classify words. A character-level RNN reads words as a series of characters - outputting a prediction and “hidden state” at each step, feeding its previous hidden state into each next step. We take the final prediction to be the output, i.e. which class the word belongs to.

Recommended resources::

https://pytorch.org/ For installation instructions
Deep Learning with PyTorch: A 60 Minute Blitz to get started with PyTorch in general
Learning PyTorch with Examples for a wide and deep overview
PyTorch for Former Torch Users if you are former Lua Torch user
The Unreasonable Effectiveness of Recurrent Neural Networks shows a bunch of real life examples
Understanding LSTM Networks is about LSTMs specifically but also informative about RNNs in general

Dataset:: We can download Dataset from here "https://download.pytorch.org/tutorial/data.zip"
