# InternshipsProjectsBased
Internship project for the 2nd semester of the 3rd year
# Members;
Furkan AY  COM20/B

Akif Can DUMAN  COM20/B

# Project;
Car Parking Sensor

# Car Parking Sensor;

What is the parking sensor with Arduino, how to make an arduino car parking sensor, I will be giving the answer to all of these in the next part of the article. But before we go into the article, let's talk a little bit about what a parking sensor is.

Simply put, parking sensors are distance sensors designed to warn the driver inside the vehicle by detecting obstacles around the vehicle at the time of parking.

Parking sensors are products that are already on sale. The issue that interests us in this article is how we can make a parking sensor using an arduino and a distance sensor. The incoming data is evaluated by a sensor that performs continuous distance control. Buzzer and/or led will be active according to the range of distance. It is not easy to describe this in writing. You will understand more clearly in the source code and the related video. Then if you're ready, let's start by getting to know the arduino parking sensor materials.


# Arduino Parking Sensor Supplies;
~ breadboard

~ Jumper Cable

~ HC-SR04 Ultrasonic Distance Sensor

~ Green Led 5mm

~ Yellow Led 5mm

~ Red Led 5mm

~ buzzer

~ Arduino Uno

~ Resistance
# HC-SR04 Ultrasonic Distance Sensor;

Ultrasonic Distance Sensor measures the multiplying and returning speed of the ultrasonic sound wave it creates and presents the data to the user. Its distance is minimum 2 cm and maximum 400 cm, which is quite sufficient for our purpose. You can find the detailed article for the HC-SR04 Sensor here.
# Buzzer;
Buzzer is a circuit element that can operate with small voltages and produce sound with the incoming electrical signal.
You can quickly and easily access the necessary materials for the Arduino parking sensor from Robotistan.com and complete your project. Now let's move on to the construction of a parking sensor with Arduino.
# Arduino Parking Sensor Circuit Diagram;
![arduino-park-sensoru-devre-semasi](https://user-images.githubusercontent.com/73740265/234953928-cd2f91ba-7b59-4b31-93e7-0ff32bcf4c58.png)
# Parking Sensor Arduino Codes;
#include <Arduino.h>

int triggerPin = 5;

int echoPin = 6;

int buzzer = 11;

long zaman;

int mesafe;

void setup()

{

  pinMode(3,OUTPUT); 
  
  pinMode(9,OUTPUT);
  
  pinMode(10 ,OUTPUT); 
  
  pinMode(triggerPin, OUTPUT);
  
  pinMode(echoPin, INPUT);
  
  Serial.begin(9600);
  
}


void loop(){
 
  int i=0;
  
  digitalWrite(triggerPin, LOW);
  
  delayMicroseconds(2);
  
  digitalWrite(triggerPin, HIGH);
  
  delayMicroseconds(10);
  
  digitalWrite(triggerPin, LOW);
  
  zaman = pulseIn(echoPin, HIGH);
  
  mesafe = zaman * 0.034 / 2;
  
  if (mesafe <12) {  
  
    digitalWrite(9,LOW);
    
    digitalWrite(10,LOW);
    
    digitalWrite(3,HIGH);
    
    tone(buzzer,250);
    
  }
  
  else if (mesafe > 18 && mesafe<= 25) {
  
    digitalWrite(3,LOW);
    
    digitalWrite(10,LOW);
    
    digitalWrite(9,HIGH);
    
    while (i<2){
    
      i++;
      
      tone(buzzer,450);
      
      delay(200);
      
      noTone(buzzer);
      
      delay(200);
      
    }
    
    delay(2000);
    
  }
  
  else if (mesafe >= 12 && mesafe<= 18) {
  
    digitalWrite(3,LOW);
    
    digitalWrite(10,LOW);
    
    digitalWrite(9,HIGH);
    
    while (i<2) {
    
      i++;
      
      tone(buzzer,450);
      
      delay(200);
      
      noTone(buzzer);
      
      delay(200);
      
    }
    
    delay(200);
    
  }
  
  else if (mesafe>25 ) { 
  
    digitalWrite(9,LOW);
    
    digitalWrite(3,LOW);
    
    digitalWrite(10,HIGH);
    
    noTone(buzzer);
    
  }
  
}

}


