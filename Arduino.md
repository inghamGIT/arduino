# Prácticas con Arduino

## Práctica 1

<img src=Practica1.png>

```c++
int led = 13;

void setup() {
  pinMode(led, OUTPUT);
}

void loop() {
  digitalWrite(led, HIGH);
  delay(1000);
  digitalWrite(led, LOW);
  delay(1000);
}
```

## Práctica 2

<img src=Practica2.png>

```c++
//Codigo básico
void setup() {
  for (int i = 11; i <= 13; i++) {
    pinMode(i, OUTPUT);
  }
}

void loop() {
  for (int i=11; i <= 13 ; i++) {
    digitalWrite(i, HIGH);
    delay(200);
    digitalWrite(i, LOW);
    delay(200);
  }
}
```

```c++
//Código parpadeo incremental
int incremento = 0
void setup() {
  for (int i = 11; i <= 13; i++) {
    pinMode(i, OUTPUT);
  }
}

void loop() {
  for (int i=11 ; i <= 13 ; i++) {
    digitalWrite(i, HIGH);
    delay(500-incremento);
    digitalWrite(i, LOW);
    delay(500-incremento);
  }
  if (incremento < 400) {
    incremento += 100;
  }
}
```

```c++
//Todos a la vez
void setup() {
  for (int i = 11; i <= 13; i++) {
    pinMode(i, OUTPUT);
  }
}

void loop() {
  digitalWrite(11, HIGH);
  digitalWrite(12, HIGH);
  digitalWrite(13, HIGH);
  delay(200);
  digitalWrite(11, LOW);
  digitalWrite(12, LOW);
  digitalWrite(13, LOW);
  delay(200);
}
```

```c++
//Segundo LED alternado
void setup() {
  for (int i = 11; i <= 13; i++) {
    pinMode(i, OUTPUT);
  }
}

void loop() {
  digitalWrite(11, HIGH);
  digitalWrite(12, LOW);
  digitalWrite(13, HIGH);
  delay(200);
  digitalWrite(11, LOW);
  digitalWrite(12, HIGH);
  digitalWrite(13, LOW);
  delay(200);
}
```

## Práctica 3

<img src=Practica3.png>

```c++
void setup() {
  for (int i = 10 ; i <= 13 ; i++) {
    pinMode(i, OUTPUT);
  }
  pinMode(9, OUTPUT);
}

void loop() {  
  for (int i=10 ; i <= 13 ; i++) {
    digitalWrite(i, HIGH);
    delay (200);
    digitalWrite(i, LOW);
    delay(200) ;
    if (i == 13) {
      tone(9, 1000);
      delay(1000);
    }
    else {
      noTone(9);
      delay(1000);
    }
  }
}
```

## Práctica 4

<img src=Practica4.png>

```c++
#include <Servo.h>
Servo servo1;
int angulo = 0;
int pin = 9;
void setup() {
  servo1.attach(pin);
}

void loop() {
  for(angulo  = 0; angulo  <= 180; angulo  += 1) {
    servo1.write(angulo);
    delay(25);
  }
  for(angulo  = 180; angulo  >=0; angulo  -=1) {
    servo1.write(angulo);
    delay(25);
  }
}
```

## Práctica 5

<img src=Practica5.png>

```c++
#include <Servo.h>
Servo servo1;
int angulo = 0;
int pin = 13;
void setup() {
  servo1.attach(pin);
  pinMode(2, INPUT);
}

void loop() {
  if (digitalRead(2) == HIGH) {
    for(angulo  = 0; angulo  <= 180; angulo  += 1) {
      servo1.write(angulo);
      delay(25);
    }
    for(angulo  = 180; angulo  >=0; angulo  -=1) {
      servo1.write(angulo);
      delay(25);
    }
  }
  else {
    servo1.write(angulo);
    delay(25);
  }
}
```

## Práctica 6

<img src=Practica6.png>

```c++
int trigPin = 10;
int echoPin = 9;
int led = 3;
long duration, cm;
 
void setup() {
  Serial.begin (9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(led, OUTPUT);
}
 
void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(5);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
 
  pinMode(echoPin, INPUT);
  duration = pulseIn(echoPin, HIGH);
  cm = (duration/2) /29.1;
  
  if(cm < 20) {
    digitalWrite(led, HIGH);
  }
  else {
    digitalWrite(led, LOW);
  }
  delay(250);
}
```