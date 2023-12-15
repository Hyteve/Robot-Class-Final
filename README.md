# Robot-Class-Final

## Problem Statement
We've learned many cool models in class that allows robots to perform tasks at a given location. However, most of these robots are doing predefined/pre-trained tasks at close proximity to the objects of interest. This is different from the ideal state of intelligent robots where the robot need to take instructions from human, and move toward the objective where the object of interest is located. For example, if we want our home robot to do laundry, it has to move toward the washing machine from wherever it was beforehand. 

Therefore, for our final project, we developed a rover that would take any instruction from human users, then search and move toward the object specified in the prompt. With our model's help, combining with the amazing robotic models introduced in class, we are one step closer to creating a smart home robot that could help us do all the houseworks! 

## Method and Solution

As shown in the demo, when we entered the prompt: "the rubbish bin", the rover looked for and identified the rubbish bin, and then successfully moved toward it from a distance. 

We used Language Segment-Anything as our core model to achieve the desired functionalities. After we specify the prompt and the rover's camera returns an image, they are processed by the Grounding DINO model to generate a bounding box of the object described in the prompt. Then, the bounding box is processed by the Segment Anything model to create a mask of the prompted object, along with its precise location in the image. Finally, based on the location of the object in the image, the rover would be instructed to turn left/right, or to go straight. 

The process described above is repeated in a loop until the rover reaches the prompted object. 


## Notes

We used Google Collab to run our code, since the vision models require GPU to run. The code are located in the file [robot_final.ipynb] (robot_final.ipynb)
