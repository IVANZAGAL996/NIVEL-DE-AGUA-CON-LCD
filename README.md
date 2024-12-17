# NIVEL-DE-AGUA-CON-LCD

# Introducción

 En esta practica se utilizara  un sensor ultrasonico en una placa de desarrollo ESP32 y un display LCD en donde se mostrara el nivel del tanque, cuando esta al 90, 75, 50, 25, y 0 %

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
const int led1 = 2;
const int led2 = 5;
const int led3 = 16;
const int led4 = 17;

#include <LiquidCrystal_I2C.h> //Libreria de LCD
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

// defines variables
long duration;
int distance;
int safetyDistance;
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
lcd.init();
lcd.backlight();
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
if (safetyDistance>=2 && safetyDistance<=10)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
lcd.clear();  
lcd.setCursor(0, 0);
lcd.print("NIVEL DE TANQUE ");
lcd.setCursor(6, 1);
lcd.print(" 90% ");
delay(2000);
}
else if(safetyDistance>=11 && safetyDistance<=20) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
  lcd.clear();
   lcd.setCursor(0, 0);
 lcd.print("NIVEL DE TANQUE ");
 lcd.setCursor(6, 1);
 lcd.print(" 75% ");
  delay(2000);
}
else if(safetyDistance>=21 && safetyDistance<=30) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
  lcd.clear(); 
  lcd.setCursor(0, 0);
lcd.print("NIVEL DE TANQUE ");
lcd.setCursor(6, 1);
lcd.print(" 50% ");
delay(2000);
}
else if(safetyDistance>=31 && safetyDistance<=40) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
  lcd.clear(); 
  lcd.setCursor(0, 0);
lcd.print("NIVEL DE TANQUE ");
lcd.setCursor(6, 1);
lcd.print(" 25% ");
delay(2000);
}
else
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
  lcd.clear(); 
  lcd.setCursor(0, 0);
lcd.print("NIVEL DE TANQUE ");
lcd.setCursor(6, 1);
lcd.print(" 0% ");
delay(2000);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```
Cargaremos las siguientes librerias:

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/LIBRERIAS.png)

insertamos sensor, display LCD Y 4 relays

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/sensor%203.PNG)

![](https://github.com/IVANZAGAL996/Ultrasonico-con-LCD/blob/main/lcd3.PNG)

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/RELAYS.png)

realizamos la siguiente conexión:

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-17%20002444.png)

Cargamos programa e iniciamos simulacion y obtenemos los siguientes resultados:

## Al 90 % (2>= && <=10)

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/NIVEL%2090.png)

## Al 75 % (11>= && <=20)

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/NIVEL%2075.png)

## Al 50 % (21>= && <=30)

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/NIVEL%2050.png)

## Al 25 % (31>= && <=40)

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/NIVEL%2025.png)

## Al 0 % (41>=)

![](https://github.com/IVANZAGAL996/NIVEL-DE-AGUA-CON-LCD/blob/main/NIVEL%200.png)


### creditos

Desarrollado por Edgar Ivan Prospero Zagal Ponce

[GitHub](https://github.com/IVANZAGAL996)


