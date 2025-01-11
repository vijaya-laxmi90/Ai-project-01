This is an overview of this project.

1.Overview 

This system utilizes YOLOv5 for real-time object detection in videos and associates detected objects with their sub-objects based on proximity. 
The system processes a video, extracts frames, detects objects in each frame, associates sub-objects with parent objects, saves cropped sub-object
images, and outputs a processed video with visualized detections. The results are stored in JSON format and can be downloaded as zip files.

2.Prerequisites

Before running the system, ensure that you have the following:

Python 3.x installed on your system pip (Python package manager) for installing dependencies A Google Colab account or a local environment
set up for video processing Required Libraries To run the system, install the necessary Python libraries:

"pip install opencv-python-headless torch google-colab numpy pathlib shutil"

Alternatively, if running on Google Colab, these libraries are available by default, and you do not need to install them manually.

3.System Requirements

A video file for object detection A working internet connection to download the YOLOv5 model for object detection Google Colab for running the code or a
local setup for video processing Sufficient disk space to store processed video, frames, and cropped images

4.How to Use the System 

Step 1: Upload Your Video a.In Google Colab, upload a video file that you want to process using the system. b.You can upload the video file using the code block provided below:

"uploaded = files.upload() # Upload your video file here video_path = next(iter(uploaded)) # Get the path of the uploaded video file"

Step 2: Process the Video The system will automatically process the video. During processing, the following steps occur:

.Frame Extraction: The video is processed frame by frame. .Object Detection: YOLOv5 is used to detect objects in each frame.
.Object-Subobject Association: Detected sub-objects (e.g., tires, helmets) are associated with their parent objects (e.g., cars, people) based on proximity.

.Detection Visualization: The detected objects and sub-objects are visualized on the frames and saved in an output video. 
.Results Storage: The results are stored in a detection_results.json file, and cropped images of sub-objects are stored in the cropped_data folder

Step 3: Save and Download Results 
a.Processed Video: The processed video with object detections is saved as processed_video.mp4 and can be downloaded by running:

"files.download(output_video_path)"

b.Detection Results: The results in JSON format are saved as detection_results.json. This file contains the object detection information (including object class, ID, bounding box, and sub-object details).

c.Cropped Sub-Objects: Cropped images of detected sub-objects are saved in the cropped_data folder.
You can download them as a zip file by running: "create_and_download_zip_file(cropped_dir, "cropped_data")"

d.Frames: You can also download the extracted frames as a zip file by running: "create_and_download_zip_file(output_dir, "frames")"

Code Workflow Video Processing: The cv2.VideoCapture method reads each frame from the uploaded video. The YOLOv5 model is applied to each frame to detect objects,
which are then processed by the detect_and_associate_objects() function.

Object Detection: The YOLOv5 model is loaded using torch.hub.load('ultralytics/yolov5', 'yolov5s'), which automatically downloads the model and loads it for inference.

Object and Sub-Object Association: Objects (such as cars, people) are detected along with their bounding boxes. Sub-objects (such as tires or helmets) 
are associated with parent objects based on proximity using the bounding box positions.

Result Storage: Detected objects and their sub-objects, along with the associated information, are saved in a JSON format for easy retrieval.
Cropped images of sub-objects are stored as individual image files.

Video Output: The processed video is generated using cv2.VideoWriter to output a video file with bounding boxes drawn around detected objects and sub-objects.

5.Reproduce the Results To reproduce the results, follow these steps:

Clone or download the project directory to your local machine or Google Colab environment. Upload a video file to process.
Run the provided code. It will process the video, detect objects, associate sub-objects, and generate a processed video. 
Download the processed video, detection results, and cropped images. License This project is licensed under the MIT License. 
You are free to use and modify the code as needed, but please attribute the original authors.

6.Acknowledgements 

YOLOv5: Used for real-time object detection. See the official YOLOv5 repository. OpenCV: Used for video processing and frame extraction. See the OpenCV documentation.
