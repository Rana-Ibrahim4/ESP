# ESP
## Design and program an electronic circuit that contains an ESP with any sensor and explain the function of the circuit
### Arduino/ESP32 
### To detect movement using a sensor PIR (passive infrared Sensor) and turn on the LED as a signal to detect this movement 
ex Git :
```
int led =13;            // led is connected to esp32 D13
 int pirdata =15 ;       // pir D is connected to D15
 int pirstate =LOW ;      // assuming no motion 
 int value =0;            // to read pin status 

void setup() {
  pinMode(led, OUTPUT);      //  Led as output
  pinMode(pirdata, INPUT);     // PIR sensor as input

  Serial.begin(9600);
}

void loop() {
  value = digitalRead(pirdata);  
  if (value == HIGH) {           
    digitalWrite(led, HIGH);  
    if (pirstate == LOW) {
     
      Serial.println("Motion detected!");
      
      pirstate = HIGH;
    }
  } else {
    digitalWrite(led, LOW); 
    if (pirstate == HIGH) {
      
      Serial.println("Motion ended!");
     
      pirstate = LOW;
    }
  }
}
```
### Explanation :
1. int led = 13;: Assigns the variable led to connect the LED to pin 13 on the ESP32 board.
2. int pirdata = 15;: Assigns the variable pirdata to connect the PIR sensor to pin 15 on the ESP32 board.
3. int pirstate = LOW;: Initializes the pirstate variable to LOW, assuming no motion is detected initially.
4. int value = 0;: Assigns the variable value to store the input status from the PIR sensor.


### In the setup() function:
1. pinMode(led, OUTPUT);: Sets the LED as an output.
2. pinMode(pirdata, INPUT);: Sets the PIR sensor as an input.
3. Serial.begin(9600);: Starts the serial communication at a baud rate of 9600.

### In the loop() function:
1. value = digitalRead(pirdata);: Reads the value of the PIR sensor and stores it in the value variable.
2. if (value == HIGH): If motion is detected (the value is `HIGH`):
   - digitalWrite(led, HIGH);: Turns the LED on.
   - if (pirstate == LOW): If no motion was detected before:
     - Serial.println("Motion detected!");: Prints a message to the serial port.
     - pirstate = HIGH;: Updates the pirstate to HIGH to indicate that motion has been detected.
3. else: If no motion is detected (the value is `LOW`):
   - digitalWrite(led, LOW);: Turns the LED off.
   - if (pirstate == HIGH): If motion was detected before:
     - Serial.println("Motion ended!");: Prints a message to the serial port.
     - pirstate = LOW;: Updates the pirstate to LOW to indicate that no motion is detected.
    
    ### IMG in the wokwi




![لقطة شاشة 2024-07-12 051047](https://github.com/user-attachments/assets/b7f0e613-cbf4-416b-8836-10c6a5c24fd1)

