# Motion-Sensor-Dipper
- #include  <LiquidCrystal.h> 
- #include <Servo.h>
- Servo servo1;
- Servo servo2;
Servo servo3;
Servo servo4;
int joyX = A0;
int joyY = A1;
int jjoyX = A2;
int jjoyY = A3;
int joyVal;
int trigpin = 12; 
int echopin = 13; 
int trigpin2 = 2; 
int echopin2 = 7; 
int sure; 
int distance1; 
int distance2; 
int rs = 11, en = 10, d4 = 8, d5 = 4, d6 = 1, d7 = 0; 
LiquidCrystal lcd(rs, en, d4, d5, d6, d7); 
void setup() {
  servo1.attach(3);
  servo2.attach(5);
  servo3.attach(6);
  servo4.attach(9);
  pinMode(trigpin, OUTPUT); 
  pinMode(echopin, INPUT); 
  pinMode(trigpin2, OUTPUT); 
  pinMode(echopin2, INPUT); 
  lcd.begin(16, 2); }
void loop() {
  {
  joyVal = analogRead(joyX);
joyVal = map (joyVal, 0, 1023, 0, 180); 
servo1.write(joyVal); 
joyVal = analogRead(joyY);
joyVal = map (joyVal, 0, 1023, 0, 180);
servo2.write(joyVal);
delay(15);
joyVal = analogRead(jjoyX);
joyVal = map (joyVal, 0, 1023, 0, 180); 
servo3.write(joyVal); 
joyVal = analogRead(jjoyY);
joyVal = map (joyVal, 0, 1023, 0, 180);
servo4.write(joyVal);
  delay(15);}
digitalWrite(trigpin , HIGH);
delayMicroseconds(1000);
digitalWrite(trigpin , LOW);
sure = pulseIn(echopin , HIGH);
distance1 = (sure/2) / 29.1;
digitalWrite(trigpin2 , HIGH);
delayMicroseconds(1000);
digitalWrite(trigpin2 , LOW);
sure = pulseIn(echopin2 , HIGH);
distance2 = (sure/2) / 29.1;
if (distance1 <= 20){
lcd.print("!!BE CAREFUL <-- !!");
delay(500);
lcd.clear();
delay(500);}
 else if (distance2 <= 20){
lcd.print("!!BE CAREFUL --> !!");
delay(500);
lcd.clear();
delay(500);}
}
