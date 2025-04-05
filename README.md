# Fem-codes
# this project is made by the students from 2nd year ECE
# currently pursuing degree at kit- kalaignarkarunanidhi institute of technology
# this project is made by us iorder to design and implement automated sorting system using mechatronics principle
# we have simulated using a software called tinkercad
# output is obtained by running a code and the items are sorted by colours
# owners must be given credit for the project
#include <Servo.h>

// Create a Servo object
Servo sorterServo;

// Define button pins
const int redButton = 2;
const int blueButton = 3;
const int resetButton = 4;

// State variable to track which color was detected
int state = 0; // 0 = idle, 1 = red, 2 = blue

void setup() {
  // Attach the servo to pin 9
  sorterServo.attach(9);

  // Set button pins as input
  pinMode(redButton, INPUT);
  pinMode(blueButton, INPUT);
  pinMode(resetButton, INPUT);

  // Start with servo in center position (idle)
  sorterServo.write(90);
}

void loop() {
  // Check if Red button is pressed
  if (digitalRead(redButton) == HIGH) {
    state = 1;
  }

  // Check if Blue button is pressed
  if (digitalRead(blueButton) == HIGH) {
    state = 2;
  }

  // Check if Reset button is pressed
  if (digitalRead(resetButton) == HIGH) {
    state = 0;
  }

  // Move servo based on state
  if (state == 1) {
    sorterServo.write(0);    // Move to left for red
  } 
  else if (state == 2) {
    sorterServo.write(180);  // Move to right for blue
  } 
  else {
    sorterServo.write(90);   // Center position (idle/reset)
  }
 delay(100); // Small delay for stability
}
