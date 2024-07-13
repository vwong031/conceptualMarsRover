For my senior design project in embedded systems and computer architecture, my team and I decided to create a conceptual version of the Mars Rover using an FPGA. 

## Our goal for this project was:
1. Education of the FPGA field and hardware description languages (HDL)
2. Learn to use basic peripherals and screen display on the FPGA.

## Our objective for the project was to:
1. Create a conceptual version of the Mars Rover
2. Use LEDs and buttons to represent movement of the rover
3. Display the rover's movements using HDMI

## Inspiration for the Project:
Conceptually, we would want to explore Mars without actually being on Mars, however, many issues can happen with technology. With FPGAs, if a part of the software breaks, we can fix it from Earth.

## Technology Used
Software:
- Jupyter Notebook
- pynq.lib.video
- pynq.lib.led
- pynq.lib.button
- import time
- from time import sleep
- from pynq.overlays.base import BaseOverlap
- from PIL import Image
- import numpy as np

Hardware:
- PYNQ-Z2 FPGA
- To control the rover we used the board buttons to represent turning left, right, and going forward
- Use HDMI Output, monitor, and HDMI cord for rover movement display

## Project Demo
https://youtu.be/hfdToV_Foyk 

## Sources for Project
- https://www.amd.com/content/dam/amd/en/documents/resources/case-studies/nasa-mars-case-study.pdf
- https://pynq.readthedocs.io/en/latest/
- https://python-statemachine.readthedocs.io/en/latest/states.html
