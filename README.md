# Smart-gate-

#include <Servo.h>

Servo parkingServo;
int irSensor = 2;
int servoPin = 9;

void setup() {
  
  pinMode(irSensor, INPUT);
  parkingServo.attach(servoPin);
  parkingServo.write(0);
  Serial.begin(9600);
}

void loop() {
  int carDetected = digitalRead(irSensor);
  if (carDetected == LOW) {
    Serial.println("Car detected! Opening gate...");
    parkingServo.write(90);
    delay(1000);
    parkingServo.write(0);
  } else {
    Serial.println("No car detected. Gate closed.");
  }
  delay(500);
}
