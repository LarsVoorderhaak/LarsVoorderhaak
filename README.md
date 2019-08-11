# LarsVoorderhaak


/*  
 *   Thank you for loading this code.
 *   This program shown how to control a H-brige L9110s with bluetooth control.
 *   The code i wrote is driving a lego stepper motor, you can use 1 stepper or 2 dc motors with this code. 
 *   The code includes even 2 led's to switch on and off.
 *   Telephone>>bluetooth,hc-05>>Arduino>>H-bridge,L9110s.
 *   Download and instal the Serial Bleuthooth Terminal app (google play).
 *   If you have instaled it then make a conection with your bluetooth divice.
 *   Give the Buttons in your app a name like in the code, give it also the value thas corrospent with the value in the code. 
 *   You can change the Digital outputs on your Arduino.
 *   
 *   © LARS VOORDERHAAK / DJQUICKLAND1982@GMAIL.COM
 */


#include <SoftwareSerial.h> // IMPORT LIBARY

SoftwareSerial Genotronex(8, 9); // TX IN RX AND RX IN TX OF YOUR ARDUINO !!!!!DISCONECT YOUR DIVICE IF YOU UPLOAD YOUR SKETCH!!!!!

int MO1A = 2;    // DC MOTOR 1.FORWARD........STEPPER CLOCKWISE
int MO1B = 3;    // DC MOTOR 1.BACKWARDS......STEPPER ANTI CLOCKWISE
int MO2A = 4;    // DC MOTOR 2.FORWARD........STEPPER CLOCKWISE
int MO2B = 5;    // DC MOTOR 2.BACKWARDS......STEPPER ANTI CLOCKWISE
int LEDF = 6;    // FRONT LIGHTS
int LEDB = 7;    // BACK LIGHTS
int LEDL1 = 8;   // TURN SIGNAL LED 1 LEFT     AUDI EFFECT
int LEDL2 = 9;   // TURN SIGNAL LED 2 LEFT
int LEDL3 = 10;  // TURN SIGNAL LED 3 LEFT
int LEDR1 = 11;  // TURN SIGNAL LED 1 RIGHT
int LEDR2 = 12;  // TURN SIGNAL LED 2 RIGHT
int LEDR3 = 13;  // TURN SIGNAL LED 3 RIGHT

int BluetoothData; // DATA FROM YOUR APP.


void setup() {     // GENERAL SKETCH SETUP
  Genotronex.println("WELCOME");
  Genotronex.begin(9600);
  

  pinMode(MO1A, OUTPUT);
  pinMode(MO1B, OUTPUT);
  pinMode(MO2A, OUTPUT);
  pinMode(MO2B, OUTPUT);
  pinMode(LEDF, OUTPUT);
  pinMode(LEDB, OUTPUT);
  pinMode(LEDL1, OUTPUT);
  pinMode(LEDL2, OUTPUT);
  pinMode(LEDL3, OUTPUT);
  pinMode(LEDR1, OUTPUT);
  pinMode(LEDR2, OUTPUT);
  pinMode(LEDR3, OUTPUT);
  
  }

void loop() {

 if (Genotronex.available()) {
    BluetoothData = Genotronex.read();
    if (BluetoothData == '0') { // 0 IS THE VALUE,  IF 0 IS SEND FROM APP TO YOUR DIVICE IT DRIVES THE STEPPER CLOCKWISE/ANTICLOCKWISE.
      digitalWrite(MO1B, 1);
      digitalWrite(MO2B, 1);
      Genotronex.println("FORWARDS");
    }

    if (BluetoothData == '1') { //1 IS THE VALUE
      digitalWrite(MO1B, 0);
      digitalWrite(MO2B, 0);
      Genotronex.println("STOP!");
    }

    if (BluetoothData == '2') { //2 IS THE VALUE
      digitalWrite(MO1A, 1);
      digitalWrite(MO2A, 1);
      Genotronex.println("BACKWARDS!");
    }

    if (BluetoothData == '1') { //3 IS THE VALUE
      digitalWrite(MO1A, 0);
      digitalWrite(MO2A, 0);
      // PRINTIN STOP VALUE 1
    }

    if (BluetoothData == '4') { //4 IS THE VALUE
      digitalWrite(LEDF, 1);
      Genotronex.println("LIGHTS FRONT ON");
    }

    if (BluetoothData == '5') { //5 IS THE VALUE
      digitalWrite(LEDF, 0);
      Genotronex.println("LIGHTS FRONT OFF");
    }

    if (BluetoothData == '6') { //6 IS THE VALUE
      digitalWrite(LEDB, 1);
      Genotronex.println("LIGHTS BACK ON");
    }

    if (BluetoothData == '7') { //7 IS THE VALUE
      digitalWrite(LEDB, 0);
      Genotronex.println("LIGHTS BACK OFF");
    }
    
    if (BluetoothData == '8') { //8 IS THE VALUE
      digitalWrite(LEDF, 1);
      digitalWrite(LEDB, 1);
      Genotronex.println("LIGHTS FRONT & BACK ON");
    }
    if (BluetoothData == '9') { //9 IS THE VALUE
      digitalWrite(LEDF, 0);
      digitalWrite(LEDB, 0);
      Genotronex.println("LIGHTS FRONT & BACK OFF");
    }

      if (BluetoothData == 'L') { //L IS THE VALUE
      Genotronex.println("TURNSIGNAL LEFT");
      digitalWrite(LEDL3, 1);
      delay(100);
      digitalWrite(LEDL2, 1);
      delay(100);
      digitalWrite(LEDL1, 1);
      delay(200);
      digitalWrite(LEDL3, 0);
      delay(100);
      digitalWrite(LEDL2, 0);
      delay(100);
      digitalWrite(LEDL1, 0);
      delay(200);
      digitalWrite(LEDL3, 1);
      delay(100);
      digitalWrite(LEDL2, 1);
      delay(100);
      digitalWrite(LEDL1, 1);
      delay(200);
      digitalWrite(LEDL3, 0);
      delay(100);
      digitalWrite(LEDL2, 0);
      delay(100);
      digitalWrite(LEDL1, 0);
      delay(200);
      digitalWrite(LEDL3, 1);
      delay(100);
      digitalWrite(LEDL2, 1);
      delay(100);
      digitalWrite(LEDL1, 1);
      delay(200);
      digitalWrite(LEDL3, 0);
      delay(100);
      digitalWrite(LEDL2, 0);
      delay(100);
      digitalWrite(LEDL1, 0);
      
    }
    
  if (BluetoothData == 'R') { //R IS THE VALUE
      Genotronex.println("TURNSIGNAL RIGHT");
      digitalWrite(LEDR1, 1);
      delay(100);
      digitalWrite(LEDR2, 1);
      delay(100);
      digitalWrite(LEDR3, 1);
      delay(200);
      digitalWrite(LEDR1, 0);
      delay(100);
      digitalWrite(LEDR2, 0);
      delay(100);
      digitalWrite(LEDR3, 0);
      delay(200);
      digitalWrite(LEDR1, 1);
      delay(100);
      digitalWrite(LEDR2, 1);
      delay(100);
      digitalWrite(LEDR3, 1);
      delay(200);
      digitalWrite(LEDR1, 0);
      delay(100);
      digitalWrite(LEDR2, 0);
      delay(100);
      digitalWrite(LEDR3, 0);
      delay(200);
      digitalWrite(LEDR1, 1);
      delay(100);
      digitalWrite(LEDR2, 1);
      delay(100);
      digitalWrite(LEDR3, 1);
      delay(200);
      digitalWrite(LEDR1, 0);
      delay(100);
      digitalWrite(LEDR2, 0);
      delay(100);
      digitalWrite(LEDR3, 0);
      
    }

    if (BluetoothData == '3') { //R IS THE VALUE
      Genotronex.println("HAZZARD LIGHTS");
      
      digitalWrite(LEDL3, 1);
      digitalWrite(LEDR1, 1);
      delay(200);
      digitalWrite(LEDL2, 1);
      digitalWrite(LEDR2, 1);
      delay(100);
      digitalWrite(LEDL1, 1);
      digitalWrite(LEDR3, 1);
      delay(200);
      digitalWrite(LEDL3, 0);
      digitalWrite(LEDR1, 0);
      delay(100);
      digitalWrite(LEDL2, 0);
      digitalWrite(LEDR2, 0);
      delay(100);
      digitalWrite(LEDL1, 0);
      digitalWrite(LEDR3, 0);
      delay(200);
      digitalWrite(LEDL3, 1);
      digitalWrite(LEDR1, 1);
      delay(100);
      digitalWrite(LEDL2, 1);
      digitalWrite(LEDR2, 1);
      delay(100);
      digitalWrite(LEDL1, 1);
      digitalWrite(LEDR3, 1);
      delay(200);
      digitalWrite(LEDL3, 0);
      digitalWrite(LEDR1, 0);
      delay(100);
      digitalWrite(LEDL2, 0);
      digitalWrite(LEDR2, 0);
      delay(100);
      digitalWrite(LEDL1, 0);
      digitalWrite(LEDR3, 0);
      delay(200);
      digitalWrite(LEDL3, 1);
      digitalWrite(LEDR1, 1);
      delay(100);
      digitalWrite(LEDL2, 1);
      digitalWrite(LEDR2, 1);
      delay(100);
      digitalWrite(LEDL1, 1);
      digitalWrite(LEDR3, 1);
      delay(200);
      digitalWrite(LEDL3, 0);
      digitalWrite(LEDR1, 0);
      delay(100);
      digitalWrite(LEDL2, 0);
      digitalWrite(LEDR2, 0);
      delay(100);
      digitalWrite(LEDL1, 0);
      digitalWrite(LEDR3, 0);
      delay(200);
  }
  delay(100);// prepare for next data ...
 }}
