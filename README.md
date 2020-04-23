# IoT
Smart Street Light System
#define trigPin 6
#define echoPin 5
#define led 10
#define led1 11
int ldr=A0;
float data;
void setup()
{ Serial.begin (9600);
pinMode(ldr,INPUT);
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
pinMode(led, OUTPUT);
}

void loop()
{ 
data=analogRead(A0);
Serial.println(data);
delay(100);
if(data<=100)
{
  digitalWrite(led,LOW);
  digitalWrite(led1,LOW);  
}
else if(data>=200)
{
  
long duration, distance;
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
duration = pulseIn(echoPin, HIGH);
distance = (duration/2) / 29.1;

if (distance < 5)

{ digitalWrite(led,HIGH);
  digitalWrite(led1,HIGH);
  delay(2000);
}

else {

analogWrite(led,20);
analogWrite(led1,20);

}

Serial.print(distance);

Serial.println(" cm");

delay(500);
}

}
