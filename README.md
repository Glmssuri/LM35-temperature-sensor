//interface the LM35 temperature sensor with an Arduino Uno. 
// LM35 Temperature Sensor Interface with Arduino Uno

// Define constants
const int lm35Pin = A0;  // Analog pin for LM35 sensor
const int ledPin = 13;   // Digital pin for onboard LED

void setup() {
  Serial.begin(9600);   // Initialize serial communication
  pinMode(ledPin, OUTPUT);  // Set LED pin as output
}

void loop() {
  // Read analog voltage from LM35 sensor
  int sensorValue = analogRead(lm35Pin);
  
  // Convert analog value to temperature in Celsius
  float temperature = (sensorValue * 5.0 / 1023.0) * 100.0;
  
  // Print temperature to serial monitor
  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.println(" °C");

  // Control onboard LED based on temperature
  if (temperature > 25.0) {
    digitalWrite(ledPin, HIGH);  // Turn on LED if temperature is above 25°C
  } else {
    digitalWrite(ledPin, LOW);   // Turn off LED otherwise
  }

  // Add a delay or other non-blocking mechanisms if needed
}
