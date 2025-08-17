#python drowniness_yawn.py --webcam webcam_index from scipy.spatial import distance as dist
from imutils.video import VideoStream from imutils import face_utils
from threading import Thread import numpy as np
import argparse import imutils import time import dlib import cv2 import os

def alarm(msg): global alarm_status
global alarm_status2 global saying

while alarm_status: print('call')
s = 'espeak "'+msg+'"' os.system(s)

if alarm_status2: print('call') saying = True
s = 'espeak "' + msg + '"' os.system(s)
saying = False
