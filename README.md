<img width="4624" height="2604" alt="20211225_002616 1" src="https://github.com/user-attachments/assets/ada3093f-8c66-41b4-bb85-c9f811e0047e" />

 https://youtube.com/shorts/S4_pfjmVYE8


I designed this small robotic arm 5 years ago as a Christmas gift for my grandson. Originally, it was only controlled remotely via a smartphone app. Now my grandson is 13, and I am teaching him how to program. I try to find interesting topics so he doesn't get bored. We wrote new software for the old toy using AI assistance.

The arm was designed in Fusion 360. I modified the stepper motors to a 4-wire configuration following a mod found online; this makes them stronger, and they are driven by TMC2208 drivers. The 28BYJ-48 motors are cheap and have a built-in gearbox, but unfortunately, the backlash is quite significant, so the arm is not very precise. However, for games and education, it is perfectly fine, as the candy-picking task allows for a 1–2 mm margin of error.

The code was developed for an STM32F103 Blue Pill board using the Arduino IDE. It accepts G-code, which it translates into simple stepper steps. It connects wirelessly to a PC or smartphone via an HC-05 Bluetooth module.

All the more complex functions are handled in Python. The stepper steps are converted into cylindrical coordinates (degrees and millimeters) using a lookup table. This goes through another conversion into XYZ coordinates, which are then mapped to the camera's pixel coordinates using non-linear calibration. In the past, this was difficult, but today AI can solve it. However, you have to define the task very precisely and break it down into parts, because if left to its own devices, it can come up with unbelievable nonsense. For calibration, we printed a chart with black dots and specified the robot coordinates for each dot. The AI then mapped these to the camera's pixel coordinates.

The object recognition is based on the Python OpenCV library. First, it detects the edges of the candies by looking for sudden changes in brightness, then it filters for circular shapes and realistic sizes. After that, it calculates the average color inside the shape to determine the color of the candy. The code is not fully finished yet; the video shows the very first successful run. It doesn't sort them by color yet, but that is the next step.
