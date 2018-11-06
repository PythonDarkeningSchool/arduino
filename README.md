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

- Author: `Humberto Israel Perez Rodriguez`