#include <Adafruit_CircuitPlayground.h>

const int buzzer = A1;

void setup() {
  // put your setup code here, to run once:
  CircuitPlayground.begin();
  pinMode(buzzer, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:  
   Serial.println(CircuitPlayground.temperatureF());
//   if(temp < 100){
//      makeTone(buzzer, 440, 100);
//   }
//   else if(temp > 500){
//    makeTone(buzzer, 200, 500);
//   }
}
void makeTone (unsigned char speakerPin, int frequencyInHertz, long timeInMilliseconds) {
  int x;   
  long delayAmount = (long)(1000000/frequencyInHertz);
  long loopTime = (long)((timeInMilliseconds*1000)/(delayAmount*2));
  for (x=0; x<loopTime; x++) {        // the wave will be symetrical (same time high & low)
     digitalWrite(speakerPin,HIGH);   // Set the pin high
     delayMicroseconds(delayAmount);  // and make the tall part of the wave
     digitalWrite(speakerPin,LOW);    // switch the pin back to low
     delayMicroseconds(delayAmount);  // and make the bottom part of the wave
  }  
}
