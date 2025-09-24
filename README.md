# Environmental-Monitor
(In progress)

Following my long term desire to join the world of IoT and Embedded systems, I decided to start developing a project of my own, on which I will progressively add features, prioritizing learning over functionality and real-world application. Main goal of the project is to create a closed-loop system which will combine data gathering through sensors, transmission of the data over different kind of networks, data visualization, 3D printing and a feedback system to close the loop.

### Quick Overview
Two different kinds of sensors measure temperature and humidity and send the data to an ESP32 microcontroller. Environmental Data is then sent over WiFi to Adafruit IO cloud platform, where it is presented in a Dashboard, and over I2C to an OLED display. When measured temperature is high enough, a fan will start blowing for 20 seconnd towards the sensor on which the temperature was measured as high. The fan and the sensors are all mounted on a 3D printed "platform" in order to grant fixed distance and positioning. Data pre fan activation and post fan activation is compared to get further insights

### Items
Microcontroller: ESP32
Sensors: 1x DHT11 & 1x DHT22
Fan: Composed of a 3d printed propeller on a DC motor, all together mounted on a servo motor to rotate the fan towards the hot sensor.

### Project Stages

Single Sensor
![single sensor no antenna](https://github.com/user-attachments/assets/4c5870e0-ca89-4dc7-b5b9-aba93adcc4c6)
<img src="[https://github.com/favicon.ico](https://github.com/user-attachments/assets/4c5870e0-ca89-4dc7-b5b9-aba93adcc4c6)" width="48">

First a single sensor is unit to test the sensor and set up the display and WiFi network. As it can be seen in the image, measurement is displayed on the OLED but as per the below image, network cannot be attached.
![WiFi Not available](https://github.com/user-attachments/assets/e12889e7-596c-4318-831a-4ce3c29b245f)

To fix the above, a 3dBi antenna is added to the ESP32 built in antenna port to enhance signal reception. As a result, network is attached and measurements are pubished to Adafruit Dashboard.

![single sensor antenna](https://github.com/user-attachments/assets/3e435d11-b2f6-49b7-a3f3-610b3dcb3a9f)

![WiFi connected](https://github.com/user-attachments/assets/cad5603c-155f-4d19-9a3e-11eb47092c44)

<img width="1164" height="675" alt="Dashboard after publishing" src="https://github.com/user-attachments/assets/a6669d63-2fd7-4b16-ac55-a1f2f466c69c" />


After succesfull network connection and data transmission, a second sensor is integrated

![2 sensors front](https://github.com/user-attachments/assets/abd6d0b5-fe31-477a-9f2a-426a4943f7ac)

![double sensor measurement](https://github.com/user-attachments/assets/a9417145-81ec-41c5-be5f-e7fd59e07f4a)

It can be seen below that DHT11 measurement took some time to converge with DHT22 as it started at 40 degrees falling to 30 in less than 2 minutes. This behaviour should be taken into consideration in the design of our system.

After sensors and network are properly set up, the fan module is integrated in our system. The fan along with the sensors are mounted on a 3D platform as per below:

![complete setup front](https://github.com/user-attachments/assets/0854c37e-c473-4463-b367-edc62a1e0735)





