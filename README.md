# Drowsiness Detection Based on Pupil Movement/Behavior

**ABSTRACT**

Drivers often feel very drowsy while continuously driving for long distances without taking breaks. Drowsiness is a major factor in increasing the chances for a vehicle to meet accidents . According to various studies, Number of accidents caused by drowsiness is much higher than the number of accidents caused by drunk driving. The number of accidents caused by drowsiness can be reduced by having a proper system that can detect drowsiness, alert the driver and prevent major injuries. It needs a proper system that will alert drivers to prevent major injuries. The project starts an alarm when it detects the driver is drowsy and notify drivers to take a rest along with a nearby rest services area. It detects the driver’s last sleeping time and suggests to take a rest.

**Introduction**

Drowsiness detection is a critical task in various domains such as transportation, industrial operations and healthcare to ensure safety and prevent some serious accidents which may even cost a life. One of the effective approaches is through convolution neural network (CNNs). And there are different ways to approach to solve this kind of problem like Viola–Jones method, Electrooculography (EOG), Infrared camera-based techniques and Facial landmark points etc. in this above project we are using CNN (convolution neural networking) technique to solve the problem. Below point justify the extent of effect drowsiness have
•	According to a study by the AAA Foundation for Traffic Safety, it is estimated that 328,000 drowsy driving crashes occur annually, with about 109,000 resulting in an injury and approximately 6,400. These numbers are more than three times the police-reported number, indicating that driver fatigue is a significant issue on the roads.
•	In healthcare, fatigued staff may make errors in medication or treatment.

•	These detections help in identifying the drowsiness of an employ and can help in assisting him/her with some psychologist increasing the overall performance of an individual.
So, one of the major solutions to detect and retain the driver in case of transportation and other fields is Cascade classifier(cv2.CasCadeClassifier).
Cascade Classifier:
Used for face detection (cv2.CascadeClassifier).
This is a pre-trained classifier based on Haar-like features. It is fast compared to modern learning models.

**About use-case**
 
•	Drowsiness Detection based on pupils movement/behaviour

This system is designed to monitor a driver's alertness level in real-time using computer vision and machine learning techniques. Here's a breakdown of the use case:
1.	Driver Monitoring: The system uses a camera (likely facing the driver) to continuously capture video of the driver's face.
2.	Drowsiness detection: It employs a cv2 model, which has been trained to detect signs of drowsiness in driver’s face.
3.	State Classification: The system classifies the driver’s facial state into two categories based on EAR(eye aspect Ratio)
•	Drowsy
•	Yawn
•	Fairly Alert
4.	Real-time Feedback: The current state is displayed on the video feed, providing immediate visual feedback.
5.	Escalating Alerts:
•	For "Drowsy" or "Yawn" states, an audible alarm is triggered.
•	For "Yawn/Sleepy" state, an SMS alert is sent to a predefined number.
6.	Continuous Monitoring: The system runs in a loop, constantly updating the driver's state based on recent observations.
This use case is particularly relevant for:

•	Long-haul truck drivers
•	Night shift workers operating vehicles or machinery
•	Any profession where maintaining alertness is critical for safety

**Working Principle**
1.	Video Capture:
•	A webcam video feed is accessed using VideoStream from imutils.
•	The frames are resized for efficiency and converted to grayscale.
2.	Face Detection:
Uses OpenCV's Haar cascades (haarcascade_frontalface_default.xml) for detecting faces in each frame.
3.	Facial Landmark Detection:
Extracts 68 facial landmarks using dlib.shape_predictor.
4.	Eye and Lip Analysis:
•	EAR is computed to detect drowsiness.
•	Lip distance is measured to detect yawning.
•	Points and EAR Calculation
Points (P1 to P6): These are the six key facial landmarks around the eye, which are detected using the shape_predictor_68_face_landmarks.dat model from Dlib. These points help define the shape and opening of the eye.
P1 to P4: Horizontal boundary of the eye.
P2, P3, P5, P6: Vertical boundaries of the eye.
•	Formula for EAR:
The EAR is calculated as the ratio of vertical eye distances to the horizontal eye distance.
•	EAR = 𝑫𝒊𝒔𝒕𝒂𝒏𝒄𝒆(𝒑𝟐,𝒑𝟔)+𝑫𝒊𝒔𝒕𝒂𝒏𝒄𝒆(𝒑𝟑,𝒑𝟓)
𝟐𝑿𝑫𝒊𝒔𝒕𝒂𝒏𝒄𝒆(𝒑𝟏,𝒑𝟒)
5.	Alarms: When thresholds are exceeded, the respective alarms are triggered using Thread.
6.	Overlay Information: Displays EAR, yawning distance, and alert messages on the video frames.

**Libraries used**
1.	OpenCV (cv2):Used for real-time video capture and frame processing. Haar cascades for face detection.
Functions like cv2.cvtColor, cv2.resize, and cv2.drawContours for image manipulation.
2.	dlib: Shape predictor (shape_predictor_68_face_landmarks.dat) for facial landmark detection. Used to extract specific regions of interest (eyes, lips).
3.	Scipy: Module spatial.distance provides the euclidean function to calculate distances between points (essential for EAR and lip distance calculation).
4.	Imutils: Simplifies image resizing and other common image-processing tasks.
5.	Threading: Enables running the alarm system concurrently without blocking the main video processing loop.
6.	OS: Executes external commands for text-to-speech functionality using espeak.
7.	NumPy (np): Handles numerical operations, especially for calculating mean distances of lips and manipulating arrays.
   
**About Flowchat**

The flowchart represents the working principle of a drowsiness detection system based on eye closure monitoring, which aligns closely with the code provided. Here's an explanation of each step:
1.	Video Stream or Input Image
The system starts by acquiring live video input from a webcam or a pre-recorded video. This serves as the source for detecting the subject's face and monitoring their drowsiness.
2.	Human Face Tracking
Pre-Processing: The input video frames are pre-processed, including resizing and converting to grayscale for faster and more efficient processing.
Algorithm: A face detection algorithm, such as Haar Cascade Classifier or Dlib's facial landmarks, is applied to locate the face in the frame.
3.	Feature Extraction
Facial Key Region: Once the face is detected, the system extracts specific facial landmarks like the eyes and mouth using a 68-point facial landmark detector.
Eyes: The eyes are segmented from the landmarks, and their geometry is analyzed to calculate the Eye Aspect Ratio (EAR).
4.	Evaluation
The extracted features, especially the EAR, are evaluated to determine if both eyes are closed. If the EAR falls below a defined threshold for a consecutive number of frames, it indicates drowsiness.
5.	Alert Alarm
If drowsiness is detected (e.g., prolonged eye closure), an alert is triggered in the form of an audible alarm to wake the person or warn them to take a break.
This process ensures real-time monitoring of drowsiness and prevents potential accidents, especially in applications like driver fatigue detection.




