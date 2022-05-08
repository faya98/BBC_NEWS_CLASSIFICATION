# BBC_NEWS_CLASSIFICATION
## Dataset Description
Consists of 2225 documents from the BBC news website corresponding to stories in five topical areas from 2004-2005.
Natural Classes: 5 (business, entertainment, politics, sport, tech)

If you make use of the dataset, please consider citing the publication: 
- D. Greene and P. Cunningham. "Practical Solutions to the Problem of Diagonal Dominance in Kernel Document Clustering", Proc. ICML 2006.

All rights, including copyright, in the content of the original articles are owned by the BBC.

Contact Derek Greene <derek.greene@ucd.ie> for further information.
http://mlg.ucd.ie/datasets/bbc.html
## Functionalities of the code
1. Extracts the raw text from bbc_news_dataset.zip file and converts it into bbc.csv file
2. Pre-processes the data by lowercase conversion, removal of stopwords, removal of punctuations, and lemmatization
3. Split the data into train/development/test - 80%/10%/10%
4. Three feature entities are used - count, one-hot and tf-idf
5. For every feature entity number of features and feature selection methods are tuned using development set
6. For each feature entity a model is trained
7. Each model make predictions on test dataset
8. All 3 predictions are combined using majority voting
9. Accuracy, macro-averaged precision, macro-averaged recall, macro-averaged f1-score are calculated

# IoT Device

## Building the device
### Requirements
1. Raspberry Pi 4 Computer Model B 4GB RAM
2. GrovePi+
3. Pi Camera
4. Grove - Temperature and Humidity Sensor
5. Grove - Light Sensor
6. Grove - Sound Sensor

### Connections
1. Connect Pi camera to the camera module port in raspberry Pi (<i>refer</i> - https://projects.raspberrypi.org/en/projects/getting-started-with-picamera)
2. Connect GrovePi+ to the raspberry Pi (<i>refer</i> - https://www.dexterindustries.com/GrovePi/get-started-with-the-grovepi/#:~:text=(note%3A%20if%20you%20don',will%20turn%20on%20the%20GrovePi.)
3. Connect temperature and humidity sensor to port D7 in grovepi+.
4. Connect sound sensor to port A0 in grovepi+.
5. Connect light sensor to port A1 in grovepi+.

After making the connections, the device will look like
<img src="https://media4.giphy.com/media/8yFOREyjmKdGtMGzol/giphy.gif?cid=790b7611a1a38206cdcda4c0ed7a2d0e7f50346217965f11&rid=giphy.gif&ct=g" alt="People count" class="center">

## Installation
Onto the ceiling, close to the room door, with the camera facing the region where people have to cross through for entering and exiting a room

## Code Information
### light.py, sound.py, tempHum.py
These files contain the code to gather sensor readings(light, sound, temperature and humidity) from the environment.

### dataserver.py
This file is made as a local server to fetch the sensor values from camera and the rest of the sensors. The program then joins the data from both files and sends further to the server. This file ideally should be remote but for the demo purpose it is situated locally.

### combine.py
This file includes modules that read the values from temperature-humidity sensor, light sensor, and sound sensor. Combines all the values and sends to the dataserver.py.

### cameraCodeVideo.py
Reading the recorded video and processing the count of people inside the room (by calculating the number of people who have entered and exited) is done in this file. Further this count will be passed to the dataserver.py. 

### cameraCodeLiveStream.py
Reading the livestream video and processing the count of people inside the room (by calculating the number of people who have entered and exited) is done in this file. Further this count will be passed to the dataserver.py.

### Required packages
cv2, imutils, math, request, json, numpy, threading, picamera, statistics, grovepi, flask.

## Program execution
### Executing the code for recorded video input
1. Open the directory terminal.
2. Run command: <code><i>./StartProgrammeVideo.sh</i></code>

This will run three files 'dataserver.py', 'combine.py', and 'cameraCodeVideo.py'. 

### Executing the code for livestream video input
1. Open the directory terminal.
2. Run command: <code><i>./StartProgrammeLiveStream.sh</i></code>

This will run three files 'dataserver.py', 'combine.py', and 'cameraCodeLiveStream.py'.

## Sample Output for capturing live occupancy in a room
<img src="https://media.giphy.com/media/nhZtxM3vwuRgpcAQAI/giphy.gif" alt="People count" class="center">


