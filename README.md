Satellite Training Kit

A hands-on, low-cost CubeSat-style training kit that helps students learn how a small satellite works by building, simulating and testing its main subsystems on the ground.

The kit splits a satellite into three stackable modules, each built from common Arduino-compatible parts:

Subsystem	Role	Key components
OBC (On-Board Computer)	Collects sensor data, position and images	Arduino Uno, GY-91 IMU (MPU-9250 + BMP280), GPS module, microSD breakout, ESP32-CAM
EPS (Electrical Power System)	Supplies, regulates and monitors power	Battery, DC-DC converter, ACS712 current sensor, solar panel (simulation)
COM (Communication)	Sends telemetry to a ground station	Arduino Nano Every, HC-12 (SI4463) wireless serial module, Zigbee/XBee link

The modules sit inside a 3D-modelled outer chassis (base, body and cap).

Repository structure
Satellite-Training-Kit/
├── Arduino Codes/        # Sensor test sketches (.ino) with compiled .hex files for Proteus
│   ├── BMP085test/       # Barometric pressure, temperature and altitude (I2C)
│   ├── DHT12/            # DHT12 humidity and temperature (I2C)
│   ├── DHT22Default/     # DHT22 humidity and temperature (SimpleDHT library)
│   ├── DHTtester/        # DHT11/21/22 test (Adafruit DHT library)
│   ├── HUM/              # Humidity-controlled fan: switches a fan on at ≥ 75% RH
│   ├── LM35/             # LM35 analog temperature sensor
│   └── LM35_2nd/         # LM35 with °C and °F output
├── Arduino/
│   ├── DEviceExample/    # GPS reading with TinyGPS++ over SoftwareSerial
│   ├── ESP-32 Cam/       # ESP32-CAM pinout and sample photos
│   └── Library/          # Libraries: TinyGPS++, ESP32 core, ATtinySerialOut, XBee (Proteus)
├── Bluetooth module/     # Bluetooth and solar panel libraries for Proteus
├── Proteus_Files/        # Circuit simulations
│   ├── Compiled System/  # Full OBC simulation
│   ├── Sub-circuit EPS   # Power system sub-circuit
│   ├── Zigbee_TX / RX    # Wireless transmitter and receiver link
│   └── test_DHT22        # DHT22 sensor test
├── Solid-Works/          # 3D CAD models
│   ├── OBC/  EPS/  COM/  # Per-subsystem assemblies and component STEP files
│   ├── Outer Chassis/    # Chassis bottom, body and cap
│   └── Compiled_stack_final.SLDASM   # Full assembled stack
└── Video rendering/
    └── Full_Chassis_design.mp4       # Rendered walkthrough of the chassis design
Requirements

Software

Arduino IDE (1.8+ or 2.x)
Proteus Design Suite (8.x or later) for circuit simulation
SolidWorks for the CAD files. The component .STEP files also open in free tools such as FreeCAD.

Arduino libraries

Adafruit BMP085 Library
Adafruit DHT Sensor Library and Adafruit Unified Sensor
SimpleDHT
DHT12 (Rob Tillaart)
TinyGPS++ (included in Arduino/Library/)

Install them from Sketch → Include Library → Manage Libraries…, or for .zip files use Sketch → Include Library → Add .ZIP Library….

Getting started
1. Run a sensor sketch on hardware
Open a sketch from Arduino Codes/, for example DHT22Default/DHT22Default.ino.
Wire the sensor as described in the comments at the top of the sketch.
Select your board (for example Arduino Uno) and port, then click Upload.
Open the Serial Monitor and set the baud rate the sketch uses (9600 or 115200).
2. Simulate in Proteus
Copy the libraries from Bluetooth module/ and Arduino/Library/ (XBee) into your Proteus library folder.
Open a project from Proteus_Files/.
Double-click the Arduino part and point Program File to the matching .hex file in Arduino Codes/.
Press Run to start the simulation.
3. Explore the mechanical design

Open Solid-Works/Compiled_stack_final.SLDASM to see the full stack, or watch Video rendering/Full_Chassis_design.mp4 for a quick overview.

Learning outcomes

Working through the kit, students practise:

Reading environmental sensors (temperature, humidity, pressure, altitude)
Getting position data from a GPS module
Simple thermal and humidity control using a sensor-driven fan
Wireless telemetry between a satellite and a ground station
Power distribution and current monitoring in an EPS
Circuit simulation before building hardware
Mechanical integration of subsystems in a CubeSat-style stack
Author

Md. Khairul Bashar Bhuiyan · GitHub @KBhuiyan13

Acknowledgements

Several test sketches are based on open-source examples from Adafruit, Rob Tillaart (DHT12), SimpleDHT and Mikal Hart (TinyGPS++). Their original licences and credits are kept in the source files.





















