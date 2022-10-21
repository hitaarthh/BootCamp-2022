<a href="https://www.tinkercad.com/things/077OPp6fBwy?sharecode=74rlew6DOBR0MMvY1Px1vNuOmE736uDwJbJcpRLY0ow"><img src="https://img.shields.io/badge/Tinker%20CAD-Click%20to%20simulate-brightgreen"></a>

<div align="center"><h1>Task 2</h1></div>


- Create a Password door lock system (using 4x4 keypad) using Arduino UNO 3.

### Simulation Diagram:

<div align="center">
   <img width="400" alt="Simulation Diagram" src="https://user-images.githubusercontent.com/91147942/186389103-b68ceca7-9caf-4fe3-bb92-b8c998c8526a.png">
</div>

### Source Code: 

```C++
#include <Keypad.h>        // header files to interface keypad along with arduino.
#include <LiquidCrystal.h> // header files to interface LCD display along with arduino.
#include <Servo.h>         // header files to interface the servo motor along with the arduino.

#define Password_Length 5  // initialising a variable Password_length and giving it a constant value of 5.

Servo myservo;
LiquidCrystal lcd(A0, A1, A2, A3, A4, A5);

int pos = 0;

char Data[Password_Length]; // initialising a one-dimensional character array of length of the password.
char Master[Password_Length] = "2404"; // Storing the defauly password 1234.
byte data_count = 0, master_count = 0;

bool Pass_is_good;
bool door = false;
char customKey;

/*---Initialising Keypad---*/

const byte ROWS = 4;
const byte COLS = 4;
char keys[ROWS][COLS] = {
    {'1', '2', '3', 'A'},
    {'4', '5', '6', 'B'},
    {'7', '8', '9', 'C'},
    {'*', '0', '#', 'D'}};

byte rowPins[ROWS] = {0, 1, 2, 3};
byte colPins[COLS] = {4, 5, 6, 7};

Keypad customKeypad(makeKeymap(keys), rowPins, colPins, ROWS, COLS);

/*--- Setting Up the Arduino ---*/
void setup()
{
    myservo.attach(9, 2000, 2400);
    ServoClose();
    lcd.begin(16, 2);
    lcd.print("Welcome Home. ");
    loading("I'm Jarvis.");
    lcd.clear();
}

void loop()
{
    if (door == true)
    {
        customKey = customKeypad.getKey();
        if (customKey == '#')
        {
            lcd.clear();
            ServoClose();
            lcd.print("Door is being closed");
            delay(3000);
            door = false;
        }
    }
    else
        Open();
}

void loading(char msg[])
{
    lcd.setCursor(0, 1);
    lcd.print(msg);

    for (int i = 0; i < 9; i++)
    {
        delay(1000);
        lcd.print(".");
    }
}

void clearData()
{
    while (data_count != 0)
    {
        Data[data_count--] = 0;
    }
    return;
}

void ServoClose()
{
    for (pos = 90; pos >= 0; pos -= 10)
    {
        myservo.write(pos);
    }
}

void ServoOpen()
{
    for (pos = 0; pos <= 90; pos += 10)
    {
        myservo.write(pos);
    }
}

void Open()
{
    lcd.setCursor(0, 0);
    lcd.print("Enter Password");

    customKey = customKeypad.getKey();
    if (customKey)
    {
        Data[data_count] = customKey;
        lcd.setCursor(data_count, 1);
        lcd.print(Data[data_count]);
        data_count++;
    }

    if (data_count == Password_Length - 1)
    {
        if (!strcmp(Data, Master))
        {
            lcd.clear();
            ServoOpen();
            lcd.print(" Door is Open ");
            door = true;
            loading("You may go in");
            lcd.clear();
            lcd.print(" Time is up! ");
            delay(1000);
            ServoClose();
            door = false;
        }
        else
        {
            lcd.clear();
            lcd.print(" Wrong Password!! ");
            loading("Re-enter pass.");
            door = false;
        }
        delay(500);
        lcd.clear();
        clearData();
    }
} 
```