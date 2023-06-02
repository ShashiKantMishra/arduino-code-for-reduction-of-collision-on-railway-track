//# arduino-code-for-reduction-of-collision-on-railway-track
// Define ultrasonic sensor pins
const int sensor1_trigger_pin = 13; // pin 13 of the arduino connect to the first sensor trigger pin
const int sensor1_echo_pin = 12;  // pin 12 of the arduino connect to the first sensor echo pin
const int sensor2_trigger_pin = 11;  // pin 11 of the arduino connect to the second sensor trigger pin
const int sensor2_echo_pin = 10;  // pin 10 of the arduino connect to the second sensor echo pin
const int sensor3_trigger_pin = 9;  // pin 9 of the arduino connect to the third sensor trigger pin
const int sensor3_echo_pin = 8;  // pin 8 of the arduino connect to the third sensor echo pin


const int area1 =7; // connect the pin 7 of the arduino to activate the area as per command
const int area2 = 6; // connect the pin 6 of the arduino to activate the area as per command
const int area3 = 5; // connect the pin 5 of the arduino to activate the area as per command

void setup() {
  // Initialize sensor pins
  pinMode(sensor1_trigger_pin, OUTPUT);
  pinMode(sensor1_echo_pin, INPUT);
  pinMode(sensor2_trigger_pin, OUTPUT);
  pinMode(sensor2_echo_pin, INPUT);
  pinMode(sensor3_trigger_pin, OUTPUT);
  pinMode(sensor3_echo_pin, INPUT);
  
  // Initialize area pins
  pinMode(area1, OUTPUT);
  pinMode(area2, OUTPUT); 
  pinMode(area3, OUTPUT);

  digitalWrite(area1, LOW); // the LED1 is "OFF".
  digitalWrite(area2, LOW); // the LED2 is "OFF".
  digitalWrite(area3, LOW); // the LED3 is "OFF".
}

void loop() {
  // Read sensor 1 it is a basic code for the ultrasonic sensor
  long duration1, distance1;
  digitalWrite(sensor1_trigger_pin, LOW);
  delayMicroseconds(2);
  digitalWrite(sensor1_trigger_pin, HIGH);
  delayMicroseconds(10);
  digitalWrite(sensor1_trigger_pin, LOW);
  duration1 = pulseIn(sensor1_echo_pin, HIGH);
  distance1 = duration1 / 58;
  
  // Read sensor 2
  long duration2, distance2;
  digitalWrite(sensor2_trigger_pin, LOW);
  delayMicroseconds(2);
  digitalWrite(sensor2_trigger_pin, HIGH);
  delayMicroseconds(10);
  digitalWrite(sensor2_trigger_pin, LOW);
  duration2 = pulseIn(sensor2_echo_pin, HIGH);
  distance2 = duration2 / 58;
  //read sensor 3
  long duration3, distance3;
  digitalWrite(sensor3_trigger_pin, LOW);
  delayMicroseconds(2);
  digitalWrite(sensor3_trigger_pin, HIGH);
  delayMicroseconds(10);
  digitalWrite(sensor3_trigger_pin, LOW);
  duration3 = pulseIn(sensor3_echo_pin, HIGH);
  distance3 = duration3 / 58;
  
  
  if (distance1 >= 5 && distance1 <= 6) {  // here we decide the range of a sensor where the sensor is working for the first sensor
    digitalWrite(area1, HIGH);
  }
  
  if (distance2 >= 5 && distance2 <= 6) {  // here we decide the range of a sensor where the sensor is working for the second sensor
    digitalWrite(area2, HIGH);
  }
  if (distance3 >= 6 && distance3 <= 7) {  // here we decide the range of a sensor where the sensor is working for the third sensor
    digitalWrite(area3, HIGH);
    delay(2000);
    digitalWrite(area1,LOW);
    delay(2000);
    digitalWrite(area2,LOW);
    delay(5000);
    digitalWrite(area3, LOW);
  } 
}// the whole loop will be continue after the loop is completed.
