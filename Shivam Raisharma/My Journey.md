# My journey
This project is based on the blog https://blog.openmined.org/federated-learning-of-a-rnn-on-raspberry-pis/

  It had been few days since the study groups were first announced in the SPAIC slack group. I was yet to finish my morning coffee when I came across this very interesting study group #sg_pytorch-robotics created by @Helena Barmer.
The primary project of the group involved training RNNs on raspberry pis by federated learning. And boy did it peak my interest!
  
  The major motive behind me choosing this was to learn. The whole scholarship journey to me has been about learning and this project offered to get me started afresh in a lot of fields simultaneously!

1. Hardware - I had never used any hardware device before. This looked like a great opportunity to get my hands dirty finally! Moreover having a huge array of experts in the study group would definitely make my start smoother!
2. Deep Learning on peripherals - I had read a lot of articles (especially by pyimagesearch) on performing deep learning on raspberry pi and other devices but had never tried it before!
3. Federated Learning - While the course by udacity has offered me a great exposure to Federated Learning techniques, I would never be able to see the magic in action unless I actually deploy it on multiple peripheral devices (like raspberry pis or PC).


So I buckled my seat belts, changed the gears and accelerated towards the RnD cell of my institute! 
After a few applications I was able to procure 3 Raspberry pi 3Bs (they did not have 3B+) and the ethernet switch mentioned in the blog.

Installing OS on the pis took a lot of time and I was able to get 1 of them started with Raspbian Buster OS while the other 2 had some problem with reading the memory card.
It took me another day to figure out why I can't connect my lone working raspberry pi to the wifi when I found that I needed to download wifi drivers. 
However the wifi driver couldn't detect anything! Great. So I have spent two days working on 3 Raspberry Pis and none of them work. 
I wished to replace those pis or buy new ones but due to flood-like situation in Mumbai, couldn't do the same for a couple of days.

## New Start
I was finally able to collect 3 new Raspberry Pis from the college R&D cell ( but not before making my R&D co-ordinators promise that they're not faulty :P)
I decided to first test my first Raspberry pi and if it works reproduce the steps on the other 2 peripherals! 

  I had my first Rpi up and running with Raspbian Stretch OS. So far so good :D. 
  I installed python and dependencies of pytorch. It's going great!
  Wait.. perhaps I spoke a tad bit quickly! I can't ping github.com :( It works fine with other websites though. Strange.
  I was able to work my way around it by calling help from a cloud enthusiast friend Kaustubh (THANKS A LOT FRIEND), he somehow managed to host the repo on an instance on AWS and I cloned the pytorch repo from there!
  
Next step : Building and installing pytorch

Someone has rightly said " Building libraries give you a lot of time to think about life ".
Building pytorch takes a lot of time and requires loads of patience. But the progress in % sure keeps you satisfied but on toes.
It gave me some errors for half a hour which I later figured out to be a result of my own negligence

20%
20%
20%
24%
Oh it's increasing!
26%
Don't do that, don't give me hope :P
28%
71%
YES A BIG JUMP THANK GOD IT'S SPEEDING UP
71%
71%
And it stayed 71% for an hour before giving me an error with caffe2.

I copied the error and pasted in the slack study group and voila! 5 responses in 15 minutes :D I am telling you my fellow scholarship participants here are beyond awesome!

  On their advice i changed some flag statuses and upgraded my numpy and increased the size of my swaps. 
  And it worked :)  (Although after almost 2 days of follow up doubts and error solvings on threads and DMs)
  Thank you good helpful people of slack!
  
Next milestone : Installing pysyft

So I started installing pysyft and it gave some very odd errors at various points of time.
There are some errors that I dont encounter sometimes but I encounter them occassionally which had me puzzled.
On times I didnt encounter them I proceeded forward and found that the setup.py was unable to detect that I had pytorch, so I edited it out of the requirements.:P
I hadn't installed torchvision which was one of the requirements but it wasn't able to install the same because it couldn't find a suitable version of it.

I realised that the python version my Rpi was installed with was python 3.5 which was apparently the official version. And pysyft requires python 3.6.7 (which maybe why I cant find the suitable versions of torchvision through pip install)but I can't find any official way to do that without overturning my whole progress.
I have found some tutorial to install python 3.6.7 and I am following them.
Last I checked my progress bar was at 89% for 8 hours while I was installing pysyft.


## Future scope
Finish the installations and code an RNN and train federately


I learnt a lot about Raspberry pis from this project. The webinars hosted in the #sg_pytorch-robotics study group helped me out for getting familiar with other IOT devices.
All in all my journey yet with this project and study group has made me learn a lot about Deep learning on IoT devices. I wish to continue this and aim to see it to the end of this project.
And I want to wholeheartedly thank the entire group and community for empowering me with this opportunity that made me learn more and exposed me to a whole new lot of domains.
It got me out of my comfort zone (ie into hardware), and patiently challenged me to explore a whole new field!

Thank you for reading. Have a great day!

