#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <Servo.h>

LiquidCrystal_I2C lcd(0x27, 16, 2); // LCD I2C Address 0x27
Servo myservo;


const int IR_Entry = 6;       // Entry IR sensor
const int IR_Exit = 5;        // Exit IR sensor
const int Slot1 = 10;         // IR sensor for Slot 1
const int Slot2 = 9;          // IR sensor for Slot 2
const int Slot3 = 11;         // IR sensor for Slot 3
const int Slot4 = 7;          // IR sensor for Slot 4


const int ServoPin = 4;       // Servo connected to pin 8

// Define servo angles
const int gateOpenAngle = 180;  // Gate open angle
const int gateCloseAngle = 90; // Gate close angle

// Variables
int totalSlots = 4;           // Total number of parking slots
int occupiedSlots = 0;        // Number of occupied slots
bool entryTriggered = false;  // Flag for entry gate
bool exitTriggered = false;   // Flag for exit gate

void setup() {
  Serial.begin(9600);

 
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("SMART PARKING");
  lcd.setCursor(0, 1);
  lcd.print("SYSTEM INIT...");
  delay(2000);
  lcd.clear();

  
  pinMode(IR_Entry, INPUT);
  pinMode(IR_Exit, INPUT);
  pinMode(Slot1, INPUT);
  pinMode(Slot2, INPUT);
  pinMode(Slot3, INPUT);
  pinMode(Slot4, INPUT);
  
  myservo.attach(ServoPin); 
  myservo.write(gateCloseAngle); 
}

void loop() {
 
  delay(100);

  // Check parking slot sensors
  int slot1State = digitalRead(Slot1);
  int slot2State = digitalRead(Slot2);
  int slot3State = digitalRead(Slot3);
  int slot4State = digitalRead(Slot4);

  
  occupiedSlots = 0;
  if (slot1State == LOW) occupiedSlots++;
  if (slot2State == LOW) occupiedSlots++;
  if (slot3State == LOW) occupiedSlots++;
  if (slot4State == LOW) occupiedSlots++;

  
  if (digitalRead(IR_Entry) == LOW && !entryTriggered && (totalSlots - occupiedSlots) > 0) {
    entryTriggered = true;
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Car Entering...");

    
    delay(2000);

  
    openGate();
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Car Entered!");
    delay(2000); 
    lcd.clear();
  }

  // Exit gate 
  if (digitalRead(IR_Exit) == LOW && !exitTriggered && occupiedSlots > 0) {
    exitTriggered = true;
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Car Exiting...");

   
    delay(2000);

    // Open the gate
    openGate();
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Car Exited!");
    delay(2000); 
    lcd.clear();
  }

  
  if (digitalRead(IR_Entry) == HIGH) entryTriggered = false;
  if (digitalRead(IR_Exit) == HIGH) exitTriggered = false;

  // Displaying on the LCD
  lcd.setCursor(0, 0);
  lcd.print("Slots Left: ");
  lcd.print(totalSlots - occupiedSlots);
  lcd.setCursor(0, 1);
  if ((totalSlots - occupiedSlots) > 0) {
    lcd.print("Parking Available");
  } else {
    lcd.print("Parking Full!   ");
  }

  delay(500); 
}

// Function to open the gate
void openGate() {
  Serial.println("Opening the gate...");
  myservo.write(gateOpenAngle); 
  delay(3000);                  
  myservo.write(gateCloseAngle); 
}
