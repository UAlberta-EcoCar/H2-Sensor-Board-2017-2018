int H2_OK_PIN = A0; // Initialize variable for H2-board output pin
int H2_SENSOR_PIN = A4; // Initialize variable for H2-sensor output pin
int H2_LED1_PIN = A2; // Initialize variable for H2 indicator LED (LED1 on board--red)

int ESTOP1_PIN = 2; // Initialize variable for ESTOP1 pin
int ESTOP2_PIN = 3; // Initialize variable for ESTOP2 pin
int ESTOP_LED2_PIN = A3; // Initialize variable for ESTOP indicator LED (LED2 on board--blue)

int h2_sensor_value; // Initialize input variable for H2_SENSOR_PIN
int h2_sensor_cutoff = 95; // Initialize variable to store cutoff value for H2-sensor
bool estop1_value; // Initialize input variable for ESTOP1_PIN
bool estop2_value; // Initialize input variable for ESTOP2_PIN


void setup() {
  pinMode(H2_OK_PIN, OUTPUT); // Set H2_OK_PIN to output
  pinMode(H2_LED1_PIN, OUTPUT); // Set H2_LED1_PIN to output
  pinMode(ESTOP_LED2_PIN, OUTPUT); // Set ESTOP_LED2_PIN to output
  pinMode(H2_SENSOR_PIN, INPUT); // Set H2_SENSOR_PIN to input
  pinMode(ESTOP1_PIN, INPUT); // Set ESTOP1_PIN to input
  pinMode(ESTOP2_PIN, INPUT); // Set ESTOP2_PIN to input

  Serial.begin(9600); // Begin serial monitor output -- for testing and setting a value for h2_sensor_cutoff (remove later)
}

void loop() {
  h2_sensor_value = analogRead(H2_SENSOR_PIN); // Read value from H2_SENSOR_PIN and store in h2_sensor_value
  estop1_value = digitalRead(ESTOP1_PIN); // Read value from ESTOP1_PIN and store in estop1_value
  estop2_value = digitalRead(ESTOP2_PIN); // Read value from ESTOP2_PIN and store in estop2_value


  if ((estop1_value == LOW) || (estop2_value == LOW) || (h2_sensor_value >= h2_sensor_cutoff))
  {
    digitalWrite(H2_OK_PIN, LOW); // If either ESTOP is pushed or excess hydrogen is sensed, shut down system
  }
  else
  {
    digitalWrite(H2_OK_PIN, HIGH); // If everything ok, keep H2 pin set to ok
  }

  if ((estop1_value == LOW) || (estop2_value == LOW)) // If either ESTOP is pushed turn on indicator LED
  {
    digitalWrite(ESTOP_LED2_PIN, HIGH); // Turn on blue LED
  }
  else
  {
    digitalWrite(ESTOP_LED2_PIN, LOW); // If no ESTOPs are pushed keep blue LED off
  }



  if (h2_sensor_value >= h2_sensor_cutoff) // If excess hydrogen is sensed, turn on H2 indicator LED
  {
    digitalWrite(H2_LED1_PIN, HIGH); // Turn on red LED
  }
  else
  {
    digitalWrite(H2_LED1_PIN, LOW); // If no excess hydrogen, keep red LED off
  }



  Serial.println(h2_sensor_value); // Print read value from H2 sensor to serial monitor -- for testing and setting a suitable value for h2_sensor_cutoff (remove later)
  delay(500); // Delay reading to make serial monitor easier to track (remove later)

}
