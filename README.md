# Ground Truth Data Session for Vehicle Detection
<p align=center>
  <img src="https://github.com/hsidd1/nl-gTruthData/assets/120290526/2e6e5211-ba2e-4025-a855-e3ebcdbbb007">
</p>

This project uses the `VideoLabeler` App from MATLAB's CV toolbox (Under Image Processing and Computer Vision) for analyses used for research papers and company R&D. It is used to determine the vehicle edge detection performance of our CV models running on different devices under the NVIDIA Jetson series. 
It serves as a `Ground Truth` for these various tests, to see just how much a model's accuracy changes based on specs. 

> In machine learning, the term ground truth refers to the reality you want to model with your supervised machine learning algorithm. Ground truth is also known as the target for training or validating the model with a labeled dataset. During inference, a classification model predicts a label, which can be compared with the ground truth label, if it is available. [Source](https://domino.ai/data-science-dictionary/ground-truth)
> 
I am providing this repository for anyone else who is interested in making use of it. The session places bounding boxes on Regions of Interest (ROIs) of different vehicle types in an intersection. It was automated via the Point Tracking Algorithm and fine-tuned manually (very tedious..). It tracks these labels with corresponding position, timestamps, etc. and saves it as LabelDefinitions in a `gTruth` variable. 
The labelling session is for 1/4th of the 1 minute video. You can open the session in MATLAB's [Video Labeler App](https://www.mathworks.com/help/vision/ug/get-started-with-the-video-labeler.html). 

### How You Can Use This Session
First, clone the repository
```sh
git clone https://github.com/hsidd1/nl-gTruthData.git
```
Then open the labelling session in MATLAB's Video Labeler App:
- Open MATLAB
- Execute command `videoLabeler` in the MATLAB shell.
- Go to `Open Session`, then select the [session file](https://github.com/hsidd1/nl-gTruthData/blob/main/labelling-session/videoLabelingSession.mat)

From there, you can add more labels past 15 seconds (where it is currently labelled up to), automate the labelling (The Point Tracking Algorithm has worked best for me), and then EXPORT the data as `gTruth` to MATLAB, and analyze the outputs in the shell. The LabelDefinitions are currently provided here, but can also be viewed from the properties from the `gTruth` variable exported (`gTruth.LabelDefinitions`). I highly suggest reading the Video Labeler documentation to get a better understanding of using this app and exploring all of its capabilities. Using timestamps and bounding box position per time stamp of each label, those positions can be compared to your model to determine accuracy against the ground truth (You may want a parser script for this). This has been abandoned as we moved to a different platform, but I still wanted to document this version somewhere. I hope it can be of use to someone out there!
