# Private Edge-Based Voice AI for Everything 
Alfred Gonzales Alfred.gonzalez@matrixlabs.ai
Github: https://github.com/Alfred-AdMobilize
https://github.com/matrix-io

Is using a very interesting voice application development board https://www.matrix.one/products/voice

Is using JavaScript and a special MATRIX library to build a voice appliance with specific wake words

The microphone seems to have some directionality- the LEDs follow the sound around the perimeter similar to an Echo Dot.

everloop.js is another library they are leveraging (https://matrix-io.github.io/matrix-documentation/matrix-core/javascript-examples/everloop/)

Appears to give access to the LEDs, microphone, and socket work 

Demo used various words to change the color of the LEDs on the top of the device

Matrix seems to have an excellent local voice recongition model

Demoer confirmed that the device has multiple microphones, but this demo involved just the one. Lots of interesting voice work can be done with the other mics

Support for JavaScript, Python, Ruby, and Go

The chip onboard is actually an FPGA (Xilinx Spartan 6) which is interesting. Says that you can have direct control of the FPGA if you don't want to use their high-level libraries.

Two versions- an RPi version or an ESP32 version

The RPI version can work offline, the ESP32 version will do the wakeword offline and then pip the audio to a cloud service or a remote Pi or computer