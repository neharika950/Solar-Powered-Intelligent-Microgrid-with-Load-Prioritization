# Solar-Powered-Intelligent-Microgrid-with-Load-Prioritization

ABSTRACT 
 
Solar-powered intelligent Microgrid combines smart load management with 
renewable energy to manage power distribution based on batteries' SoC. Two ESP32 
devices communicating through RS-485 (MAX485) are included in the system: one 
master that tracks battery voltage and calculates SoC, and one slave that manages 
loads (fan and light) through relays. 
 
A load control mechanism based on priority ensures effective utilization of energy: all 
loads run at high SoC, critical loads are at medium SoC, and non-critical loads are 
switched off at low SoC. Remote monitoring and control are facilitated using Blynk 
IoT, while ThingSpeak is used for real-time data logging and email notification for 
SoC status. 
 
This microgrid provides a cost-effective and stable energy solution for off-grid sites, 
disaster relief camps, and remote hospitals, providing continuous power supply where 
electricity is scarce. 
 
INTRODUCTION  
 
The Solar-Powered Smart Microgrid combines smart load control with renewable 
power to maximize power distribution according to the State of Charge (SoC) of a 
12V lead-acid battery. Two ESP32 microcontrollers in communication using RS-485 
(MAX485) are used in the system, where: 
 
The master ESP32 measures battery voltage through a 25V voltage sensor, computes 
SoC, and makes smart decisions on load control. 
The master sends control signals to the slave ESP32, and it controls relays to control 
loads connected (light and fan). 
 
A priority-based load control system guarantees energy-efficient utilization: 
 
 High SoC → All loads are on. 
 Medium SoC → Only critical loads are on. 
 Low SoC → non-critical loads are switched off to save battery power. 
 
For remote control and monitoring, the system combines Blynk IoT so that users can 
remotely control loads manually through a mobile application. Also, ThingSpeak is 
employed to log data in real-time as well as provide email alerts when SoC is low or 
reaches critical battery states. 
 
This microgrid is a cost-efficient, decentralized, and reliable power solution for off
grid sites, disaster relief centers, and remote health clinics, guaranteeing an 
uninterrupted and optimized supply of power where access to electricity is minimal. 
 
 
 
  PROBLEM STATEMENT 
As the adoption of solar-powered microgrids grows, the need for efficient energy 
management, real-time monitoring, and automated load control becomes critical. 
Traditional microgrid systems face several challenges that impact their efficiency and 
reliability: 
1. Lack of Real-Time Monitoring – Conventional solar microgrid setups often lack 
continuous tracking of the battery voltage, State of Charge (SoC), and load 
consumption, leading to inefficient power utilization. 
2. Inefficient Load Management – Without an automated load scheduling 
mechanism, excessive power draw or underutilization can reduce system 
efficiency and shorten battery lifespan. 
3. Communication Limitations – Many existing systems use direct-wired 
connections for data transmission, limiting scalability and reliability, 
especially over long distances. 
4. Manual Decision-Making – Traditional microgrids rely on human intervention 
to switch loads based on available power, making them less adaptive to real
time energy fluctuations. 
This project addresses these issues by implementing a solar-powered intelligent 
microgrid that integrates RS-485 communication, remote monitoring (Blynk IoT), and 
automated load management to enhance energy efficiency, reliability, and 
scalability. 
 
 
METHODOLOGY 
 
 
1. System Architecture: 
 
The intelligent microgrid solar powered unites smart load management and renewable 
energy with remote monitoring. The system's primary components are: 
 
 Solar Power Source – Supplies energy to the system. 
 Battery Storage Unit (12V, 7.2Ah Lead-Acid Battery) – Sells over excess solar 
energy and provides power in the event of solar input shortfalls. 
 ESP32 Microcontrollers – Two ESP32 modules talk through RS-485 
(MAX485), with one being the master and one slave for control and data 
exchange. 
 RS-485 Communication (MAX485 Module) – Allows reliable long-distance 
communications between the ESP32 modules. 
 Voltage & Current Sensors – Monitor battery voltage and current to calculate 
State of Charge (SoC) and available energy. 
 Relay Module – Switches loads (light and fan) based on SoC levels. 
 Blynk IoT & ThingSpeak – Employed for remote switching, data plotting, and 
emailing. 
 
 

 
2. Hardware Implementation: 
 
ESP32 Modules (Master & Slave) 
 
Master ESP32: 
 Monitors the battery voltage from a 25V voltage sensor and estimates SoC. 
 Reports voltage and SoC data to the Slave ESP32 over RS-485 (MAX485 
module). 
Slave ESP32: 
 It accepts SoC and voltage information from the slave. 
 Enforces relay-controlled switching of the load based on given SoC ranges. 
 Post the data to ThingSpeak for logging and real-time visualization. 
 Allows remote load control through Blynk IoT. 
 
Sensors & Modules Utilized 
 Voltage Sensor (0-25V) – Used to measure battery voltage for SoC calculation. 
 Current Sensor (ACS712, 20A) – Used to measure battery current flow. 
 2-Channel Relay Module – Used to control light and fan according to SoC 
status. 
 MAX485 Module – Allows RS-485 communication between ESP32 modules. 
 
3. Communication & Data Flow: 
 
 Master ESP32 reads the battery voltage and computes SoC. 
 The Master ESP32 sends SoC and voltage data to the Master ESP32 through 
RS-485. 
 The Slave ESP32: - Uses SoC information to decide optimal load running. - Manages relay states accordingly. - Transmits data to ThingSpeak to store and visualize in the cloud. 
 
4. Load Management Strategy: 
 
A priority scheme of relay control manages load running according to battery SoC 
levels: 
 SoC > 75% → Light and Fan ON. 
 50% < SoC ≤ 75% → Only Light ON. 
 SoC ≤ 50% → All non-essential loads OFF to save battery energy. 
 
The relay switching cycle is automated and executed every 20 minutes to guarantee 
effective load allocation according to available battery energy. 
 
5. Remote Monitoring & Data Analysis: 
 
 Blynk IoT provides real-time remote load control through a smartphone app. 
 ThingSpeak Cloud retains voltage and SoC readings so users can see trends and 
maximize load scheduling. 
 Email alerts are sent through ThingSpeak to notify users of low SoC levels. 
- 8 - 
 
RESULTS 
 
 <img width="557" alt="image" src="https://github.com/user-attachments/assets/7d8f5b6d-3616-4709-9669-6a3f12db752f" />

 The table (Fig.01) presents real-time solar panel readings, showing the 
relationship between irradiance, battery voltage, and SoC. 
 
Location: AB2, third floor 
Time: 12.00 PM TO 03.00 PM  
*Irradiance is read by using the app “Solar Radiation. 
 

 
Table 01. Solar Panel Readings 
 


 <img width="533" alt="image" src="https://github.com/user-attachments/assets/c8a08618-4517-40c6-a337-2438557f1cce" />

 
Fig.01. Charge Controller and Battery Voltage Sensor 
 
 
 
 
 
 
 
 When the battery gets drained or disconnected. 



 <img width="422" alt="image" src="https://github.com/user-attachments/assets/b7109e50-977c-40b5-a35a-41ff56d69562" />

Fig.02. The Thingspeak website gets information and analyzes  
 


 <img width="392" alt="image" src="https://github.com/user-attachments/assets/a9e57890-3726-4aa4-87c1-91066f2610aa" />

Fig.03. User gets the mail regarding the alert 

 
 When during the normal condition of the battery. 
 

 <img width="291" alt="image" src="https://github.com/user-attachments/assets/14de6d65-4732-4cec-bed5-829f726987fc" />

Fig.04. The Thingspeak website gets information and analyzes 
 
 

 <img width="481" alt="image" src="https://github.com/user-attachments/assets/57a3b6ae-0725-41ce-8053-bd2e48783e09" />

Fig.05.Load Prioritizing with the Soc Value at the standalone state 
 
 

 
 
 <img width="472" alt="image" src="https://github.com/user-attachments/assets/5864c2ce-b118-49d3-b7dd-292e05350dc1" />

Fig.06. The serial communication between two ESP32s successfully transfers SoC data via 
RS-485. 
 
 

<img width="516" alt="image" src="https://github.com/user-attachments/assets/c26090ad-b46c-4fe8-9030-c933ed9f9ec6" />

 
Fig.07. The Serial  Data Transmission between two Esp32 successfully transfers SoC data via 
RS-485 and load prioritizing  
 
 
 

 
 <img width="502" alt="image" src="https://github.com/user-attachments/assets/6e2ecd3f-c2f7-45b1-8b38-002a1bc81da7" />

 
 
Fig.08. Remote Controlling using Bylnk Iot 
 
 
CONCLUSIONS  
The solar-powered intelligent microgrid showcased in this work is a vital step toward 
distributed, sustainable, and autonomous power management. Leveraging real-time 
load prioritization according to the State of Charge of the battery enables the system 
to optimize power utilization even during stressed energy conditions. The integration 
of ESP32 microcontrollers with the RS-485 communication protocol, without any 
bottlenecks in data exchange across modules, comprised the backbone of an 
intelligent control network. The addition of IoT platforms such as Blynk and 
ThingSpeak augmented the system's ability to monitor remotely, have user
configurable alerts, and view historical data, giving users visibility and control. 
This project is not only affordable and environmentally friendly but also tackles a 
pressing worldwide demand—access to energy in rural and underdeveloped areas. 
From lighting rural homes and medical camps to powering emergency shelters during 
natural disasters, the portability and scalability of this system make it an invaluable 
asset in disaster resilience and rural electrification. The load-priority mechanism 
makes certain that mission-critical devices stay on in low-resource conditions, 
ultimately maximizing energy efficiency, cutting down waste, and extending battery 
life. 
In the future, the project will provide a solid foundation for the integration of next
generation technologies like AI-based load forecasting, MPPT controllers, and hybrid 
renewable sources. With additional developments, it has the potential to transform 
into a fully autonomous, self-healing microgrid—able to adapt to shifting conditions 
in real time while providing power with no disruptions. In a sense, this project 
represents the future of smart energy systems: green, intelligent, and resilient. 
