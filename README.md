# goproUSB

A simple Python package for controlling, recording images and videos, and downloading media from GoPro cameras connected via USB.

It allows to connect to a single or multiple cameras and perform simultaneous recordings of images or videos.

The only thing required to connect to a camera is its serial number. The serial number is a 14. character string, beginning with "C3". It can be obtained either directly from the camera's menu ( [Preferences] > [About] > [Camera Info]), or by right-clicking camera connected via USB in file explorer (Windows) and selecting "Properties". 

I have only tested it with HERO 10 cameras. Not sure how will it work with other GoPro cameras.

Example usage - take picture and download it to a current working directory:

serial_number = 'C3xxxxxxxxxxxx'
output_file_name = 'image'
from goproUSB import GPcam
cam1 = GPcam(serial_number)
cam1.USBenable()
cam1.modePhoto()
cam1.shutterStart()
#wait for the camera to finish processing:
while cam1.camBusy():
    continue
while cam1.encodingActive():
    continue
cam1.mediaDownloadLastJpg(output_file_name)

For examples of other operating options - recording videos, using webcam mode, and acquiring data from multiple cameras simultaneously - please refer to the "examples" folder.
