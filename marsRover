import time
from time import sleep
from pynq.overlays.base import BaseOverlay
base = BaseOverlay("base.bit")
from PIL import Image
import numpy as np
from pynq.lib.video import *

hdmi_out = base.video.hdmi_out
hdmi_out.configure(VideoMode(1920, 1080, 24))  # Adjust the resolution and color depth as needed
hdmi_out.start()

led0 = base.leds[0]
led1 = base.leds[1]
led2 = base.leds[2]
led3 = base.leds[3]
button0 = base.buttons[0]
button1 = base.buttons[1]
button2 = base.buttons[2]
button3 = base.buttons[3]
sw0 = base.switches[0]
sw1 = base.switches[1]

state = 4

def state_action(argument):
    global state
    match argument:
        case 0:
            led0.off()
            led1.off()
            led2.off()
            led3.off()
        case 1:
            led0.on()
            led1.off()
            led2.off()
            led3.off()
            
            # Path to the local image file on the board
            image_path = "/home/xilinx/jupyter_notebooks/up.png"   # Modify this path according to your image file location

            # Open the image file
            image = Image.open(image_path)

            # Resize the image to match HDMI output resolution
            image = image.resize((hdmi_out.mode.width, hdmi_out.mode.height))

            # Convert the image to grayscale
            image_gray = image.convert('L')

            # Convert the grayscale image to a NumPy array
            image_np = np.array(image_gray)

            # Create a new frame buffer for HDMI output
            outframe = hdmi_out.newframe()

            # Copy the grayscale image_np array to the outframe buffer
            outframe[0:1080, 0:1920, 0] = image_np[0:1080, 0:1920]

            # Write the frame buffer to the HDMI output
            hdmi_out.writeframe(outframe)

        case 2:
            led0.off()
            led1.on()
            led2.off()
            led3.off()
            
            # Path to the local image file on the board
            image_path = "/home/xilinx/jupyter_notebooks/left.png"   # Modify this path according to your image file location

            # Open the image file
            image = Image.open(image_path)

            # Resize the image to match HDMI output resolution
            image = image.resize((hdmi_out.mode.width, hdmi_out.mode.height))

            # Convert the image to grayscale
            image_gray = image.convert('L')

            # Convert the grayscale image to a NumPy array
            image_np = np.array(image_gray)

            # Create a new frame buffer for HDMI output
            outframe = hdmi_out.newframe()

            # Copy the grayscale image_np array to the outframe buffer
            outframe[0:1080, 0:1920, 0] = image_np[0:1080, 0:1920]

            # Write the frame buffer to the HDMI output
            hdmi_out.writeframe(outframe)

        case 3:
            led0.off()
            led1.off()
            led2.on()
            led3.off()
            
            # Path to the local image file on the board
            image_path = "/home/xilinx/jupyter_notebooks/r1.png"   # Modify this path according to your image file location

            # Open the image file
            image = Image.open(image_path)

            # Resize the image to match HDMI output resolution
            image = image.resize((hdmi_out.mode.width, hdmi_out.mode.height))

            # Convert the image to grayscale
            image_gray = image.convert('L')

            # Convert the grayscale image to a NumPy array
            image_np = np.array(image_gray)

            # Create a new frame buffer for HDMI output
            outframe = hdmi_out.newframe()

            # Copy the grayscale image_np array to the outframe buffer
            outframe[0:1080, 0:1920, 0] = image_np[0:1080, 0:1920]

            # Write the frame buffer to the HDMI output
            hdmi_out.writeframe(outframe)
        case 4:
            print("Booting up")
        case default:
            print("ERROR")

def state_transition(argument):
    global state
    match argument:
        case 0:
            if (sw0.read()== 1):
                print("going forward")
                state = 1
            else:
                state = 0
        case 1:
            if (button0.read() == 1):
                state = 1
            elif (button1.read() == 1):
                print ("Rotating left")
                state = 2
            elif (button2.read() == 1):
                print ("Rotating Right")
                state = 3
        case 2:
            if (button0.read() == 1):
                print("going forward")
                state = 1
            elif (button1.read() == 1):
                state = 2
            elif (button2.read() == 1):
                print ("Rotating Right")
                state = 3
        case 3:
            if (button0.read() == 1):
                print("going forward")
                state = 1
            elif (button1.read() == 1):
                print ("Rotating left")
                state = 2
            elif (button2.read() == 1):
                state = 3
        case 4:
            state = 0
            print("Going to off state")
        case default:
            print("Transition Error")
            
while (True):
    state_action(state)
    state_transition(state)
