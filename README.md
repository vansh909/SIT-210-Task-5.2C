import tkinter as tk
import RPi.GPIO as GPIO

GPIO.setmode(GPIO.BCM)

GPIO.setup(27,GPIO.OUT)
GPIO.setup(22,GPIO.OUT)
GPIO.setup(17,GPIO.OUT)

GPIO.setup(27,GPIO.LOW)
GPIO.setup(22,GPIO.LOW)
GPIO.setup(17,GPIO.LOW)

win =tk.Tk()
win.title("LED Blink by Vansh Tomer")
win.geometry('800x600')


def green():
    if GPIO.input(27):
        GPIO.output(27, GPIO.LOW)
        green_button.config(text="Green Led: OFF")
    else:
        GPIO.output(27, GPIO.HIGH)
        GPIO.output(22, GPIO.LOW)
        GPIO.output(17, GPIO.LOW)
        green_button.config(text="Green Led: ON")

def blue():
    if GPIO.input(22):
        GPIO.output(22, GPIO.LOW)
        blue_button.config(text="Blue Led: OFF")
    else:
        GPIO.output(22, GPIO.HIGH)
        GPIO.output(27, GPIO.LOW)
        GPIO.output(17, GPIO.LOW)
        blue_button.config(text="Blue Led: ON")
        
def red():
    if GPIO.input(17):
            GPIO.output(17, GPIO.LOW)
            red_button.config(text="Red Led: OFF")
    else:
        GPIO.output(17, GPIO.HIGH)
        GPIO.output(27, GPIO.LOW)
        GPIO.output(22, GPIO.LOW)
        red_button.config(text="Red Led: ON")
        
   

green_button = tk.Radiobutton(win, text="Green Led: OFF", command=green)
green_button.pack(pady=10)
blue_button = tk.Radiobutton(win, text="Blue Led: OFF", command=blue)
blue_button.pack(pady=10)
red_button = tk.Radiobutton(win, text="Red Led: OFF", command=red)
red_button.pack(pady=10)

def exit():
    GPIO.cleanup()
    win.quit()


exit_button = tk.Button(win, text="Exit", command=exit)
exit_button.pack(pady=10)


win.mainloop()
