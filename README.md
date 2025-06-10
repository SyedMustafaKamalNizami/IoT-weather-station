# IoT-weather-station
IoT based weather station using esp32 and blynk IoT platform

Project Overview:

This project is an IoT-based weather station designed to provide real-time environmental monitoring using the Blynk platform. Built on the ESP32 microcontroller, the system integrates several sensors to measure key atmospheric parameters including temperature, humidity, carbon dioxide (CO₂) levels, atmospheric pressure, and ambient light intensity. The sensors used are DHT22 for temperature and humidity, MQ135 for air quality and CO₂ estimation, BMP180 for barometric pressure and temperature, and BH1750 for measuring light intensity. A blinking alarm LED is incorporated to provide a visual warning when CO₂ levels exceed 1000 ppm. All sensor data is transmitted to and displayed on the Blynk mobile app, allowing users to monitor environmental conditions remotely.

Hardware Components Used

The ESP32 serves as the central processing and Wi-Fi-enabled unit of the weather station. It communicates with the connected sensors and handles all data processing and transmission to the Blynk platform. The DHT22 sensor captures ambient temperature and humidity. The MQ135 gas sensor estimates CO₂ concentration in the environment. The BMP180 sensor provides accurate atmospheric pressure readings, and the BH1750 light sensor measures the surrounding light intensity in lux. An LED connected to a digital output pin act as a CO₂ alarm. This combination of hardware enables comprehensive environmental monitoring in a compact and cost-effective system.

Circuit Connections

Each sensor and component are interfaced with the ESP32 according to their specific requirements. The DHT22 is connected to a digital GPIO pin, while the MQ135 connects to the ESP32's analog input pin. The BMP180 and BH1750 sensors both operate over the I²C bus and are connected to the ESP32’s SDA and SCL pins. The LED alarm is connected to a digital GPIO and controlled via code. All components share a common ground and receive power from the ESP32’s 3.3V or 5V outputs, depending on their operating voltage. Proper wiring and voltage matching ensure stable performance across all sensors. 

Blynk App Integration

The Blynk platform is used to visualize sensor data in real time on a mobile device. Each sensor is assigned to a virtual pin in the Blynk app, and the readings are displayed using widgets such as labelled value displays and gauge meters. A virtual LED or notification widget can be configured to reflect the status of the CO₂ alarm. The Blynk cloud serves as the communication bridge between the ESP32 and the mobile application. Once the project is connected using a unique authentication token and Wi-Fi credentials, the user can access live environmental data from anywhere with an internet connection.

Working Principle

When powered on, the ESP32 initializes all sensors and begins collecting data at set intervals. The DHT22 measures temperature and humidity, while the MQ135 continuously monitors air quality. If the CO₂ level rises above 1000 ppm, the ESP32 activates the LED alarm, which begins blinking to alert nearby users. At the same time, the BMP180 records atmospheric pressure, and the BH1750 captures light intensity. This data is then sent to the Blynk platform using virtual pins, where it is displayed on the mobile app for real-time monitoring. The system thus ensures constant observation of environmental parameters, with local and remote alerting mechanisms.

CO₂ Alarm Feature

The MQ135 gas sensor provides a simple yet effective way to estimate CO₂ levels in the environment. The ESP32 reads this value and compares it to a predefined safety threshold. If the level crosses 1000 ppm, the system activates a blinking LED to serve as an immediate visual warning. This feature enhances user safety by ensuring that even if the mobile app is not being actively monitored, a local alert is still triggered to draw attention to potentially hazardous air quality conditions.

Software Details

The project is developed using the Arduino IDE with the ESP32 board configuration installed. Key libraries include BlynkSimpleEsp32.h for Blynk integration, DHT.h for the DHT22 sensor, Adafruit_BMP085.h for the BMP180, BH1750.h for light measurement, and Wire.h for I²C communication. The code includes Wi-Fi credentials and the Blynk authentication token. Sensor values are read periodically and sent to the Blynk cloud using virtual pins. The logic for controlling the LED alarm is embedded in the main loop, providing both local and remote feedback on CO₂ levels.

Code and Flowchart

System Initialization

The process begins with initializing the serial monitor for debugging, establishing a WiFi connection, and authenticating with the Blynk cloud using the provided auth token. Sensor hardware (DHT22, MQ135, BH1750, BMP180) is configured for data acquisition.

Main Loop Execution

The system enters an infinite loop where sensor data is continuously read and processed. Temperature and humidity values from the DHT22 sensor are transmitted to Blynk virtual pins V4 and V5, respectively.

CO2 Monitoring and Alert System

The MQ135 sensor measures CO2 levels, triggering an LED alarm if concentrations exceed 1000ppm. If levels are within the safe threshold, the system proceeds to measure ambient light intensity using the BH1750 sensor.

Environmental Data Transmission

Atmospheric pressure data from the BMP180 sensor is sent to Blynk virtual pin V8, while light intensity readings are transmitted to V7. A 1-second delay ensures optimal sensor performance and prevents data overload.

Code Structure Overview

The code integrates sensor libraries, Blynk communication protocols, and conditional logic to manage real-time data streaming and threshold-based alerts. Virtual pins facilitate seamless interaction between the ESP32 and the Blynk mobile/web dashboard.

Continuous Operation

The loop ensures persistent data collection and transmission, maintaining real-time monitoring capabilities for environmental parameters. Error handling and connectivity checks are implicitly managed within the Blynk framework.

Applications

This IoT weather station can be used in a variety of real-world applications. It is ideal for indoor air quality monitoring in homes, classrooms, and offices where maintaining a safe and comfortable environment is important. It can be used in laboratories or greenhouses to keep track of environmental conditions affecting plant growth or sensitive experiments. It also serves as a valuable educational tool for students and hobbyists interested in learning about sensors, IoT, and environmental monitoring systems.

Limitations of Blynk (Free Version)

While the Blynk platform provides a powerful and user-friendly interface for IoT projects, its free version has some limitations. Notably, there is a limit on the number of messages or events that can be sent between the device and the cloud, which can restrict frequent data updates. Although Blynk offers advanced widgets such as graphs, historical data views, and automation triggers, many of these features are only available in the paid version. Users on the free plan may need to design around these constraints or explore alternative platforms for extended features like Arduino IoT platform or others.




