# Python-code-for-Tkinter-
code for On screen control of height (Stepper motor) and pan/Tilt(Servo motors) adjustment through tkinter GUI using arrow icons.

import tkinter as tk
from gpiozero import Servo, Motor

# Initialize your servo and motor objects
pan_servo = Servo(17)  # Replace 17 with the actual GPIO pin
tilt_servo = Servo(18)  # Replace 18 with the actual GPIO pin
height_motor = Motor(forward=22, backward=23)  # Replace 22 and 23 with the actual GPIO pins

# Tkinter GUI setup
root = tk.Tk()
root.title("Selfie Booth Controls")

# Function to handle arrow button presses
def pan_left():
    pan_servo.value -= 0.1

def pan_right():
    pan_servo.value += 0.1

def tilt_up():
    tilt_servo.value += 0.1

def tilt_down():
    tilt_servo.value -= 0.1

def move_up():
    height_motor.forward()

def move_down():
    height_motor.backward()

# Create arrow buttons
left_button = tk.Button(root, text="←", command=pan_left)
right_button = tk.Button(root, text="→", command=pan_right)
up_button = tk.Button(root, text="↑", command=tilt_up)
down_button = tk.Button(root, text="↓", command=tilt_down)
up_arrow = tk.Button(root, text="⇧", command=move_up)
down_arrow = tk.Button(root, text="⇩", command=move_down)

# Place buttons in the GUI
left_button.grid(row=1, column=0)
right_button.grid(row=1, column=2)
up_button.grid(row=0, column=1)
down_button.grid(row=2, column=1)
up_arrow.grid(row=0, column=3)
down_arrow.grid(row=2, column=3)

# Run the Tkinter main loop
root.mainloop()
