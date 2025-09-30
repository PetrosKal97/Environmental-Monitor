# Environmental-Monitor
(In progress)

Following my long term desire to join the world of IoT and Embedded systems, I decided to start developing a project of my own, on which I will progressively add features, prioritizing learning over functionality and real-world application. Main goal of the project is to create a closed-loop system which will combine data gathering through sensors, transmission of the data over different kind of networks, data visualization, 3D printing and a feedback system to close the loop.

### Quick Overview


https://github.com/user-attachments/assets/94cf2de9-a663-4269-af8a-05bd08b0c5ef


The system gathers environmental data from two sensors (DHT11, DHT22) for temperature and humidity, sends it to the cloud, and activates a fan as a feedback mechanism. Data is both visualized on an OLED and on Adafruit IO dashboards.
When measured temperature is high enough, a fan will start blowing towards the sensor on which the temperature was measured as high. The fan and the sensors are all mounted on a custom 3D printed mounting platform in order to grant fixed distance and positioning.

###Technologies used:

ESP32, DHT11/DHT22, OLED, MQTT, Adafruit IO, 3D printing, servo motor, DC motor.


### Project Phases

Single Sensor

<img width="378" height="504" alt="single sensor no antenna" src="https://github.com/user-attachments/assets/a4ddc9c4-0a85-4569-b9e0-fe69a6cfc4b7" />


First a single sensor is unit to test the sensor and set up the display and WiFi network. As it can be seen in the image, measurement is displayed on the OLED but as per the below image, network cannot be attached.
<img width="778" height="378" alt="WiFi Not available" src="https://github.com/user-attachments/assets/91c8ccf6-3895-4f8c-9216-7b70b748b2d8" />



To fix the above, a 3dBi antenna is added to the ESP32 built in antenna port to enhance signal reception.

<img width="378" height="504" alt="single sensor antenna" src="https://github.com/user-attachments/assets/5b444c15-4eb1-436a-ad70-b825c1381e99" />


 As a result, network is attached and measurements are pubished to Adafruit Dashboard.
 

<img width="800" height="400" alt="WiFi connected" src="https://github.com/user-attachments/assets/8686dc0d-6bc9-44c7-bea5-b6704c4b77be" />



<img width="600" height="350" alt="Dashboard after publishing" src="https://github.com/user-attachments/assets/a6669d63-2fd7-4b16-ac55-a1f2f466c69c" />


After succesfull network connection and data transmission, a second sensor is integrated

<img width="378" height="504" alt="2 sensors front" src="https://github.com/user-attachments/assets/e65c9c29-fc01-48fc-8860-b4a8ba7adae7" />


<img width="600" height="300" alt="second sensor conveying slowly after position sub" src="https://github.com/user-attachments/assets/c13071a5-e0ef-43d4-bf4d-3c47231e68d3" />



It can be seen above that DHT11 measurement took some time to converge with DHT22 as it started at 40 degrees falling to 30 in less than 2 minutes. This behaviour should be taken into consideration in the design of our system.

After sensors and network are properly set up, the fan module is integrated in our system. The fan along with the sensors are mounted on a 3D platform as per below:

<img width="600" height="800" alt="complete setup front" src="https://github.com/user-attachments/assets/f7e91cc2-9132-45d1-94c5-0fd7b65c0c9b" />


Depending on the measurement and a pre-defined threshold, the fan might move either to one of the sensors or to sweep between both of them. 


Focusing on one sensor at a time


https://github.com/user-attachments/assets/43aca7bf-3518-4d37-9609-6dea0f6f62f6

Sweep between both sensors


https://github.com/user-attachments/assets/3cfe72b2-d20f-42ec-908f-6904dddb75f5


### Current Challenges

As the sensing element of both sensors is inside the plastic cover, the measured temperature is very slightly affected by the fan blow, as the only the plastic surface is cooled down, the air remains at the same temperature (air circulating). In order to drop the measured temperature and cool down a sensor, colder air should be blown to the sensor. For our experiment maybe an ice cube could be used between the fan and the sensor to cool the blown air.

### Next Steps

An interesting way to move on with our project would be to connect the system to External Power such as Batteries/Solar Panel. Take longer measurements (2-3) days and in addition to environmental conditions, also publish to a Dashboards other insights such as how many times the fan turned on, how long did it stay on, what was the average effect of the fan on each sensor and others. Depending on the collected data, different analysis can be applied and different ways to move on the project might arise.
