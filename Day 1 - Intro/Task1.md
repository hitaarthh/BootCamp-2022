<a href="https://www.tinkercad.com/things/azOPyEa4ytt?sharecode=VX-Y9VYOZTGjo6zeabijYUQipnqg3iDjYqT7ETs4u3w"><img src="https://img.shields.io/badge/Tinker%20CAD-Click%20to%20simulate-brightgreen"></a>

<div align="center"><h1>Task 1</h1></div>

- Interfacing PIR Sensor with Arduino UNO 3.



### Simulation Diagram:

<div align="center">
   <img width="400" alt="Simulation Diagram" src="https://user-images.githubusercontent.com/91147942/186391762-47a85ac4-5e23-4cb2-b049-db2b930ef19d.png">
</div>


### Source Code:

```C++
// C++ code
//
void setup()
{
  pinMode(12, INPUT);
  Serial.begin(9600);
}

void loop()
{
  if ((digitalRead(12)==HIGH)){
    Serial.println("Motion detected...");
  }
  else{
       Serial.println("No Motion detected.");
  }
}
```
