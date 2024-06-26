# Project-2
![Grand Migelo (1)](https://github.com/HoseaKamau/Project-2/assets/172508721/da04a69b-e476-4600-a922-016985e73e86)
int pmeter = A0;
int forwardPin = 11;
int backwardPin = 10;
int greenLED = 3;
int yellowLED = 4;
int redLED = 5;
String mgs1 = "slow speed";
String mgs2 = "medium speed";
String mgs3 = "high speed";

void setup()
{
  pinMode(pmeter, INPUT);
  pinMode(forwardPin, OUTPUT);
  pinMode(backwardPin, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(redLED, OUTPUT);
  Serial.begin(9600); 
}

void loop(){
  int calc = analogRead(pmeter);
  int speed = map(calc, 0, 1023, 0, 255);
  
  if (calc > 0 && calc <= 200){
 	analogWrite(forwardPin,speed);
  	analogWrite(backwardPin,0);
    digitalWrite(greenLED, HIGH);
    digitalWrite(redLED, LOW);
    digitalWrite(yellowLED, LOW);
    Serial.println(mgs1);
  
  }
  else if (calc > 50 && calc <= 400){
 	analogWrite(forwardPin,speed);
  	analogWrite(backwardPin,0);
    digitalWrite(yellowLED, HIGH);
    digitalWrite(redLED, LOW);
    digitalWrite(greenLED, HIGH);
    Serial.println(mgs2);
  }
    else if (calc > 1000){
 	analogWrite(forwardPin,speed);
  	analogWrite(backwardPin,0);
    digitalWrite(redLED, HIGH);
    digitalWrite(greenLED, HIGH);
    digitalWrite(yellowLED, HIGH);
    Serial.println(mgs3);
    }
  else{
  analogWrite(forwardPin, 0);
  	analogWrite(backwardPin,0);
  }
}
