# Robot-Class-Final

## Problem Statement
We've learned many cool models in class that allows robots to perform tasks at a given location. However, most of these robots are doing predefined tasks at close proximity to the objects of interest. This is different from the ideal state of intelligent robots where the robot need to take instructions from human, and move toward the objective where the object of interest is located. For example, if we want our home robot to do laundry, it has to move toward the washing machine from wherever it was beforehand. 

Our project presents a proof of concept method for integrating a language-vision model into the control loop of a robot. Utlizing the open-set object detection ability of the recent vision model, we have empowered our robot not only to perform simple object-following tasks but also to follow any unseen object based on textual descriptions.

## Method

We used the [language segment anything](https://github.com/luca-medeiros/lang-segment-anything), a project based on [Grounding DINO](https://arxiv.org/abs/2303.05499) and [Segment Anything Model](https://arxiv.org/abs/2304.02643), to generate mask for frame captured by rover camera conditioned on text prompt. 

As shown in the following example, when we entered the prompt: "the left rubbish bin", the mask is generated, and we use the postition of the centroid of the mask as the target direction.
<img width="502" alt="071f0749858b89d1f0f21f24d9b90c2" src="https://github.com/Hyteve/Robot-Class-Final/assets/33574420/9b6ae976-a3f7-475b-9257-adbae36ae74a">

As implemented in [language segment anything](https://github.com/luca-medeiros/lang-segment-anything). After we specify the prompt and the rover's camera returns an image, the Grounding DINO model will generate a bounding box of the object described in the prompt. Then, the bounding box is processed by the Segment Anything model to create a mask of the prompted object, along with its location in the image. Finally, based on the location of the object in the image, the rover would be instructed to turn left/right, or to go straight. 

## Notes

We used Google Collab to run our code, since the vision models require GPU to run. The code are located in the file [robot_final.ipynb](robot_final.ipynb)
