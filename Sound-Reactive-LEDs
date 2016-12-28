/*
 * This file randomly generates RGB values that change the color of an LED strip 
 * with the beat of a song using a sound sensor and an Arduino  
 */

#include <stdlib.h>

#define rPIN 11 //pin location of red LED
#define gPIN 10 //pin location of green LED
#define bPIN 9 //pin location of blue LED
#define SIS 7 //pin location of sound impact sensor

int rLED;
int gLED;
int bLED;

void setup() {
  pinMode(SIS, INPUT);
  pinMode(rLED, OUTPUT);
  pinMode(gLED, OUTPUT);
  pinMode(bLED, OUTPUT);
}

void loop() {
  boolean soundState = digitalRead(SIS); //reads signal from SIS
  
  if (soundState == 1) { //if SIS sends 1 signal
    rLED = rand_lim(255);
    gLED = rand_lim(255);
    bLED = rand_lim(255);
    
    analogWrite(rPIN, rLED);
    analogWrite(gPIN, gLED);
    analogWrite(bPIN, bLED);
    
    delay(1); //waits 1 ms before 
  } else { //if SIS sends 0 signal all LEDS are turned off
      analogWrite(rPIN, 0);
      analogWrite(gPIN, 0);
      analogWrite(bPIN, 0);
    }
}

int rand_lim(int limit) { //return a random number between 0 and limit inclusive
  int divisor = RAND_MAX / (limit + 1); //RAND_MAX == 2147483647 (largest signed integer in 32 bits)
  int retval;

  do {
    retval = rand() / divisor;
  } while (retval > limit);

  return retval;
}
