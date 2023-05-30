# face_recognition
## v_0.0 
The code of v_0.0 only allows you to recognize faces from a webcam

## v_1.0
The code of v_1.0 allows you to find and recognize faces in a video conference, as well as count the time of presence on the video using facenet_pytorch (MTCNN, InceptionResnetV1) and OpenCV.

## v_2.0
+ Added YoloV5_face for face recognition

# Start

1. Cloning a repository:
    
    ```bash
    git clone https://github.com/mkgs210/face_recognition
 
1. Installing the required libraries:

    ```bash
    #facenet-pytorch==2.5.2
    #opencv-python==4.6.0.66
    #pandas==1.5.1
    #matplotlib==3.6.2
    pip install -r requirements.txt

1. Running the program with default options:

    ```bash
    python main.py

Passed parameters:

  * `-h` or `--help` Displays description of all passed parameters
  * `-pcp` or `--photo_catalog_path` The path to the photo folder. Inside this directory there should be signed folders with photos of people who will be present in the video (default=`photos`)
  * `-ud` or `--update_data` Updates/Creates a file data.pt (call when updating photos). This file contains encoded faces of people (embeddings)(default=`True`)
  * `-dp` or `--data_path` Path to the directory where the data.pt file is located (default=` ` - the folder where the program is located)
  * `-wc` or `--web_cam` Reading video from a webcam. Time log files will not be created (default=`False`)
  * `-ivp` or `--input_video_path` Full path to input video (default=`video.mp4`)
  * `-dv` or `--do_video` True - create a video in which all found and recognized faces will be marked. False - do not create (default=`False`)
  * `-ovp` or `--output_video_path` Full path of output video with tagged faces (default=`new_video.mp4`)

An example of calling a program with parameters: `python main.py -pcp photos -ud True -ivp video.mp4 -dv True -ovp new_video.mp4`


# Output data

### *At the first start, the `InceptionResnetV1_VGGFace2` folder will be created and the `InceptionResnetV1-vggface2` model will be loaded into it*

At the end of the program, 4 files will be created:
  * Time_{`--input_video_path`}.csv - file with calculated presence time on video
  <img width="250" alt="image" src="https://user-images.githubusercontent.com/78417431/219395573-36cabff4-cf1d-4e60-a235-b93d366f95ee.png">

  * Time_drop0_{`--input_video_path`}.csv - file with calculated time of presence on the video (values with zero time are discarded)
  <img width="250" alt="image" src="https://user-images.githubusercontent.com/78417431/219395965-8048e19a-c169-43d3-8bac-61687b8d2950.png">

  * barh_{`--input_video_path`}.jpg - a bar graph showing the percentage of time each person is present
  <img width="1031" alt="image" src="https://user-images.githubusercontent.com/78417431/219396714-46e727a8-73d3-4308-b7ec-938b31cf7379.png">

  * pie_{`--input_video_path`}.jpg - a pie chart showing the presence time of video participants relative to each other
  <img width="616" alt="image" src="https://user-images.githubusercontent.com/78417431/219397109-4f44d869-6e2c-40a0-86c6-8d57a02248f3.png">

Also, `--do_video True` will create a video called `--output_video_path` (default=`new_video.mp4`)
