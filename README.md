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

### Programa 2 (ABECEDARIO en display de 7 segmentos)
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

    PORTD=B11011100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra A

    PORTD=B11110000;
    digitalWrite(8, HIGH);
    delay(500);   // Letra B

    PORTD=B11100100;
    digitalWrite(8, LOW);
    delay(500);   // Letra C

    PORTD=B01111000;
    digitalWrite(8, HIGH);
    delay(500);   // Letra D

    PORTD=B11100100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra E

    PORTD=B11000100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra F

    PORTD=B11110100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra G

    PORTD=B11011000;
    digitalWrite(8, HIGH);
    delay(500);   // Letra H

    PORTD=B00011000;
    digitalWrite(8, LOW);
    delay(500);   // Letra I

    PORTD=B00111000;
    digitalWrite(8, LOW);
    delay(500);   // Letra J

    PORTD=B11100000;
    digitalWrite(8, LOW);
    delay(500);   // Letra L

    PORTD=B01010000;
    digitalWrite(8, HIGH);
    delay(500);   // Letra N

    PORTD=B01010100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra Ñ

    PORTD=B11111100;
    digitalWrite(8, LOW);
    delay(500);   // Letra O

    PORTD=B11001100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra P

    PORTD=B10011100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra Q

    PORTD=B01000000;
    digitalWrite(8, HIGH);
    delay(500);   // Letra R

    PORTD=B10110100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra S

    PORTD=B11000000;
    digitalWrite(8, HIGH);
    delay(500);   // Letra T

    PORTD=B11111000;
    digitalWrite(8, LOW);
    delay(500);   // Letra U

    PORTD=B01101100;
    digitalWrite(8, HIGH);
    delay(500);   // Letra Z

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

### Programa 4 Led RGB
```
/* LED RGB
 *
 * 1 fase: el led tiene que apagarse para cambiar de color
 * 2 fase: el led no se tiene que apagar para cambiar de color
 *
 * Notas:
 * 1. Cada pin tiene 8 bits y en hexadecimal son 256
 * 2. Los colores son: rojo / verde / azul / amarillo / morado / azul cielo / blanco
 * 3. Las combinaciones de colores son:
 *  3.1 Amarillo = rojo + verde
 *  3.2 Morado = rojo + azul
 *  3.3 Azul cielo = azul + verde
 *  3.4 Blanco = todos
 * 4. 0 == INPUT
 * 5. 1 == OUTPUT
*/

// SWITCH PORTS DECLARATION
byte SWITCH_PUERTO_8;

byte RED_PIN=9;
byte GREEN_PIN=10;
byte BLUE_PIN=11;

void setup() {
  Serial.begin(9600);
  // PORTS 9,10 & 11 as OUTPUTS for RGB, PORT 8 for the switch as INPUT
  DDRD=B001110;
  //RGB_color(0, 0, 0); // start with the led in off state
}

void loop() {

  SWITCH_PUERTO_8 = digitalRead(8); // PIN 8 TO DIP SWITCH

  Serial.print("SWITCH_PUERTO_8: " + SWITCH_PUERTO_8);

  if(SWITCH_PUERTO_8 == HIGH) {
    Serial.print("HIGH\n");

    int smoothDelay = 10;
    RGB_color(0, 255, 255); // Red

    for(int x=255; x>=0; x--){ // decrement
      RGB_color(0, x, 255); // Yellow  
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++){ // increment
      RGB_color(x, 0, 255); // Green
      delay(smoothDelay);
    }

    for(int x=255; x>=0; x--){ // decrement
      RGB_color(255, 0, x); // Cyan  
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++){ // increment
      RGB_color(255, x, 0); // Blue
      delay(smoothDelay);
    }

    for(int x=255; x>=0; x--){ // decrement
      RGB_color(x, 255, 0); // Magenta  
      delay(smoothDelay);
    }


  }
  else {

    int smoothDelay = 10;

    // RED
    for(int x=255; x>=0;x--){
      analogWrite(RED_PIN,x);
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++) {
      analogWrite(RED_PIN,x);
      delay(smoothDelay);
    }

    // GREEN
    for(int x=255; x>=0;x--){
      analogWrite(GREEN_PIN,x);
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++) {
      analogWrite(GREEN_PIN,x);
      delay(smoothDelay);
    }

    // BLUE
    for(int x=255; x>=0;x--){
      analogWrite(BLUE_PIN,x);       
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++) {
      analogWrite(BLUE_PIN,x);
      delay(smoothDelay);
    }

    // YELLOW(RED & GREEN)
    for(int x=255; x>=0;x--){
      analogWrite(RED_PIN,x);
      analogWrite(GREEN_PIN,x);
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++) {
      analogWrite(RED_PIN,x);
      analogWrite(GREEN_PIN,x);
      delay(smoothDelay);
    }

    // MAGENTA (RED & BLUE)
    for(int x=255; x>=0;x--){
      analogWrite(RED_PIN,x);
      analogWrite(BLUE_PIN,x);   
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++) {
      analogWrite(RED_PIN,x);
      analogWrite(BLUE_PIN,x);
      delay(smoothDelay);
    }

    // WHITE (RED, BLUE & GREEN)
    for(int x=255; x>=0;x--){
      analogWrite(GREEN_PIN,x);
      analogWrite(RED_PIN,x);
      analogWrite(BLUE_PIN,x);   
      delay(smoothDelay);
    }

    for(int x=0; x<=255; x++) {
      analogWrite(GREEN_PIN,x);
      analogWrite(RED_PIN,x);  
      analogWrite(BLUE_PIN,x);
      delay(smoothDelay);
   }

  }

  delay(1000);

}



void RGB_color(int red_light_value, int green_light_value, int blue_light_value)
 {
  analogWrite(RED_PIN, red_light_value);
  analogWrite(GREEN_PIN, green_light_value);
  analogWrite(BLUE_PIN, blue_light_value);
}
```

### Programa 5 Sistema De Climatizacion con LM35
```
/* Sistema De Climatizacion con LM35

Variables:
1. dos variables tipo float
  1.1 - la primera para medir el sensor de temperatura (puerto A0 del arduino)
  1.2 - la segunda para calcular la formula de la temperatura en grados celcious


Valores de la Temperatura:

Azul: temperatura normal
Verde: aumento de temperatura
Rojo: temperatura alta

Cuando la temperatura incrementa
- 29 grados = led RGB en azul
- de 30 a 34 grados = led RGB en verde
- 35 grados = led RGB en rojo

Cuando la temperatura decrementa
- de 35 a 29 grados = se pasa de rojo a azul

 *  0 == INPUT
 *  1 == OUTPUT

*/

byte RED_PIN=9;
byte GREEN_PIN=10;
byte BLUE_PIN=11;
float SENSOR, TEMPERATURA;
int smoothDelay = 3;
int redFlag = 0;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  //pinMode(A0, INPUT);
  //DDRC=B000000;

}

void turnOffRGB(int color){
  switch(color){
    case 1: // RED
      // RGB de Anodo Comun se apaga con 1 = 255
      Serial.print("\nturnOffRGB RED\n");
      analogWrite(RED_PIN, 255);
      break;
     case 2: // GREEN
      Serial.print("\nturnOffRGB GREEN\n");
      analogWrite(GREEN_PIN, 255);
      break;
     case 3: // BLUE
      Serial.print("\nturnOffRGB BLUE\n");
      analogWrite(BLUE_PIN, 255);
      break;
  }
}

void setRBGColor(int color){
  switch(color){
    case 1: // RED
      // RGB de Anodo Comun se prende con 1 = 255
      Serial.print("\nsetRBGColor RED\n");
      // Se necesitan mandar los 3 para un solo pin
      analogWrite(RED_PIN, 255);
      analogWrite(RED_PIN, 0);
      analogWrite(RED_PIN, 0);
      break;
     case 2: // GREEN
      Serial.print("\nsetRBGColor GREEN\n");
      // Se necesitan mandar los 3 para un solo pin
      analogWrite(GREEN_PIN, 255);
      analogWrite(GREEN_PIN, 0);
      analogWrite(GREEN_PIN, 0);
      break;
     case 3: // BLUE
      Serial.print("\nsetRBGColor BLUE\n");
      // Se necesitan mandar los 3 para un solo pin
      analogWrite(BLUE_PIN, 255);
      analogWrite(BLUE_PIN, 0);
      analogWrite(BLUE_PIN, 0);
      break;
  }
}

void loop() {
  // put your main code here, to run repeatedly
  TEMPERATURA = analogRead(A0); // value from 0 a 1023
  TEMPERATURA = (5.0 * TEMPERATURA * 100.0)/1024.0; // Se calcula la temperatura
  Serial.print(TEMPERATURA);
  Serial.print("\n");


  if(TEMPERATURA < 30){
    Serial.print("condition 1: \n");
    redFlag = false;
    Serial.print(TEMPERATURA);
    turnOffRGB(1); // TURN OFF RED
    delay(500);
    turnOffRGB(2); // TURN OFF GREEN
    delay(500);
    setRBGColor(3); // TURN ON BLUE
    delay(500);
  }
  //if(redFlag == 0 && TEMPERATURA > 30 && TEMPERATURA < 32){
  if(redFlag == 0 && TEMPERATURA >= 30 && TEMPERATURA <=34){
    Serial.print("==============>>>>>>>>>>redFlag: ");
    Serial.print(redFlag);
    Serial.print("condition 2: \n");
    Serial.print(TEMPERATURA);
    turnOffRGB(1); // TURN OFF RED
    delay(500);    
    turnOffRGB(3); // TURN OFF BLUE
    delay(500);
    setRBGColor(2); // TURN ON GREEN
    delay(500);
  }
  //if(TEMPERATURA >=32){
  if(TEMPERATURA > 35){
    Serial.print("condition 3: \n");
    redFlag = 1;
    Serial.print(TEMPERATURA);
    turnOffRGB(2); // TURN OFF GREEN
    delay(500);
    turnOffRGB(3); // TURN OFF BLUE
    delay(500);
    setRBGColor(1); // TURN ON RED
    delay(500);
  }



}
```

### Programa 6 Arduino + RGB + Bluetooth
```

char Incoming_value = 0;
byte RED_PIN=9;
byte GREEN_PIN=10;
byte BLUE_PIN=11;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(13, OUTPUT);

}

void turnOffRGB(int color){
  switch(color){
    case 1: // RED
      // RGB de Anodo Comun se apaga con 1 = 255
      analogWrite(RED_PIN, 255);
      break;
     case 2: // GREEN
      analogWrite(GREEN_PIN, 255);
      break;
     case 3: // BLUE
      analogWrite(BLUE_PIN, 255);
      break;
  }
}

void setRBGColor(int color){
  switch(color){
    case 1: // RED
      // RGB de Anodo Comun se prende con 1 = 255
      // Se necesitan mandar los 3 para un solo pin
      analogWrite(RED_PIN, 255);
      analogWrite(RED_PIN, 0);
      analogWrite(RED_PIN, 0);
      break;
     case 2: // GREEN
      // Se necesitan mandar los 3 para un solo pin
      analogWrite(GREEN_PIN, 255);
      analogWrite(GREEN_PIN, 0);
      analogWrite(GREEN_PIN, 0);
      break;
     case 3: // BLUE
      // Se necesitan mandar los 3 para un solo pin
      analogWrite(BLUE_PIN, 255);
      analogWrite(BLUE_PIN, 0);
      analogWrite(BLUE_PIN, 0);
      break;
  }
}

void loop() {
  // put your main code here, to run repeatedly:

  if(Serial.available() > 0)  
  {
    Incoming_value = Serial.read();      //Read the incoming data and store it into variable Incoming_value
    Serial.print(Incoming_value);        //Print Value of Incoming_value in Serial monitor
    Serial.print("\n");        //New line
    if(Incoming_value == '1')            //Checks whether value of Incoming_value is equal to 1
      digitalWrite(13, HIGH);  //If value is 1 then LED turns ON
    else if(Incoming_value == '0')       //Checks whether value of Incoming_value is equal to 0
      digitalWrite(13, LOW);   //If value is 0 then LED turns OFF

    switch(Incoming_value){
      case 'r':
        // red
        turnOffRGB(3); // TURN OFF BLUE
        turnOffRGB(2); // TURN OFF GREEN
        turnOffRGB(1); // TURN OFF RED **
        setRBGColor(1); // TURN ON GREEN
      break;
      case 'g':
        // green
        turnOffRGB(1); // TURN OFF RED
        turnOffRGB(2); // TURN OFF GREEN **
        turnOffRGB(3); // TURN OFF BLUE
        setRBGColor(2); // TURN ON GREEN
      break;
      case 'b':
        // blue
        turnOffRGB(1); // TURN OFF RED
        turnOffRGB(2); // TURN OFF GREEN
        turnOffRGB(3); // TURN OFF GREEN **
        setRBGColor(3); // TURN ON BLUE
      break;
      case 'y':
        // yellow
        turnOffRGB(1); // TURN OFF RED
        turnOffRGB(2); // TURN OFF GREEN
        turnOffRGB(3); // TURN OFF GREEN **
        setRBGColor(1); // TURN ON RED
        setRBGColor(2); // TURN ON GREEN
      break;
      case 'p':
        // purple
        turnOffRGB(1); // TURN OFF RED
        turnOffRGB(2); // TURN OFF GREEN
        turnOffRGB(3); // TURN OFF GREEN **
        setRBGColor(1); // TURN ON RED
        setRBGColor(3); // TURN ON BLUE
      break;
      case 'c':
        // cyan
        turnOffRGB(1); // TURN OFF RED
        turnOffRGB(2); // TURN OFF GREEN
        turnOffRGB(3); // TURN OFF GREEN **
        setRBGColor(2); // TURN ON GREEN
        setRBGColor(3); // TURN ON BLUE
      break;
      case 'w':
        // white
        turnOffRGB(1); // TURN OFF RED
        turnOffRGB(2); // TURN OFF GREEN
        turnOffRGB(3); // TURN OFF GREEN **
        setRBGColor(1); // TURN ON RED
        setRBGColor(2); // TURN ON GREEN
        setRBGColor(3); // TURN ON BLUE

      break;
      case 'n':
        // turn off
        turnOffRGB(1); // TURN OFF RED
        turnOffRGB(2); // TURN OFF GREEN
        turnOffRGB(3); // TURN OFF GREEN **
      break;
    }
  }



}
```

- Author: `Humberto Israel Perez Rodriguez`
