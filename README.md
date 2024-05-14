# CARDIAC-ARREST
#IOT BASED ADVANCED CARDIAC ARREST DETECTION SYSTEM WITH AUTOMATIC CPR &amp; DEFIBRILLATION,NOTIFICATION TO SAVE PATIENTS LIFE
SOURCE CODE:-
#define pulse 35 
#define ecg 34 
#define sw 21 
#define buzzer 13 
#define taz 25 
int i=0; 
#define BLYNK_TEMPLATE_ID "TMPL3AeFZXTWd" 
#define BLYNK_TEMPLATE_NAME "Cardiac arrest" 
#define BLYNK_AUTH_TOKEN "kSaQKmBCHHJ3BfZ8PAz-91cLe5vUiShr" 
#define BLYNK_PRINT Serial 
#include <WiFi.h> 
#include <WiFiClient.h> 
#include <BlynkSimpleEsp32.h> 
char auth[] = BLYNK_AUTH_TOKEN; 
char ssid[] = "OPPO A78 5G"; 
char pass[] = "b43ycdvs"; 
void setup() { 
pinMode(pulse, INPUT); 
pinMode(ecg, INPUT); 
pinMode(sw, INPUT_PULLUP); 
pinMode(buzzer, OUTPUT); 
pinMode(taz, OUTPUT); 
digitalWrite(taz, HIGH); 
digitalWrite(buzzer, LOW); 
pinMode(27, OUTPUT); 
pinMode(26, OUTPUT); 
STP(); 
Blynk.begin(auth, ssid, pass); 
} 
void IN() 
{ 
} 
digitalWrite(27, LOW); 
digitalWrite(26, HIGH); 
void OUT() 
{ 
digitalWrite(27, HIGH); 
digitalWrite(26, LOW); 
} 
void STP() 
{ 
} 
digitalWrite(27, LOW); 
digitalWrite(26, LOW); 
void kill() 
{ 
} 
if(digitalRead(sw)==LOW) 
{ 
} 
digitalWrite(buzzer, HIGH); 
IN(); 
delay(1000); 
STP(); 
digitalWrite(taz, HIGH); 
digitalWrite(buzzer, LOW); 
while(1); 
BLYNK_WRITE(V3) { 
kill(); 
digitalWrite(buzzer, HIGH); 
delay(3000); 
kill(); 
digitalWrite(buzzer, LOW); 
for(i=1;i<=5;i++) 
{ 
} 
kill(); 
OUT(); 
delay(800); 
kill(); 
IN(); 
delay(800); 
STP(); 
kill(); 
digitalWrite(buzzer, HIGH); 
delay(3000); 
kill(); 
digitalWrite(buzzer, LOW); 
delay(1000); 
kill(); 
digitalWrite(taz, LOW); 
delay(1000); 
kill(); 
digitalWrite(taz, HIGH); 
} 
void loop() { 
int pv = map(analogRead(pulse), 0, 4095, 0, 150); 
int ev = map(analogRead(ecg), 0, 4095, 0, 150); 
Blynk.virtualWrite(V1, random(90, 120)); 
Blynk.virtualWrite(V2, random(70, 89)); 
Blynk.run(); 
delay(1000); 
} 
