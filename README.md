# ArduinoAquaponics
Using Blynk IoT to control Arduino MKR WiFi 1010, and return sensor data to phone.

# Part 1: Downloading the Necessary Software

- 1. Download the Arduino IDE onto your computer. Any version should be fine. [Download Arduino IDE](https://www.arduino.cc/en/software)
- 2. Download the Blynk IoT app onto your phone. Make sure it is NOT the Legacy app, which will no longer be supported.
    - [Blynk Download on Google Play](https://play.google.com/store/apps/details?id=cloud.blynk&hl=en_US&gl=US).
    - [Blynk Download for Iphone](https://apps.apple.com/us/app/blynk-iot-new/id1559317868).
    - Make an account with Blynk [Blynk Sign Up](https://blynk.cloud/dashboard/register)

# Part 2: Getting Started With Blynk IoT

1. Documentation [link](https://docs.blynk.io/en/getting-started/what-do-i-need-to-blynk)

# Part 3: Arduino Code ReadMe

### Features: 
  1) Feed at certain times throughout the day
    1a) spins a stepper motor a certain # of steps
    1b) notifies me fish were fed at the given time
  2) water parameters updated every interval Turbidity, pH, temperature, TDS

### Pin description:

1) Turbidity sensor
    NOTE: This sensor normally reads from 0-4.2V. However, the Arduino MKR 1010 pins read in the range of 0-3.3V. So we need to step-down the voltage with a voltage divider [what is a voltage divider?](https://en.wikipedia.org/wiki/Voltage_divider)

    PINS: (look at wikipedia article for diagram) 
    5V from main board (do not pull 5V from a wall module for this)
    Z [=] resistor
    Vin (output from the turbidity sensor) 
    Z1 = 2000 Ohm
    Z2 = 7230 Ohm, then wire to ground
    Vout = wire to A2 pin on the arduino board

2) Stepper motor 
    Nema 17 stepper motor and Stepper Motor Driver TB6600
    12V 1 amp power source to the VCC (+) and Grnd (-) pins
    B-: red wire to motor
    B+: green wire to motor
    A-: blue wire to motor
    A+: yello wire to motor
    Dir-: Grnd
    Dir+: D8 (might need to switch to D14, hard to tell if I swapped D8 and D14)
    Pul-: Grnd
    Pul+: D14

3) Various pin # for Blynk Widgets. 
    Note that some pins don't actually exist on the arduino board. The Virtual pin is just used to communicate with Blynk.
    V0    Terminal (must be v0)
    V1    Current Time
    V2    Current Date
    V3    H20 Temp
    V4    pH
    V5    TDS
    V6    Turbidity
    V7    Food Per Meal
    V8    Feed Fish Button command
    V9    Meals Today (numfeedings)
    V10   BreakFast Time (meal1)
    V11   Lunch Time (meal2)
    V12   Dinner Time (meal3)
    V13   Modnight Snack Time (meal4)
    V14   Grow Light timing
    V15   Fish Tank Light Timing
    V16   Grow light button sync
    V17   Fish Tank Light button sync
    V18   Water Sensor alert 
    V19   Number of Disconnections
    V20   Uptime counter since last disconnection

### Future Features:
    1) adding lights + color control for main tank
    2) Overflow/water spill sensors on floor in case of emergency spills
    3) water height sensors in each tank (and possibly grow bed)
    4) flow rate meter for pump 
    5) Valve control for directing pump water to tank/garden
    6) Water heater control / temperature control