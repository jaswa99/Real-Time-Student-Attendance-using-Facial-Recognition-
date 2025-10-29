Real-Time Student Attendance using Facial Recognition
This project is a real-time attendance system that uses facial recognition to identify students from a webcam feed and automatically log their attendance in a CSV file.

📋 Overview
The system captures video from a webcam, detects faces in each frame, and compares them against a "database" of known student images. When a known student is identified, their name, the current date, and the time are recorded in an Attendance.csv file.

✨ Features
Real-time Recognition: Detects and identifies faces from a live webcam feed.

Automatic Logging: Automatically records attendance in an Attendance.csv file.

Timestamping: Logs both the date and the time of the first sighting.

Duplicate Prevention: The system is built to only mark a student present once per day, ignoring subsequent recognitions on the same day.

⚙️ How It Works
Load Known Faces:

On startup, the script reads all images from the ImagesAttendance directory.

It extracts the student's name from the image filename (e.g., Elon Musk.jpg becomes the class name Elon Musk).

Generate Encodings:

It uses the face_recognition library to find the facial features (encodings) for each student image in the database. These known encodings are stored in a list.

Capture & Recognize:

The script activates the webcam (cv2.VideoCapture).

In a continuous loop, it captures a frame from the video feed.

It resizes the frame for faster processing.

It finds all faces in the current frame and generates their encodings.

Compare & Identify:

For each face found in the frame, it compares its encoding to the list of all known encodings.

It calculates the "face distance" to find the best match. The student with the smallest distance is identified as the match.

Log Attendance:

When a student is identified (e.g., Elon Musk), the markAttendance(name) function is called.

This function opens Attendance.csv and checks if the student's name has already been logged for the current date.

If the student is not yet in the log for today, their name, the current date, and the current time are appended to the file.

Display:

An OpenCV window (cv2.imshow) displays the live webcam feed.

A green rectangle and the student's name are drawn around each recognized face.

🚀 How to Run
Clone the Repository:

Bash

git clone <your-repo-url>
Install Dependencies: You must have Python and the following libraries installed. You can install them using pip:

Bash

pip install opencv-python numpy face-recognition
Create the Image Database:

Create a folder named ImagesAttendance in the same directory as your script.

Add images of the students you want to recognize into this folder.

IMPORTANT: The filename of each image must be the student's name (e.g., John Doe.png, Jane Smith.jpg).

Run the Script:

Run the Python script or execute all cells in the STUDENT ATTENDANCE DETECTION(1).ipynb notebook.

The webcam will activate, and the "Webcam" window will appear.

As students are recognized, the Attendance.csv file will be created/updated in the same directory.

🛠️ Libraries Used
OpenCV (cv2): For capturing video from the webcam, processing frames (resizing, color conversion), and drawing rectangles/text on the screen.

face_recognition: A high-level library for finding face locations, computing facial encodings, and comparing faces.

NumPy: Used for high-performance array operations.

OS: Used to read the filenames from the ImagesAttendance directory.

datetime: Used to get the current date and time for logging attendance.
