# Object Detection-Human Detection-Social Distancing using Tensorflow Object Detection
# Specific Object Detection using Tensorflow Object Detection API

STEPS : 
1. Object Detection using TensorFlow Object Detection API
2. Convert Video To Images
3. Visualize Objects in Image
4. Delete Boxes of other Objects except for Human
5. Visualize Humans
6. Calculate distance between Human Objects using Euler's distance formula between center points of both objects
7. Change color of human objects which are breaking rules of social distancing.
8. Visualize The Output Image
9. Convert Images to Video

*To Detect Specific Object You Required print category-index and get the key of your object*<br>
*Replace 1 which represent Person with the key of your object in VisualizeHumansImage*<br>
*if(output_dict['detection_classes'][index] != 1):*<br>
        *indexes_not_human.append(index)*<br>
*Change this 1*<br>
*PATH_TO_LABELS = 'models/research/object_detection/data/mscoco_label_map.pbtxt'*<br>
*category_index = label_map_util.create_category_index_from_labelmap(PATH_TO_LABELS, use_display_name=True)*<br>
*print this category index to get the key of objects you can detect*<br>

Input Dataset : https://www.robots.ox.ac.uk/ActiveVision/Research/Projects/2009bbenfold_headpose/Datasets/TownCentreXVID.avi

Outputs :

<h3>Object Detection</h3>

<img src="objectDetection.png" alt="Object Detection Image">

<h3>Social Distancing</h3>

<img src="SocialDistancing.png" alt="Social Distancing Image">

Functions

1. load_model
2. run_inference_for_single_image
3. VideoToFrames
4. VisualizeImage
5. DisplayImage
6. FramesToVideo
7. getSingleHumanCoordinates
8. getDistance
9. VisualizeSocialDistancing
10. VisualizeHumanImage
11. FramesToStore
12. SocialDistanceToVideo

**Functions Explaination**:

1. **load_model** <br> 

    *Args*  :<br>
    &nbsp;&nbsp;&nbsp;model_name : Passing Tensorflow model Name<br>
    *Returns* : <br>
            &nbsp;&nbsp;&nbsp;Trained model<br>

2. **run_inference_for_single_image** <br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;model : Passing loaded Model<br>
          &nbsp;&nbsp;&nbsp;image : Image to be processed<br>
    
    *Returns* : <br>
              &nbsp;&nbsp;&nbsp;Output Dictionary which contains<br>
              &nbsp;&nbsp;&nbsp;1. Detected Boxes Dimensions<br>
              &nbsp;&nbsp;&nbsp;2. Detected Classes index <br>
                 &nbsp;&nbsp;&nbsp;eg [1,2,3] 1 is for Person<br>
              &nbsp;&nbsp;&nbsp;3. Detected Scores which is <br>
                 &nbsp;&nbsp;&nbsp;list of scores for each detection<br>
              &nbsp;&nbsp;&nbsp;4. Number of Detected Objects<br>

3.  **VideoToFrames** <br>

    *Args* : <br>
          &nbsp;&nbsp;&nbsp;VideoFileName : Pass name of video file with ext <br>
          &nbsp;&nbsp;&nbsp;Path : Pass Path where to store Frames<br>
    
    *Returns* :<br>
            &nbsp;&nbsp;&nbsp;Creates Frames From video and store it in path<br>

4.  **VisualizeImage**<br>
    
    *Args* : <br>
          &nbsp;&nbsp;&nbsp;ImageName : Pass name of Image to be Visualized<br>
          &nbsp;&nbsp;&nbsp;Path : path to the image<br>
          
    *Returns* :<br>
            &nbsp;&nbsp;&nbsp;Image with object detected boxes drawn on it<br>

5. **DisplayImage**<br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;Image : numpy array Image<br>
          
    *Outputs* :<br>
            &nbsp;&nbsp;&nbsp;Prints image to output<br>

6. **FramesToVideo**<br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;no_of_frames : Number of frames to be converted to<br>
                &nbsp;&nbsp;&nbsp;Video<br>
                         
    *Outputs* :<br>
            &nbsp;&nbsp;&nbsp;The Video with 15 fps created using 0-n frames<br>

7. **getSingleHumanCoordinates**<br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;Boxes : List of Detected boxes coordinates<br>
          &nbsp;&nbsp;&nbsp;Image : Image <br>
          &nbsp;&nbsp;&nbsp;position: position of object from list of <br>
                    coordinates<br>
                    
    *Returns* : <br>
            &nbsp;&nbsp;&nbsp;Left right bottom top coordinates of object<br>

8. **getDistance**<br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;x1,x2,y1,y2 : Coordinates to find Distance<br>
          
    *Returns* :<br>
          &nbsp;&nbsp;&nbsp;Distance between (x1,y1) and (x2,y2)<br>

9. **VisualizeSocialDistancing**<br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;Boxes : List of Coordinates of all objects<br>
          &nbsp;&nbsp;&nbsp;Image : Image To Visualize<br>
          
    *Outputs* :<br>
          &nbsp;&nbsp;&nbsp;Draws red color on boxes near to each other<br>

10. **VisualizeHumanImage**<br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;ImageName : Name of Image File to Visualize<br>
          &nbsp;&nbsp;&nbsp;Path : path to Image<br>
          
    *Returns* :<br>
          &nbsp;&nbsp;&nbsp;Image with Boxes drawen<br>

11. **FramesToStore**<br>

    *Args* : <br>
          &nbsp;&nbsp;&nbsp;tillFrame : Pass number of Frames to Visualize<br>
          
    *Outputs* :<br>
            &nbsp;&nbsp;&nbsp;Stores Visualized Image To SocialDistancingFrames<br>
            &nbsp;&nbsp;&nbsp;Folder<br>

12. **SocialDistanceToVideo**<br>

    *Args* :<br>
          &nbsp;&nbsp;&nbsp;no_of_frames : Pass number of Frames<br>
          
    *Outputs* :<br>
            &nbsp;&nbsp;&nbsp;Video till no_of_frames of 15fps<br>
