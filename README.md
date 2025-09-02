AQUA-FEEDBOAT

<img width="443" height="590" alt="image" src="https://github.com/user-attachments/assets/54d2a717-30ce-490b-83af-6e4f77ed5b97" />

DOCUMENT No. i4MT/AQUAFEEDBOAT/UM
       Prepared and published by
i4 Marine Technologies Pvt. Ltd. Electronic Estate, Pune Satara Road
Pune-411 009



           USER HANDBOOK FOR AQUANAUT 30 V3
CONTENTS

0.	TITLE PAGES								          

1.	CHAPTER 1                                                                                              	4
      Introduction				 
2.	CHAPTER 2                                                           			          	  
2.1 Applications                                                   
2.2 Leading Particular And General Data
3.	CHAPTER 3                                                         			              
 3.1 setup and operation guide  
 3.2 Flashing firmware
 3.3 Radio master tx setup                                    
 3.4 Autonomous navigation 
 3.5 Feeder motor setup with RC 
 3.6 Lora communication 							

4.	CHAPTER 4                                                                                                            47
                4.1 System specification
                4.2 Mechanical drawings                                                	

CHAPTER 1

 Introduction
This project presents the design and implementation of an autonomous fish feeder boat, which is primarily intended for use in aquaculture. The boat is capable of both manual and autonomous operation, enabling users to efficiently distribute fish feed while also monitoring water quality in real-time. The system is designed to reduce manual labor and improve feeding accuracy by automating the feeding process using a combination of remote control (RC), onboard sensors, and wireless communication.

2. System Overview
The autonomous fish feeder boat is controlled using an Eagle i flight controller, which supports autonomous navigation via the iNav firmware. Manual control is facilitated through an RC transmitter, which allows users to steer the boat and control the feeder motor using designated toggle switches.
The propulsion system consists of two Brushless DC (BLDC) motors. These motors are connected to the flight controller via PWM signal wires. The flight controller interprets the PWM signals and regulates the motors accordingly to control the movement and speed of the boat.
The RC transmitter has two toggle switches configured for specific functions. One switch is used to activate autonomous mode after the feed has been loaded into the onboard feeder. The other switch is used to control the feeder motor, which dispenses the food to the fish.

3. Water Quality Monitoring System
To ensure optimal conditions for fish health, the boat is equipped with a water quality monitoring system. This system includes a pH sensor, a turbidity sensor, and a temperature sensor. These sensors continuously collect data from the water body.
An ESP32 microcontroller is used to read the sensor data. The ESP32 processes the sensor inputs and transmits the data using a LoRa (Long Range) communication module. This allows for real-time monitoring of water quality parameters at a base station located far from the boat.



4. Feeding Mechanism
The feeding mechanism is mounted on the top side of the boat and is capable of holding a significant quantity of fish feed. Once the feed is manually loaded into the feeder, the operator can activate the feeder motor using a toggle switch on the RC transmitter.
When the switch is toggled, the motor rotates and dispenses the feed into the water. This mechanism can be controlled during both manual and autonomous modes, providing flexibility to the operator.

5. Operating Modes
The fish feeder boat supports two primary modes of operation: manual mode and autonomous mode.
In manual mode, the operator controls the boat directly using the RC transmitter. This includes steering, speed control, and feeder motor activation.
In autonomous mode, the operator fills the feeder and then toggles the designated switch on the RC transmitter to activate the autonomous navigation system. Once in autonomous mode, the boat follows a set of predefined waypoints and can dispense feed at specific locations if programmed accordingly.

6. Communication and Telemetry
The system uses a LoRa module for wireless communication between the boat and the base station. The ESP32 microcontroller sends the collected water quality data via LoRa, allowing users to monitor the status of the water in real-time from a remote location.
This communication system can also be extended to transmit other telemetry data, such as GPS coordinates, battery voltage, and heading, depending on the application requirements.

7. Applications and Benefits
This autonomous fish feeder boat is designed to significantly reduce manual labor in fish feeding operations. It ensures that feed is distributed accurately and consistently, which promotes better growth and health of the fish.
In addition, the real-time water quality monitoring feature allows aquaculture operators to detect changes in water conditions early and take corrective action promptly. The combination of automation and remote monitoring makes this system particularly useful for large ponds and remote aquaculture sites.

                                                             Short description  about Eagle-i


<img width="940" height="873" alt="image" src="https://github.com/user-attachments/assets/8cd63e63-1c43-491f-aff8-f85c52ec03b4" />



This flight controller is a versatile, high-performance board designed for advanced applications in remote-controlled vehicles, such as drones and boats. It features an STM32 microcontroller and runs the INAV firmware, which enables enhanced navigation and control.
   The flight controller is powered by an STM32 microcontroller with 1 MB of flash memory and a 166 MHz refresh rate.
   It supports an input voltage range of 6-25V and provides a stable 5V output, powering all peripherals across the board.
   It runs on INAV firmware, enabling advanced navigation and control capabilities.


Peripheral Ports and Communication
1.	Motor Control: 4 GPIO ports for motor connections.
2.	Switches:
o	1 port for LEDs.
o	1 port for a buzzer.
3.	UART Ports:
o	1 port for GPS.
o	1 port for the receiver.
o	2 additional UART ports for custom sensors 
4.	I2C Ports:
o	Used for pressure sensors and magnetometers.
5.	SPI Ports:
o	Used for MPU6500 gyroscope/accelerometer and SD card integration.
6.	Camera Port:
o	Enables integration with FPV (First-Person View) cameras.
o	Includes an On-Screen Display (OSD) feature for telemetry data overlay on the video feed.
7.	DFU Port:
o	Provides support for Device Firmware Upgrades via USB without requiring specialized hardware.



CONNECTION DIGRAM 


<img width="940" height="849" alt="image" src="https://github.com/user-attachments/assets/f735444f-81b5-4337-9993-38b1232c34fa" />


                                        CHAPTER-2

2.1 Applications of Aqua Feedboat
The autonomous fish feeder boat has several practical applications, particularly in the field of aquaculture.
Firstly, it can be used for automated fish feeding in aquaculture farms. The boat eliminates the need for manual labor by automatically distributing fish feed across the pond or lake. This ensures consistent and timely feeding, which is crucial for the healthy growth of fish.
Secondly, the boat is equipped with pH, turbidity, and temperature sensors, allowing it to perform real-time water quality monitoring. This feature helps aquaculture operators maintain ideal water conditions and detect any environmental changes that could negatively affect fish health.
Thirdly, the system allows remote operation of feeding tasks. Using an RC transmitter, the operator can control the boat manually or switch it to autonomous mode without physically approaching the water body. This is especially useful for large or difficult-to-access ponds.
The boat also supports efficient feed distribution. Its autonomous navigation ensures that feed is evenly spread over a defined path, reducing waste and improving feed conversion efficiency.
Additionally, the boat uses a LoRa module to send sensor data to a base station. This enables data logging and analysis, allowing users to review historical water quality trends and make informed decisions to enhance fish farm management.
Another application is in large or remote aquaculture sites, where manual feeding is impractical. The autonomous boat can cover long distances and operate independently, making it ideal for such environments.
Finally, the integration of automation and environmental monitoring promotes sustainable fish farming practices. By reducing manual intervention and optimizing resource usage, the system supports efficient and eco-friendly aquaculture operations.


CHAPTER-3
          Aqua Feedboat Setup and Operation Guide
3.1 Fish Feeder Boat – Basic Manual Setup + Flashing firmware                      (2 Thrusters + RC Control)
 To set up your boat for manual control using a RadioMaster RC transmitter and two APSQEEN BLDC motors (thrusters), powered by a 24V battery and controlled by an Eagle i flight controller running iNav firmware.

 Hardware List
Component	Description
Eagle i Flight Controller	Main brain of the boat running iNav
RadioMaster TX12 (EdgeTX)	RC transmitter used to control the boat
RadioMaster RP1 ELRS	RC receiver to receive control signals
2x APSQEEN BLDC Motors + ESCs	Motors for propulsion and steering
24V Battery	Powers motors and other electronics
24V to 5V Converter	Powers the Eagle i flight controller
 Power Setup
1.	Main Power:
o	Connect your 24V battery to a power on the control box
o	Use a 24V to 5V converter to power the Eagle i flight controller.
o	Connect the converter's 5V output to the 5V and GND pins of the flight controller.
2.	Motor Power:
o	Connect each BLDC motor to its respective ESC.
o	Connect both ESCs' power (24V) and GND lines to the battery.
o	Connect each ESC's signal wire to the Motor 1 and Motor 2 PWM outputs on the flight controller.

 Receiver (RP1 ELRS) Wiring
1.	Connect the RP1 ELRS receiver to a UART port on the flight controller:
o	RP1 TX → FC RX
o	RP1 RX → FC TX
o	RP1 5V → FC 5V
o	RP1 GND → FC GND
2.	In iNav Configurator (later), you’ll enable Serial RX on the UART port used.


3.2                                 Flashing Firmware in Eagle-i 

<img width="709" height="399" alt="image" src="https://github.com/user-attachments/assets/bfcc3341-e355-42f6-93bf-139b64a1e92f" />


 Flash INAV.hex Firmware (Local) on Eagle-i
  Prerequisites:
•	INAV Configurator installed
Download from GitHub
•	Flight controller in DFU mode
•	Your .hex file ready on your computer


 Steps:
1. Launch INAV Configurator
Open INAV Configurator (use latest version if possible).

2. Connect the Board in DFU Mode
Make sure the Eagle-i flight controller:
•	Is connected via USB
•	Shows DFU in the top-right port dropdown of INAV Configurator
(If it says “No DFU detected,” check that the boot button was held when plugging it in.)


3. Go to "Firmware Flasher" Tab
•	On the left sidebar, select Firmware Flasher.


<img width="704" height="396" alt="image" src="https://github.com/user-attachments/assets/ea36ecb0-6ed7-4859-811f-05583969b65e" />


4. Load Firmware from File
•	Click "Load firmware [Local]"
•	Select your .hex file (e.g., EAGLEI.hex)

5. Flash the Firmware
•	Hit "Flash Firmware"
•	It should start writing the firmware. You’ll see a progress bar.
•	Wait for “Flashing successful” message.

      Disconnect and reconnect the board (this time without the boot button).

•	Go to the “Connect” screen and verify the firmware boots.
•	Then configure your board in INAV Configurator (ports, mixer, sensors, etc.)



Troubleshooting
If anything fails:
•	Try a different USB cable or port
•	Make sure no other apps are using the COM port
•	If DFU is not showing up, you might need Zadig to reinstall the driver (want help with that?)

1.	Connections:
o	Motors: ESCs connected to the PWM outputs of the RMA board.
o	Sensors: GPS and compass interfaced via UART or I2C ports for navigation.
o	Receiver: RadioMaster RP1 ELRS receiver linked through UART for real-time communication.
o	Power: A dedicated power module to ensure stable power supply.

Calibration of RMA Board Using iNav Configurator
1.	Connect the Board:
o	Use a USB-C cable to connect the RMA board to your PC.
o	Open iNav Configurator and click Connect.
o	Select the model type for your application (e.g., "Boat" for safety boat configuration).




<img width="584" height="329" alt="image" src="https://github.com/user-attachments/assets/fb190e7d-e983-4bab-8f38-19d3f4c67cba" />




2.	Calibrate Accelerometer:
o	Follow the on-screen instructions to calibrate the accelerometer



<img width="623" height="350" alt="image" src="https://github.com/user-attachments/assets/23fe6863-9bde-4ca2-ad63-020738f40ab7" />



3.	Mixer Configuration:
o	Navigate to the Mixer tab.
o	Select the platform type (e.g., "Boat").
o	Add new mixer rules for the motor configuration as required.



<img width="648" height="364" alt="image" src="https://github.com/user-attachments/assets/71ec9194-dba2-4db1-8858-ae124d3bd59c" />



4.	Output Setup:
o	Go to the Output tab.
o	Enable motor and servo outputs.
o	Set the appropriate ESC protocol for your motor.
o	Enable Stop Motors on Low Throttle.
o	Set Motor Idle Power to 0.
o	Enable Reversible Motors Mode.



<img width="673" height="378" alt="image" src="https://github.com/user-attachments/assets/4397b60c-adb2-462f-a75f-0efe5b4bddfd" />



5.	Ports Configuration:
o	Check the Ports tab to ensure Serial RX is enabled.




<img width="720" height="405" alt="image" src="https://github.com/user-attachments/assets/df2d1a79-85ee-4a64-889a-3c89a6ffb263" />



6.	Configuration Tab:
o	Enable the following options:
	GPS for Navigation and Telemetry.
	Telemetry Output.
	Reversible Motors Mode.
	Motor and Servo Outputs.


<img width="836" height="470" alt="image" src="https://github.com/user-attachments/assets/c685cf3d-1618-4020-aa41-47202e5309fa" />



8.	Modes Setup:
o	In the Modes tab:
	Assign the Arm mode to a channel on your RC remote.
	Set the range for arming the system.
o	Ensure your RC remote is connected to the receiver, which is linked to the RMA board.



<img width="642" height="361" alt="image" src="https://github.com/user-attachments/assets/8c6c1ed8-c13f-4245-9cc8-c59fe9facfa6" />



8.	Receiver Configuration:
o	In the Receiver tab:
	Set Receiver Mode to Serial.
	Set Serial Receiver Provider to CRSF (if using RadioMaster RC remote or as per your transmitter).



<img width="746" height="420" alt="image" src="https://github.com/user-attachments/assets/949ab9e4-479b-4a60-8bb2-7e5ffc353631" />



9.	CLI Commands:
o	Open the CLI tab and enter the following commands:
	set min_check =  set the minimum value
	set max_throttle = set the maximum value
o	Save the settings by typing save.



<img width="809" height="455" alt="image" src="https://github.com/user-attachments/assets/ff33eccf-7c04-4e23-8697-9e202da7b791" />



                        BASIC CONNECTION DIGRAM OF FLIGHT CONTROLLER WITH 2 MOTOR
                        


<img width="940" height="1221" alt="image" src="https://github.com/user-attachments/assets/853cf1ed-5458-4e80-aaeb-ac86b87e45e3" />




                      Communication between transmitter and receiver
                      


1.	Transmitter and Receiver Communication:
o	You are using the RadioMaster TX12 RC transmitter with the ELRS (ExpressLRS) protocol, and the RadioMaster RP1 Nano ELRS receiver is connected to the RMA flight controller.
o	The transmitter sends control commands (throttle, yaw, pitch, roll) to the receiver over the ELRS protocol.
2.	Receiver and RMA Board:
o	The RP1 Nano receiver is connected to the UART port of the RMA flight controller.
o	The receiver communicates with the flight controller to relay the commands from the transmitter for controlling the boat’s movements.
3.	Telemetry Data:
o	The RMA board generates telemetry data such as GPS position, battery status, and other metrics.
o	This data is sent back to the RP1 Nano receiver through the same UART connection.
4.	Telemetry Feedback to the Transmitter:
o	The RP1 Nano receiver uses the CRSF (Crossfire) protocol to send telemetry data back to the TX12 transmitter.
o	The transmitter displays this telemetry data, allowing you to monitor the boat's status.
5.	Control and Monitoring:
o	With this setup, you can control the boat using the transmitter and simultaneously view telemetry data directly on the transmitter's screen.




3.3                                    RADIOMASTER  TX12  setup



<img width="508" height="508" alt="image" src="https://github.com/user-attachments/assets/93ef6288-8605-4e8d-b283-430bb1458bfa" />


    how to:
1.	Bind RadioMaster RC to RP1 ELRS Receiver
2.	Add and configure channels (for switches, etc.)
3.	View telemetry data

1. Binding RadioMaster to RP1 ELRS Receiver (Bind Method)  
1.	Power off receiver.
2.	Power on and off 3 times the receiver  
o	The LED will start fast blinking = Bind mode.
3.	On the transmitter:
System → Tools → ExpressLRS → [Bind]
4.	Wait 5–10 seconds.
o	LED on RP1 becomes solid = bound.
 Now your receiver is bound to the transmitter!



2.Add Channels to Switches (for flight modes, relays, etc.)
1.	On the RadioMaster transmitter:
o	Go to Model Settings → Inputs
2.	Add Inputs:
o	Example:
	Input 1 = Throttle (CH1)
	Input 5 = SA Switch → for mode control
	Input 6 = SB Switch → for feeder
3.	Go to: Model Settings → Mixes
4.	Add mixes for each channel:
o	Example:
                              CH5 → Source: SA
                              CH6 → Source: SB
                      ✅ Now CH5 and CH6 control two switches.

   3. View Telemetry (Battery, GPS, etc.)
A. Enable Telemetry on Flight Controller
1.	Connect FC to Configurator (INAV or Betaflight).
2.	Go to Ports tab:
o	Set in UART 3 on telemetry section enable mavlink and set the baud rate to maximum 
o	In the receiver  tab select mavlink in serial reciver provider  
3.	Go to Configuration tab:
o	Enable Telemetry option.
4.	Save and Reboot FC.



B. View Telemetry on Transmitter
1.	On RadioMaster:
Model Settings → Telemetry → Discover new sensors
2.	After few seconds, you’ll see:
o	RSSI
o	Battery voltage
o	GPS
o	Current draw
o	Flight mode
o	More depending on FC setup
✅ You can assign telemetry sensors to your home screen or sound alerts.

 2       Aqua-Feedboat – Autonomous Navigation Setup
         
•	Assign a switch to enable Autonomous (NAV) mode.
•	Upload waypoint missions.
•	Automatically load the mission on boot.
•	Enable Return to Home (RTH) in case of RC signal loss or on command.

 Prerequisites
You should already have:
•	iNav flashed on Eagle i flight controller.
•	Motors and RC receiver connected.
•	Boat working in Manual Mode.




  Required Software  
•	iNav Configurator
•	(Optional) mission planner – for easier waypoint planning

1️ Assign Autonomous Modes to a Switch
1.	Connect flight controller via USB → open iNav Configurator.
2.	Go to Modes tab.
3.	Add these modes:
o	MANUAL: For manual RC control.
o	NAV WP: For automatic waypoint following.
o	NAV POSHOLD (optional): For holding position (like stop & hover).
o	NAV RTH: For Return to Home (manual or failsafe).
4.	Assign a switch from your RC transmitter (e.g., SA or SB) to each mode using AUX channels.
5.	Click Save.

2️ Setup Waypoint Mission (Using iNav Configurator)
1.	Go to "Missions" tab in iNav Configurator.
2.	Click "Add Waypoint" and set coordinates.
o	You can enter coordinates manually
3.	Add a few points around your water body.
o	Altitude: 0 (you’re on water)
o	Speed: ~2–5 m/s
4.	Once finished:
o	Click Upload Mission → saves waypoints to flight controller.
o	Click "Save to Flash" (important!)
→ Ensures mission loads automatically on boot.

3️ Set Home Position & Return To Home (RTH)
A. Home Point Setup
1.	Home is automatically set on GPS lock at power-up.
2.	You can verify the home position in the OSD tab or via CLI command:

4️ Test Before Launching in Water
1.	With battery connected and GPS lock acquired:
o	Switch to NAV WP mode → boat should wait for arming
o	ARM the boat → boat should begin moving toward waypoint 1
2.	During mission:
o	Switch to RTH → boat will return to GPS home point
o	Switch back to Manual → you regain RC control



       
3.4     WAYPOINT NAVIGATION USING EAGLE-i WITH MISSION PLANNER 

Way Point Mission Workflow with EAGLE i Flight Controller, RadioMaster TX Transmitter & ELRS Ecosystem

1   Configure the EAGLE i Flight Controller for a Boat
1.	Load INAV firmware appropriate to your board (e.g., INAV 8.1 “Eagle”).
2.	On the Configuration ▶ Mixer tab choose Boat/Rover layout and assign:
Output	Function	Note
M1	Motor A (Port)	Normal or reverse PWM as needed
M2	Motor B (Starboard)	Yaw mix for differential thrust


<img width="505" height="284" alt="image" src="https://github.com/user-attachments/assets/19d40763-0ddf-4bd4-9720-0b325c85c54e" />

2   put the reciver in wifi mode. a wifi will be visible in your laptop and click on the hotspot, you will be directed to a browser on which you can set the receiver 



<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/e0aed88f-4246-472c-9116-d607d5497c76" />


In the model setup select mavlink as serial protocol



<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/16a7fa32-1ef6-460e-8ff9-99b4a732cc9a" />

You can see a option tab next to model you can set baud rate 460800 and click save


<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/c6221072-398c-4869-b912-4afdd4ce6211" />



3   Ports tab – set a spare UART to MAVLink 1 output if you want telemetry to Mission                     Planner in parallel with INAV MSP.
Receiver tab
o	Serial based receiver = MAVLINK
o	Stick protocol to FC is still MAVLINK
o	RSSI Channel = Disable 


<img width="720" height="405" alt="image" src="https://github.com/user-attachments/assets/ce148a78-0dd1-4907-9cae-2a32f19b9c70" />




<img width="707" height="398" alt="image" src="https://github.com/user-attachments/assets/36d67aa8-1f42-4a31-9a32-b4fd0bad8fb0" />



4   Link ELRS Module to Mission Planner
1.	Plug the ELRS RF module’s USB C into the laptop (acts as a USB UART).
2.	In Device Manager note the COM port.
3.	Launch Mission Planner ▶ INITIAL SETUP ▶ Wizard.
4.	Baud = 460 800, COM = port from step 2, CONNECT.
o	Mission Planner should display MAVLink heartbeat within seconds.




<img width="680" height="382" alt="image" src="https://github.com/user-attachments/assets/6b9e274e-e60a-41a6-85f8-5e75cd274284" />




5   Assign a “NavWP” Channel inside INAV
1.	Modes tab → add a line, select Nav WP.
2.	Pick an unused AUX channel (e.g., CH7).
3.	Set the slider range (e.g., 1500 µs–2000 µs => ON).
On the TX create a SAFETY/3 position switch mapped to the same channel.




<img width="640" height="360" alt="image" src="https://github.com/user-attachments/assets/3f3ea629-9213-42b8-9d62-8dfa33b99723" />



6   Plan Your Way Point Path
1.	In Mission Planner click PLAN.
2.	Drop way points on the map; choose WAYPOINT command, alt = 0 m.
3.	Click Write WPs to upload to the FC (stored in flash).



<img width="662" height="373" alt="image" src="https://github.com/user-attachments/assets/fd18caef-7a99-497e-8a7f-8e1924f17cf5" />




7   Execute the Mission on the Water
1.	Power the boat and acquire GPS 3D fix 
2.	Arm in MANUAL and test throttle + steering.
3.	Flip the NavWP switch → FC enters AUTO and starts the uploaded mission.
4.	Monitor telemetry in Mission Planner
5.	To abort, toggle back to MANUAL or disarm.


