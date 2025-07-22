#include <LiquidCrystal.h>

// LCD pins: RS, E, D4, D5, D6, D7
LiquidCrystal lcd(7, 6, 5, 4, 3, 2);

const int sensorA = 8;
const int sensorB = 9;

unsigned long startTime = 0;
unsigned long endTime = 0;
float distance = 0.2; // Distance between sensors in meters (20 cm)

void setup() {
  pinMode(sensorA, INPUT);
  pinMode(sensorB, INPUT);
  lcd.begin(16, 2);
  lcd.print("Speed Detector");
  delay(2000);
  lcd.clear();
}

void loop() {
  lcd.setCursor(0, 0);
  lcd.print("Waiting...");

  // Wait for first sensor to be triggered
  while (digitalRead(sensorA) == HIGH);
  startTime = millis();

  // Wait for second sensor to be triggered
  while (digitalRead(sensorB) == HIGH);
  endTime = millis();

  // Calculate time taken
  float timeTaken = (endTime - startTime) / 1000.0; // in seconds

  // Calculate speed in m/s
  float speedMS = distance / timeTaken;
  float speedKMH = speedMS * 3.6;

  // Display
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Speed:");
  lcd.setCursor(0, 1);
  lcd.print(speedKMH);
  lcd.print(" km/h");

  delay(3000); // Wait before next reading
  lcd.clear();
}
