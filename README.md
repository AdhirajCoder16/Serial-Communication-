 Arduino UNO Serial Communication: Control LED via Serial Monitor

This project demonstrates how to **send and receive data via the serial port** on an Arduino UNO. You can toggle an LED based on commands sent from the Serial Monitor and receive feedback from the Arduino.

---

## 🧠 Overview

Using the Arduino UNO, this project:
- Receives serial data from the computer (via USB).
- Turns an LED **ON or OFF** depending on the received command.
- Sends back the LED status to the Serial Monitor.



## 🧩 Components Required

| Quantity | Component         |
|----------|-------------------|
| 1        | Arduino UNO       |
| 1        | USB Cable         |
| 1        | LED               |
| 1        | 220Ω Resistor     |
| 1        | Breadboard        |
| Several  | Jumper Wires      |


 Working Principle

 1. **Serial Ports**

- The Arduino UNO communicates via USB using **Serial communication** (UART on Pins 0/RX and 1/TX).
- You interact through the **Serial Monitor** in the Arduino IDE at a defined **baud rate (e.g., 9600)**.
- **Important:** Do not use pins 0 and 1 for other I/O while using Serial.

 2. **Key Functions**

#### `Serial.begin(baudRate)`
Sets the data rate in bits per second for serial data transmission.

#### `Serial.read()`
Reads the first byte of incoming serial data. Returns `-1` if no data is available.

#### `Serial.print(val)`
Sends data to the serial port. It prints the data as ASCII characters.

#### `Serial.println(val)`
Similar to `print()` but appends a carriage return and newline (`\r\n`).

Code-
int ledpin=11;           //definition digital 11 pins as pin to control the LED

void setup()
{
  Serial.begin(9600);   // opens serial port, sets data rate to 9600 bps
  pinMode(ledpin,OUTPUT);//Set digital 11 port mode, the OUTPUT for the output
}
void loop()
{
    char receiveVal;                  // Defined receive data
   
    if(Serial.available() > 0)       //Receive serial data
    {        
        receiveVal = Serial.read();  //Save the serial data received 
        
       if(receiveVal == '1')          //Receive data is 1, lit LED lights    
       { 
           digitalWrite(ledpin,HIGH); //print out the value of the LED       
           Serial.println("LED:ON"); //send data to the serial monitor
       }
       if(receiveVal == '0')          //Receive data is 0, off LED lights
       { 
           digitalWrite(ledpin,LOW);  //print out the value of the LED                
           Serial.println("LED:OFF");//send data to the serial monitor
      } 
    }
  delay(50);                          //delay 50ms
}




