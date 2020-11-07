# Printing Precisely - Desktop 3D Printer Calibration
Eric Moyer

Files and instructions: https://hackaday.io/project/175611-remoticon-printing-precisely-demo

Uses this excellent resource: https://teachingtechyt.github.io/calibration.html

# Bed Level and Nozzle Offset

Nozzle offset from the bed, often checked with a piece of paper between the nozzle and the bed. Which means it will be off by the thickness of the paper you need to adjust for.
Instead of paper, he has printed five squares that he has placed in the corners and center of the bed. Generates it using the following tool.
Recommends the use of this fantastic tool: https://teachingtechyt.github.io/calibration.html#firstlayer
Generates g-code you can run on your printer. Opens right up in Cura.
If you don't want to use the tool, he has put STLs on his git repo linked from his Hackaday page.s
The teaching tech tool also has photos of poor results and what causes them.

# Retraction Tuning

Used this retraction tuning tool: https://teachingtechyt.github.io/calibration.html#retraction

Generates this excellent model with two stacked sets of cylinders where you can change the retraction distance for each segment of the tower

# Temperature

The tool also generates a multi-segmented "tower" where you can set the temperature for each segment to tune this well: https://teachingtechyt.github.io/calibration.html#temp

Also tests how well your bridging is doing which is excellent.

Recommends you tune your retraction before temperature or else you will get awful stringining across gaps.

# Extrusion/Flow

The right page on the tool for this step is here: https://teachingtechyt.github.io/calibration.html#flow

Generates these thin hollow boxes that lets you play with flow rate. You can target a specific wall thickness and then enter your measured thickness from the real print to get a new flow rate recommendation.