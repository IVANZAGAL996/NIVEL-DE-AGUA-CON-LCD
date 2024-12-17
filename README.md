# NIVEL-DE-AGUA-CON-LCD

# Introducción

 En esta practica se utilizara  un sensor ultrasonico en una placa de desarrollo ESP32 y un display LCD en donde se mostrara el nivel del tanque.

# Material Necesario
Para realizar esta practica necesitas lo siguiente:

- WOKWI
- Tarjeta ESP32
- Sensor ultrasonico HC-SR04
- RELAYS
- LCD (16x2) 12c

# Requisitos previos:
Para poder usar este repositorio necesitas entrar a la plataforma WOKWI.

Instrucciones de preparación de entorno:
1.-Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=2 && safetyDistance<=5)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=5 && safetyDistance<=10) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else
{
 digitalWrite(led1,  LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```


