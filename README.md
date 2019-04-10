# Sun-Track
# Introduction : The Project named "Solar Tracker" is about making the project in which the solar panel mounted system is rotating as per the direction of Sun so that we get continuous energy generation throughout the day.
# Arduino IDE Code
#include<Servo.h>                      //Including Servo library
Servo Servoud;                         // Initialising Servo for Up-Down Movement
Servo Servolr;                         // Initialising Servo for Left-Right Movement
int initialud=45;                     // Up-Down initial angle = 45 deg.
int initiallr=90;                     // Left-Right initial angle = 90 deg.
void setup()
{
  pinMode(A0,OUTPUT);       // LDR 1
  pinMode(A1,OUTPUT);       // LDR 2
  pinMode(A2,OUTPUT);       // LDR 3
  pinMode(A3,OUTPUT);       // LDR 4
  Serial.begin(9600);
  Servoud.attach(10);         // attaching Servo up-down
  Servolr.attach(9);          // attaching Servo left-right
  Servoud.write(initialud);
  Servolr.write(initiallr);
}
void loop()
{
 int l1=analogRead(A0);
  int l2=analogRead(A1);
  int l3=analogRead(A2);
 int  l4=analogRead(A3);
 
 Serial.print(l1);
 Serial.print(' ');
 Serial.print(l2);
 Serial.print(' ');
 Serial.print(l3);
 Serial.print(' ');
 Serial.println(l4);
 delay(200);

if(l1>l2&&l4>l3)
  {
    initialud=initialud+5;
    Servoud.write(initialud);
    Servolr.write(initiallr);
  }
 else if(l2>l1&&l3>l4)
  {
    initialud=initialud-5;
    Servoud.write(initialud);
    Servolr.write(initiallr);
  }
else  if(l4>l1&&l3>l2)
  {
    initiallr=initiallr+5;
    Servolr.write(initiallr);
    Servoud.write(initialud);
  }
else  if(l1>l4&&l2>l3)
  {
    initiallr=initiallr-5;
    Servolr.write(initiallr);
    Servoud.write(initialud);
  }
  else
  {
   ;
  }
}
