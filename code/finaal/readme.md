#include "arduino_secrets.h"
#include "thingProperties.h"

// pin definitie
#define PUMP_PIN 10          // kies vrije digitale pin
#define MOISTURE_PIN 2       // analoge pin (ADC)

// timing variabelen
unsigned long previousMillis;
unsigned long sampleRate = 1000; // 1 sec sampletijd

void setup() 
{
  Serial.begin(115200);
  delay(1000);

  // fix voor WiFi TX power bug
  WiFi.begin();
  WiFi.setTxPower(WIFI_POWER_8_5dBm);

  initProperties();
  ArduinoCloud.begin(ArduinoIoTPreferredConnection);
  setDebugMessageLevel(4);
  ArduinoCloud.printDebugInfo();

  pinMode(PUMP_PIN, OUTPUT);
  previousMillis = millis();
}

void loop() 
{
  ArduinoCloud.update();

  if (millis() - previousMillis > sampleRate)
  {
    moisture = analogRead(MOISTURE_PIN);
    previousMillis = millis();
  }

  if (moisture < thresholdLow) pump = true;
  else if (moisture > thresholdHigh) pump = false;

  digitalWrite(PUMP_PIN, pump);
}

void onThresholdLowChange() {}
void onThresholdHighChange() {}
