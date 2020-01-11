[arduino_logo]: images/arduino_logo.png

![alt text][arduino_logo]

## Table of contents
- [Sequence 1](#sequence-1)
- [Sequence 2](#sequence-2)

## Sequence 1
```text

// initialization of the groups
int all_leds[]= {22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37};
int total_leds = 16;

int group_1_normal[] = {25, 28, 31, 34};
int group_1_inverted[] = {34, 31, 28, 25};

int group_2_normal[] = {22, 27, 32, 37};
int group_2_inverted[] = {37, 32, 27, 22};

int face_1[] = {22, 23, 24, 25};
int face_2[] = {29, 33};
int face_3[] = {34, 35, 36, 37};
int face_4[] = {26, 30};

// timer variables for loop control
int timer_each_led=70;
int timer_after_for=100;

void setup() {
  // runs once run once, after each powerup or reset of the Arduino board
  for(int i = 0; i < total_leds; i++){
    // configuring the pins defined in the led array as OUTPUT
    pinMode(all_leds[i], OUTPUT);
  }
}

void loop() {

  // cross code

  for(int i=0; i< 4; i++)
  {
    digitalWrite(group_1_normal[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(group_2_normal[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(group_1_inverted[i], LOW);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(group_2_inverted[i], LOW);
    delay(timer_each_led);
  }

  delay(timer_after_for);


  // face code

    for(int i=0; i< 4; i++)
  {
    digitalWrite(face_1[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(face_3[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(face_2[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(face_4[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

  // turn off all the leds

    for(int i=0; i< total_leds; i++)
  {
    digitalWrite(all_leds[i], LOW);
    // no delay is needed in order to turn off all the leds
  }

  // the last delay for the main loop
  delay(100);

}
```


## Sequence 2
```text

// initialization of the groups
int all_leds[]= {22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37};
int total_leds = 16;

int corners[] = {22, 25, 34, 37};

int center_1[] = {35, 31, 27, 23};
int center_2[] = {36, 32, 28, 24};
int group_center_1[] = {35, 31, 27, 23, 36, 32, 28, 24};

int center_3[] = {29, 28, 27, 26};
int center_4[] = {33, 32, 31, 30};
int group_center_2[] = {29, 28, 27, 26, 33, 32, 31, 30};


int center_5[] = {27, 28, 31, 32};

// timer variables for loop control
int timer_each_led=120;
int timer_after_for=120;

void setup() {
  // runs once run once, after each powerup or reset of the Arduino board
  for(int i = 0; i < total_leds; i++){
    // configuring the pins defined in the led array as OUTPUT
    pinMode(all_leds[i], OUTPUT);
  }
}

void loop() {

  // code for the corners
  for(int i=0; i< 4; i++)
  {
    digitalWrite(corners[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

  // code for the middle 1
    for(int i=0; i< 4; i++)
  {
    digitalWrite(center_1[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(center_2[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 8; i++)
  {
    digitalWrite(group_center_1[i], LOW);
    delay(timer_each_led);
  }

  // code for the middle 2

    for(int i=0; i< 4; i++)
  {
    digitalWrite(center_3[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(center_4[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 8; i++)
  {
    digitalWrite(group_center_2[i], LOW);
    delay(timer_each_led);
  }


  // code for the middle 3

    for(int i=0; i< 4; i++)
  {
    digitalWrite(center_5[i], HIGH);
    delay(timer_each_led);
  }

  delay(timer_after_for);

    for(int i=0; i< 4; i++)
  {
    digitalWrite(center_5[i], LOW);
    delay(timer_each_led);
  }

  delay(timer_after_for);


  // turn off for the corners
  for(int i=0; i< 4; i++)
  {
    digitalWrite(corners[i], LOW);
    delay(timer_each_led);
  }

  // the last delay for the main loop
  delay(1000);

}
```


## Combinaciones de Leds (Sistemas Digitales 3)
### Programa 1 (4 Combinaciones)
```text
/* Notes: ROTABIT
 *  0 == INPUT
 *  1 == OUTPUT
 */

// PORTS DECLARATIONS
byte PUERTO_10, PUERTO_11;

void setup() {
  Serial.begin(9600);
  // Declarar puertos
  DDRD=B11111100; // (PORTS from 1 to 7)
  DDRB=B111011; // (PORTS from 8 to 13) se declaran como OUTPUT 12 & 13 a pesar que no se vallan a usar (para proteccion)
}

void loop() {
  // put your main code here, to run repeatedly:
  PUERTO_10 = digitalRead(10); // PIN 10 (DIP SWITCH)
  PUERTO_11 = digitalRead(11); // PIN 11 (DIP SWITCH)


  // ==== PRIMERA COMBINACION ====
  if(PUERTO_10 == 0 && PUERTO_11 == 0){
    PORTD=B11111100; // se prenden los leds del 2-7
    PORTB=B110011; // se prenden los leds del 8-9
    delay(200);
  }


  // ==== SEGUNDA COMBINACION ====
  if(PUERTO_10 == 1 && PUERTO_11 == 1){ // (ROTABIT)
    PORTD=B00000000; // se apagan los leds del 2-7
    PORTB=B000000; // se apagan los leds del 8-9
    delay(200);

    for(byte i=2; i<10; i++){
      digitalWrite(i-1, LOW);
      digitalWrite(i, HIGH);
      digitalWrite(i+1, HIGH);
      delay(100);
    }

    for(byte i=10; i>=2; i--){
      digitalWrite(i+1, LOW);
      digitalWrite(i, HIGH);
      digitalWrite(i-1, HIGH);
      delay(100);
    }
  }


  // ==== TERCERA COMBINACION ====
  if(PUERTO_10 == 1 && PUERTO_11 == 0){
    PORTD=B00000000; // se apagan los leds del 2-7
    PORTB=B110000; // se apagan los leds del 8-9
    delay(200);

    for(byte port=2; port<10; port++){

      int a=0;

      for(byte i=1; i<=port; i++){
          if(port%i==0) // si num1 módulo de i es 0, incrementamos a en 1.
          a++;
      }

      if(a>2){
        digitalWrite(port, HIGH); // PRENDER NUMEROS COMPUESTOS
        delay(200);
      }

    }
  }

  // ==== CUARTA COMBINACION ====
  if(PUERTO_10 == 0 && PUERTO_11 == 1){ // dip switch prendido
    PORTD=B00000000; // se apagan los leds del 2-7
    PORTB=B000000; // se apagan los leds del 8-9
    delay(200);

    for(byte port=2; port<10; port++){

      int a=0;

      for(byte i=1;i<=port;i++){
          if(port%i==0) // si num1 módulo de i es 0, incrementamos a en 1.
          a++;
      }

      if(a==2){
        digitalWrite(port, HIGH); // PRENDER NUMEROS PRIMOS
        delay(200);
      }

    }
  }
}
```

### Programa 2 Palabras en display de 7 segmentos
```
text
/* Notes: ROTABIT
 *  0 == INPUT
 *  1 == OUTPUT
 */


void setup() {
  Serial.begin(9600);
  // Declarar puertos
  DDRD=B11111100; // (PORTS from 1 to 7)
  DDRB=B111111; // (PORTS from 8 to 13)
}

void loop() {
  // put your main code here, to run repeatedly:

    PORTD=B11011000;
    PORTB=B000001;
    delay(500); // Letra H

    PORTD=B11111100;
    PORTB=B000000;
    delay(500);   // Letra O  


    PORTD=B11100000;
    PORTB=B000000;
    delay(500);   // Letra L


    PORTD=B11011100;
    PORTB=B000001;
    delay(500);   // Letra A


    PORTD=B11110000;
    PORTB=B000001;
    delay(500);   // Letra B

    PORTD=B11100100;
    PORTB=B000001;
    delay(500);   // Letra E

    PORTD=B11110000;
    PORTB=B000001;
    delay(500);   // Letra B

    PORTD=B11100100;
    PORTB=B000001;
    delay(500);   // Letra E

    PORTD=B00000000;
    PORTB=B0000010;
    delay(1000);   // Se apaga el display
}
```

### Programa 3 Juego de Pin Pong
```
text

/* Notes: ROTABIT
 *  0 == INPUT
 *  1 == OUTPUT
 */

const int buttonPin = 10;     // the number of the pushbutton pin
const int ledPin =  3;      // the number of the LED pin
const int rotabitSpeed = 100;
const int letterSpeed = 500;

int buttonState = 0;         // variable for reading the pushbutton status
int strikes = 0;

void setup() {
  Serial.begin(9600);
  // Declarar puertos
  DDRD=B11111100; // (PORTS from 1 to 7)
  DDRB=B111011; // (PORTS from 8 to 13) se declaran como OUTPUT 12 & 13 a pesar que no se vallan a usar (para proteccion) | puerto 11 es G en display
  DDRC=B111111; // (ANALOGIC PORTS from A0 to A5) == USED FOR DISPLAY == | A0 = A on display an so on |
}


void setNumberInDisplay(int number){
  switch (number) {
    case 1:
      PORTC=B000110;
      digitalWrite(11, LOW);
      break;
    case 2:
      PORTC=B011011;
      digitalWrite(11, HIGH);
      break;
    case 3:
      PORTC=B001111;
      digitalWrite(11, HIGH);
      break;
    case 4:
      PORTC=B100110;
      digitalWrite(11, HIGH);
      break;
    case 5:
      PORTC=B101101;
      digitalWrite(11, HIGH);
      break;
    case 6:
      PORTC=B111101;
      digitalWrite(11, HIGH);
      break;      
    case 7:
      PORTC=B000111;
      digitalWrite(11, HIGH);
      break;
    case 8:
      PORTC=B111111;
      digitalWrite(11, HIGH);
      break;
    case 9:
      PORTC=B100111;
      digitalWrite(11, HIGH);
      break;
  }
}


void setMessage(){
  // Shows a message in the display when the user lost the game

  PORTC=B111000;
  digitalWrite(11, LOW); // Letra L
  delay(letterSpeed);

  PORTC=B111111;
  digitalWrite(11, LOW); // Letra O
  delay(letterSpeed);

  PORTC=B111111;
  digitalWrite(11, LOW); // Letra O
  delay(letterSpeed);

  PORTC=B101101;
  digitalWrite(11, HIGH); // Letra S
  delay(letterSpeed);


  PORTC=B111001;
  digitalWrite(11, HIGH); // Letra E
  delay(letterSpeed);

  PORTC=B110111;
  digitalWrite(11, HIGH); // Letra R (que seria una A mas bien)
  delay(letterSpeed);
}

void turnOffDisplay(){
    // Apago el display
    PORTC=B000000;
    digitalWrite(11, LOW);
}

void turnOffLeds(){
    PORTD=B00000000; // Se apagan los leds del 0-7
    digitalWrite(8, LOW);
    digitalWrite(9, LOW);
}

void checkStrikes(int strikes){
  if(strikes >= 9){
    turnOffLeds();
    delay(1000); // delay after number 9
    turnOffDisplay();
    delay(1000);
    setMessage();
    delay(2000);
    turnOffDisplay();
    exit(0);
  }
}

void verifyStrike(byte iteration, byte pin){
    // read the state constantly on every iteration of the pushbutton value
    buttonState = digitalRead(buttonPin);

    if(iteration == pin){ // Checar el ultimo led encendido
      if (buttonState == LOW) { // Si el push button NO es presionado
        strikes++;
        setNumberInDisplay(strikes);
      }
    }
}

void loop() {

  // ==== PIN PONG ====

    //int strikes = 0;

    for(byte iteration=0; iteration<=9; iteration++){ // Main loop

      for(byte i=2; i<=9; i++){ // ROTABIT DE DERECHA A IZQUIERDA

        // Instrucciones para prender los leds
        digitalWrite(i-1, LOW);
        digitalWrite(i, HIGH);
        digitalWrite(i+1, HIGH);

        verifyStrike(i, 9); // 9 es el ultimo pin de izquierda a derecha    
        delay(rotabitSpeed);
      }

      checkStrikes(strikes); // Verifica que aun se tenga oportunidades

      for(byte i=9; i>=2; i--){ // ROTABIT DE IZQUIERDA A DERECHA
        // Instrucciones para prender los leds
        digitalWrite(i+1, LOW);
        digitalWrite(i, HIGH);
        digitalWrite(i-1, HIGH);

        verifyStrike(i, 2); // 2 es el primer pin de derecha a izquierda
        delay(rotabitSpeed);
      }

      checkStrikes(strikes); // Verifica que aun se tenga oportunidades

    }

    checkStrikes(strikes); // Verifica que aun se tenga oportunidades

}
```
- Author: `Humberto Israel Perez Rodriguez`
