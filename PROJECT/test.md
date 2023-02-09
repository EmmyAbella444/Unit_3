
# Unit 3: A Distributed Weather Station for ISAK

# Criteria A: Planning

## Problem definition

## Proposed Solution

## Design Statement
## Success Criteria



# Criteria B: Design



## Flow Diagram



## Test Plan
| Description | Type | Inputs | Outputs | 
| ----------- | ---- | ------ | ------- |




## Record of Tasks
| Task No | Planned Action                                                | Planned Outcome                                                                                                 | Time estimate | Target completion date | Criterion |
|---------|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|---------------|------------------------|-----------|
| 1       | Planning : meeting with client| Start collecting the context of the problem                    | 6min         |   7 february             | A         |




**Table 2** This table shows the record of tasks from the begining of creating this project until the end when the temperature and humidity is received and the analysis is completed. The table consists of the task number, planned action, planned outcome, the time taken to do the task, the date, and the criterion of the task(A,B,C,D).

## Data Storing Method
## 1. Online API Server
The data of temperature and humidity is being stored in an online API server: http://192.168.6.142/readings. Every 5 minutes for 48 hours, the program will send data to the server. As there are 3 sensors, each minute, the server will receive a total of 3 temperature data, and 3 humidity data. The data  will be sent to the server in a particular format. The following is an example of the 6 data sent each time:

```.py
{"value": 22.0, "id": 65010, "datetime": "2022-12-12T19:29:47.212069", "sensor_id": 507}, {"value": 20.0, "id": 65011, "datetime": "2022-12-12T19:29:47.260282", "sensor_id": 510}, {"value": 24.0, "id": 65012, "datetime": "2022-12-12T19:29:47.848937", "sensor_id": 508}, {"value": 20.0, "id": 65013, "datetime": "2022-12-12T19:29:47.918365", "sensor_id": 511}, {"value": 24.0, "id": 65014, "datetime": "2022-12-12T19:29:51.051459", "sensor_id": 509}, {"value": 20.0, "id": 65015, "datetime": "2022-12-12T19:30:02.040595", "sensor_id": 512},
```

Each data tells different information separated by commas, the first element, “value”, tells the value of either temperature(celcius) or humidity(%). The second element “id” shows the id of the data. The third element, “datetime”, tells the date (Year-Month-Day) and the time in hours, minutes, seconds, and milliseconds. The last element tells the sensor id of each of the 3 DHT 11 sensors and each sensor represents either temperature or humidity. We set sensor id 507-509 as the sensors that collect temperature, and the sensors 510-512 as the sensor for humidity.

For example, this data, {"value": 22.0, "id": 65010, "datetime": "2022-12-12T19:29:47.212069", "sensor_id": 507}, shows that the sensor detects temperature as the sensor id is “507”. It also shows that the temperature is 22 degrees Celsius, the id of this sensor is 65010, and the date of the data is 12th December 2022 at 7pm 29 minutes 47 seconds.

<img width="1249" alt="data in server" src="https://user-images.githubusercontent.com/112055062/207038574-7ef259ff-d995-48d2-9738-f786076aecda.png">

**Fig.6** Shows a section of the online API server http://192.168.6.142/readings where the data is being stored in real time every 5 minutes

## 2. Comma Separated Value File (CSV)
The data is not only stored in the online server, but also in a comma separated value file which we created called "Database_inside". The format of the data is organized to show the information of the datetime, the sensor id, and the value of either temperature of humidity from the local location indoors. 

![csv image](https://user-images.githubusercontent.com/112055062/207229610-c8bf7db0-0321-46a7-bd9c-5fd92ef6c091.png)

**Fig.7** Shows a screenshot of the CSV file, Database_inside which contains the information of the datetime, sensor id, and value of temperature and humidity.

# Criteria C: Development

## List of techniques used
1. Functions
2. For loop
3. While loop 
4. Creating graph using Matplotlib[^11]
5. Generating mathematical equations with Numpy [^12]
6. Working remotely with Raspberry pi 4 [^9] using VNC Viewer [^13]
7. Getting data from the sensors using Adafruit DHT Library [^14] 
8. Sending the temperature and humidity from the sensors to an online api server 
9. Validate integer input 
10. Using If statement
11. Creating ASCII art 
12. Using Variables
13. Importing functions from library
14. Print 
15. Using f strings
16. Using Elif statement
17. Using Else statement
18. Logging in to an online api server
19. Reading data from an online api server
20. Using ANSI colors 

## Development
The following are what we developed from the client’s success criteria.
## 1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and outside the house (Remote) for a period of minimum 48 hours.
To provide a visual representation of the temperature and humidity values, we requested the data of the indoor sensor from the server which we have sent real time data every 5 minutes for 48 hours and the outdoor data from the same server. Then, we smoothed the data with a size window of 12 samples to eliminate the outliers for a more accurate result.  After we get the smoothed data from all sensors, we calculate the mean of the data from the 3 sensors.  The data is then merged into one list for each temperature and humidity outside and inside the residence. With the clean data, we use Matplotlib which is a plotting diagram library for Python to plot a graph that shows the relationship between the change in temperature/humidity and the number of samples.

```.py
sensors_temperature = [507, 508, 509]
sensors_humidity = [510, 511, 512]
sensors_outside_temperature = [5]
sensors_outside_humidity = [4] 
values_temperature = []
values_humidity = []
values_outside_temperature = []
values_outside_humidity = []

for s in sensors_outside_humidity:
   # get the sensors_temperature from the server
   value = get_sensor(id=s)
   # smooth the data with a size of 12 samples
   x, smoothed_value = smoothing(data=value[0:288])
   values_outside_humidity.append(smoothed_value)

for s in sensors_outside_temperature:
   # get the sensors_temperature from the server
   value = get_sensor(id=s)
   # smooth the data with a size of 12 samples
   x, smoothed_value = smoothing(data=value[0:288])
   values_outside_temperature.append(smoothed_value)

for s in sensors_temperature:
   # get the sensors_temperature from the server
   value = get_sensor(id=s)
   # smooth the data with a size of 12 samples
   x, smoothed_value = smoothing(data=value[0:288])
   values_temperature.append(smoothed_value)

for s in sensors_humidity:
   # get the sensors_temperature from the server
   value = get_sensor(id=s)
   # smooth the data with a size of 12 samples
   x, smoothed_value = smoothing(data=value[0:288])
   values_humidity.append(smoothed_value)
```
**Code1** Shows the code where the program gets the data from the server with the function that we have written in another library called get_sensor (shown below in **Code2**) and the data is then smoothed with a size of 12 samples using the funciton smoothing (shown below as **Code3**)

```.py
def get_sensor(id: int, url: str = "192.168.6.142/readings") -> list:
   req = requests.get(f'http://{url}')
   data = req.json()
   readings = data["readings"][0]
   out = []
   for r in readings:
       if r["sensor_id"] == id:
           out.append(r["value"])
   return out
```
**Code2** Shows the function that is used to get the data of the temperature and humidity from the sensors

```.py
def smoothing(data:list, size_window:int=12)->list:
   x = [] # horizontal axis
   y = [] # smoothed version vertical axis
   for i in range(0, len(data), size_window):
       segment_mean = sum(data[i:i+size_window])/size_window
       y.append(segment_mean)
       x.append(i)
   x.pop()
   y.pop()
   return x, y
```
**Code3** Shows the function that is used to smooth the window size for a cleaner and more accurate set of data

![Average of sensors for Temperature-Humidity](https://user-images.githubusercontent.com/111758436/207184962-f6440ccb-76d1-4370-9889-da9b2ce8d5f9.png)

**Fig.8** The figure shows the two graphs of the Average of sensors for Temperature and the Average of sensors for Humidity respectively. The first graph which is the Average of sensors for Temperature consists of two components which are the temperature inside(local) and outside(remote). On the x-axis the graph shows the samples per hour for the temperature, and on the y-axis, the graph shows the temperature in Celcius. The second graph, Average of sensors for Humidity, consists of two components which are the temperature inside(local) and outside(remote). The x-axis of the graph whos Samples per hour for Humidity, while the y-axis shows the percent humidity.

## 2.The local variables will be measured using a set of 3 sensors.
To complete the criteria, we have 3 DHT11 sensors that are connected to a Raspberry pi 4 and each measure the temperature and humidity (see figure 7). We use 3 sensors to get more accurate data just in case one of the sensors is inaccurate the other two could lower the error margin. The measuring device is then placed indoors in the same residence as where Peter, the bird, lives, so the temperature, and humidity measurements is the most accurate and reliable. 

![3 sensors](https://user-images.githubusercontent.com/112055062/207089251-25ad59e2-0dcf-42c1-bebd-cbdda18916d2.JPG)

**Fig.9** Shows the Raspberry pi 4 connected to the three DHT11 sensors

![A Distributed Weather Station at R3-14](https://user-images.githubusercontent.com/112055062/207089309-a8355fe6-c88c-4cf6-9b36-85ba4727a892.jpg)
**Fig.10** Shows the location of the sensoring device in an indoor location

## 3. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations.
From the humidity and temperature that we have collected, we have generated a mathematical model for both humidity and temperature for each local and remote location. The mathematical equation generated is below:

![Average of sensors for Temperature Inside](https://user-images.githubusercontent.com/112055062/207272287-25a4ede6-fd58-4d0e-8a7e-b5b604d568f8.png)

**Fig.11** The figure above shows the graph for the average of sensors for the temperature inside (local). The equation for this mathematical model is **y = 0.000123x<sup>2</sup>-0.006x+22.73** which is a quadratic equation.

```.py
values = []

for s in sensors:
    # get the sensors from the server
    value = get_sensor(id=s)
    # smooth the data with a size of 12 samples
    x, smoothed_value = smoothing(data=value[0:490])
    values.append(smoothed_value)

mean_per_hour = []
for i in range(len(values[0])):
    # list comprehension
    data = [values[n][i] for n in range(len(sensors))]
    mean_per_hour.append(sum(data) / len(sensors))

a1, b1, c1 = np.polyfit(x, mean_per_hour, 2)
```
**Code4** The code above shows how NumPy is being used to get the equation for the data. The mathematical model is a quadratic equation as the max degree is x to the power of two. The x-axis of the graph is represented as 'x' and the y-axis is 'mean_per_hour'. a1, b1, c1 represent the coefficient of each element of the equation from x to the power of 2,1,0 respectively.

![Average of sensors for Humidity Inside (1)](https://user-images.githubusercontent.com/112055062/207273226-d467f2c5-3e7a-4c4c-bd66-7cb0b9b17124.png)

**Fig.12** The figure above shows the graph for the Average of Sensors for Humidity Inside(local). The equation for this mathematical model is **y=-0.0000083x<sup>2</sup>+0.003x+19.85** which is a quadratic equation.


```.py
values = []

# Get the data from the server
for s in sensors:
    # get the sensors from the server
    value = get_sensor(id=s)
    # smooth the data with a size of 12 samples
    x, smoothed_value = smoothing(data=value[0:490])
    values.append(smoothed_value)


mean_per_hour = []
for i in range(len(values[0])):
    # list comprehension
    data = [values[n][i] for n in range(len(sensors))]
    mean_per_hour.append(sum(data) / len(sensors))

a1, b1, c1 = np.polyfit(x, mean_per_hour, 2)
```
**Code5** The code above shows how the mathematical equation is being calculated by using the library NumPy. The x and y axis of the graph is x, and mean_per_hour respectively. The mathematical model is a quadratic equation with coefficients: a1,b1,c1. With the coefficients, the equation can be found. 

![Temperature outside - line - equation](https://user-images.githubusercontent.com/112055062/207268274-3796c0f0-3e9d-4f4d-967b-4cb34e4ea383.png)

**Fig.13** The figure above shows the graph for the Temperature Outside(remote) to the samples per hour. The equation for this mathematical model is a polynomial equation which is **y=-0.0000000017x<sup>3</sup>-000004.5x<sup>2</sup>-0.0007x+25.34**.

```.py
for i in range(len(Sensor_5)):
    # list comprehension
    data = [Sensor_5[i] for n in range(len(Sensor_5))]
    mean_per_hour_outside_h.append(sum(data) / len(Sensor_5))

for i in range(0, len(mean_per_hour_outside_h)):
    sample.append(i)

y = []
a1, b1, c1, d1 = np.polyfit(sample, mean_per_hour_outside_h, 3)
print(a1, b1, c1, d1)
```
**Code6** The code above shows how we used the NumPy library to get the equation. We generated the 2 lists for each axis in which the x-axis is 'sample' and the y-axis is 'mean_per_hour_outside_h. We then use NumPy to look for the coefficient of x to the power of 3,2,1,0 by naming a1,b1,c1,d1 respectively. The mathematical model is polynomial with degree 3, so we can find the equation from the 2 lists and the information that the model is a third degree polynomial.

![Humidity outside - line - equation](https://user-images.githubusercontent.com/112055062/207268303-b12d46f3-2a0e-40fd-b164-03ea6017dbe3.png)
**Fig.14** The figure above shows the graph for the humidity outside(remote) to the samples per hour. The equation for this mathematical model is a polynomial equation which is **y=-0.0000000032x<sup>3</sup>+0.0001x<sup>2</sup>-0.002x+23.72**

```.py
sample = []  # empty list

mean_per_hour_outside_h = []

for i in range(len(Sensor_4)):
    # list comprehension
    data = [Sensor_4[i] for n in range(len(Sensor_4))]
    mean_per_hour_outside_h.append(sum(data) / len(Sensor_4))

for i in range(0, len(mean_per_hour_outside_h)):
    sample.append(i)

#Sensor_4 = Sensor_4[]
y = []
a1, b1, c1, d1 = np.polyfit(sample, mean_per_hour_outside_h, 3)
```
**Code7** The code above shows how the mathematical model for the humidity to the sample is by using NumPy. The two lists of x and y axis are sample and mean_per_hour_outside_h. The mathematical model is a 3rd degree polynomial. The equation is given by giving out the coefficients a1, b1, c1, d1 which forms the equation. 

## 4. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.

To provide a comparative analysis, we created a graph where we compare the temperature and humidity of the inside(local) and outside(remote) location in the same graph next to each other. From **Fig.15**, we are able to see two graphs in which the first one shows the average temperature with the samples. The red line shows the temperature for outside(remote) location, and the blue line presents the temperature for inside(local) location. The graph shows that there is a point where the temperature matches at approximately 6.5 samples, then it diverges, and gets closer to eachother again. In the second graph, we are able to see the average humidity which, again, the blue line represents the inside(local) location, and the red line represents the outside(remote) location. The graph shows that the difference between the two locations are greater then converges closer to eachother and starts diverging again.

![Average of sensors for Temperature-Humidity (1)](https://user-images.githubusercontent.com/112055062/207328018-8a99f681-672c-467f-b67f-f2e9d0c14add.png)

**Fig.15** The figure shows the two graphs of average of sensors for temperature and humidity with the comparison between the two sensoring locations: inside(local) and outside(remote)

```.py
mean_per_hour_t = []
mean_per_hour_h = []
mean_per_hour_outside_h = []
mean_per_hour_outside_t = []
x_t = []
x_h = []
x_t_o = []
x_h_o = []
for i in range(len(values_temperature[0])):
    # list comprehension
    data = [values_temperature[n][i] for n in range(len(sensors_temperature))]
    mean_per_hour_t.append(sum(data) / len(sensors_temperature))
    x_t.append(i)

for i in range(len(values_humidity[0])):
    # list comprehension
    data = [values_humidity[n][i] for n in range(len(sensors_humidity))]
    mean_per_hour_h.append(sum(data) / len(sensors_humidity))
    x_h.append(i)

for i in range(len(values_outside_temperature[0])):
    # list comprehension
    data = [values_outside_temperature[n][i] for n in range(len(sensors_outside_temperature))]
    mean_per_hour_outside_t.append(sum(data) / len(sensors_outside_temperature))
    x_t_o.append(i)

for i in range(len(values_outside_humidity[0])):
    # list comprehension
    data = [values_outside_humidity[n][i] for n in range(len(sensors_outside_humidity))]
    mean_per_hour_outside_h.append(sum(data) / len(sensors_outside_humidity))
    x_h_o.append(i)

# plot the mean of the sensors
a1, b1, c1, d1 = np.polyfit(x_t, mean_per_hour_t, 3)
print(a1, b1, c1, d1)
polynomial_model_t = []
for t in range(0, len(values_temperature[0])):
    polynomial_model_t.append(a1*(t**3) + b1*(t**2) + c1*t + d1)

a2, b2, c2, d2 = np.polyfit(x_h, mean_per_hour_h, 3)
print(a2, b2, c2, d2)
polynomial_model_h = []
for t in range(0, len(values_humidity[0])):
    polynomial_model_h.append(a2*(t**3) + b2*(t**2) + c2*t + d2)

a3, b3, c3, d3 = np.polyfit(x_t_o, mean_per_hour_outside_t, 3)
print(a3, b3, c3, d3)
polynomial_model_outside_t = []
for t in range(0, len(values_outside_temperature[0])):
    polynomial_model_outside_t.append(a3*(t**3) + b3*(t**2) + c3*t + d3)

a4, b4, c4, d4 = np.polyfit(x_h_o, mean_per_hour_outside_h, 3)
print(a4, b4, c4, d4)
polynomial_model_outside_h = []
for t in range(0, len(values_outside_humidity[0])):
    polynomial_model_outside_h.append(a4*(t**3) + b4*(t**2) + c4*t + d4)

ax = plt.axes()
ax.set_facecolor("lightsteelblue") # Choosing the background color
plt.subplot(3, 1, 1)
plt.title("Average of sensors for Temperature\n11 December 2022 10:39 - 13 December 2022 10:39 AM")
plt.grid(True, color='dimgray')
plt.plot(x_t, polynomial_model_t, color='#3264a8')
plt.plot(x_t_o, polynomial_model_outside_t, color='#eb4034')
plt.legend(['Inside', 'Outside']) # adding labels of colors to the graph
plt.xlabel("Samples per hour for Temperature")
plt.ylabel("Celsius")
plt.tick_params('x', labelbottom=True)
plt.subplot(3, 1, 3)
plt.title("Average of sensors for Humidity\n11 December 2022 10:39 - 13 December 2022 10:39 AM")
plt.grid(True, color='dimgray')
plt.plot(x_h, polynomial_model_h, color='#3290a8')
plt.plot(x_h_o, polynomial_model_outside_h, color='#eb4034')
plt.legend(['Inside', 'Outside']) # adding labels of colors to the graph
plt.xlabel("Samples per hour for Humidity")
plt.ylabel("%")
plt.tick_params('x', labelbottom=True)

plt.show()
```
**Code8** The code above shows the code of the two graphs which is used to compare the data of the temperature and humidity outside(remote) and inside(local) locations.

## 5. The Local samples are posted to the remote server.
To fulfill this criteria, we stored the data acquired with the DHT11 sensors located indoors on an online API server http://192.168.6.142/readings. The data is being posted to the server in real time every 5 minutes. 

```.py
import Adafruit_DHT
import time
import requests
from datetime import datetime

DHT_SENSOR = Adafruit_DHT.DHT11

def data_reader(pin_number: int)->str:
    humidity, temperature = Adafruit_DHT.read_retry(DHT_SENSOR, pin_number)
    while temperature == 0 and humidity == 0:
        humidity, temperature = Adafruit_DHT.read_retry(DHT_SENSOR, pin_number)
    return temperature, humidity

while True:
    user = {"username": "test", 'password': 'test1234'}
    req = requests.post('http://192.168.6.142/login', json=user)
    req = req.json()
    access_token = req["access_token"]
    auth = {"Authorization": f"Bearer {access_token}"}
    data = []
    for i in range(2, 5):
        data = data_reader(i)
        print(data)
        new_record_temperature = {"datetime": datetime.isoformat(datetime.now()), "sensor_id": (i +505), "value": data[0]}
        r_temperature = requests.post('http://192.168.6.142/reading/new', json=new_record_temperature, headers=auth)
        new_record_humidity = {"datetime": datetime.isoformat(datetime.now()), "sensor_id": (i + 508), "value": data[1]}
        r_humidity = requests.post('http://192.168.6.142/reading/new', json=new_record_humidity, headers=auth)
        print(r_temperature.json())
        print(r_humidity.json())
    time.sleep(300)
```

**Code9** This is the code that is used to send the temperature and humidity which is being sent to the online API server http://192.168.6.142/readings every 5 minutes. We used the library Adafruit_DHT which is used with the DHT11 sensors. Then, we created a function called data_reader to return the temperature and humidity. The data is then sent to the server. To send the data to the server, we also need to have authorization using access token with a username and password. 


<img width="1249" alt="data in server" src="https://user-images.githubusercontent.com/112055062/207038574-7ef259ff-d995-48d2-9738-f786076aecda.png">

**Fig.16** Shows a section of the online API server http://192.168.6.142/readings where the data is being stored in real time every 5 minutes

```.py
import requests

req = requests.get('http://192.168.6.142/readings')
data = req.json()
readings = data['readings'][0]

for sample in readings:
    if sample['sensor_id'] == 507:
        with open("Database_inside", "a") as file:
            file.write(f"{sample['datetime']},{sample['sensor_id']},{sample['value']}\n")
    elif sample['sensor_id'] == 508:
        with open("Database_inside", "a") as file:
            file.write(f"{sample['datetime']},{sample['sensor_id']},{sample['value']}\n")
    elif sample['sensor_id'] == 509:
        with open("Database_inside", "a") as file:
            file.write(f"{sample['datetime']},{sample['sensor_id']},{sample['value']}\n")
    elif sample['sensor_id'] == 510:
        with open("Database_inside", "a") as file:
            file.write(f"{sample['datetime']},{sample['sensor_id']},{sample['value']}\n")
    elif sample['sensor_id'] == 511:
        with open("Database_inside", "a") as file:
            file.write(f"{sample['datetime']},{sample['sensor_id']},{sample['value']}\n")
    elif sample['sensor_id'] == 512:
        with open("Database_inside", "a") as file:
            file.write(f"{sample['datetime']},{sample['sensor_id']},{sample['value']}\n")
```
**Code10** Shows the code of the data written into the CSV file

![csv image](https://user-images.githubusercontent.com/112055062/207231324-5e2b936e-f8dd-432e-beba-b46cc575bb10.png)
**Fig.17** Shows the screenshot of the CSV file Database_inside 

## 6.Create a prediction the subsequent 12 hours for both temperature and humidity.

To fulfill criteria 6, we predicted the temperature and humidity of the next subsequent 12 hours by looking at the pattern of the previous data that we have collected. The data has a repeating pattern in each day, which we can use to find a mathematical equation that will work for the next 12 hours as well. Once we got the mathematical equation, we generate a graph which could be the prediction of the next subsequent data.

![Predicted data for 12 hours - temperature inside](https://user-images.githubusercontent.com/112055062/207365447-3278203d-3c72-477e-ad76-e1c798047789.png)

**Fig.18** Presents the predicted data for the next subsequent 12 hours for the Temperature of the inside(local) location

![Predicted data for 12 hours - humidity inside](https://user-images.githubusercontent.com/112055062/207365771-a97e2502-c258-4516-815b-1fde1975a4df.png)

**Fig.19** Presents the predicted data for the next subsequent 12 hours for the Humidity of the inside(local) location

## 7. A poster summarizing the visual representations, model and analysis is created. The poster includes a recommendation about healthy levels for Temperature and Humidity.

![Cartaz  para Imprimir Comemoração Dia do Garçom Cinza e Preto ](https://user-images.githubusercontent.com/112055062/207363062-9835cc8f-9d8c-46a9-9cdc-f29c02606673.jpg)

![Cartaz  para Imprimir Comemoração Dia do Garçom Cinza e Preto  (1)](https://user-images.githubusercontent.com/112055062/207367006-c426251d-0a9e-4874-8b15-0e276ac9737c.png)

![Cartaz  para Imprimir Comemoração Dia do Garçom Cinza e Preto  (2)](https://user-images.githubusercontent.com/112055062/207367160-04572a61-ad91-479a-b86a-e27c9197e396.png)

**Fig.20 & 21** Shows the poster which fulfills criteria 7, summarizing the visual representations, model and analysis is created. The poster includes a recommendation about healthy levels for Temperature and Humidity


# Criteria D: Functionality
## A 7 min video demonstrating the proposed solution with narration
https://drive.google.com/drive/folders/1lezKfb5EglCE-TGsE2RxsHOTJydVnSUX

[^1]: Industries, Adafruit. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog RSS, https://www.adafruit.com/product/386. 
[^2]: Nelson, Carter. “Modern Replacements for DHT11 and dht22 Sensors.” Adafruit Learning System, https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives.   
[^3]:“How to Connect dht11 Sensor with Arduino Uno.” Arduino Project Hub, https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239.  
[^4]:Team, The Arduino. “What Is Arduino?: Arduino Documentation.” Arduino Documentation | Arduino Documentation, https://docs.arduino.cc/learn/starting-guide/whats-arduino.  
[^5]:Tino. “Tino/PyFirmata: Python Interface for the Firmata (Http://Firmata.org/) Protocol. It Is Compliant with Firmata 2.1. Any Help with Updating to 2.2 Is Welcome. the Capability Query Is Implemented, but the Pin State Query Feature Not Yet.” GitHub, https://github.com/tino/pyFirmata. 
[^6]:Python Geeks. “Advantages of Python: Disadvantages of Python.” Python Geeks, 26 June 2021, https://pythongeeks.org/advantages-disadvantages-of-python/. 
[^7]: Real Python. “Python vs C++: Selecting the Right Tool for the Job.” Real Python, Real Python, 19 June 2021, https://realpython.com/python-vs-cpp/#memory-management. 
[^8]: Ornithology, British Trust for. “Tree Sparrow.” BTO, 4 Sept. 2019, https://www.bto.org/our-science/projects/gbw/gardens-wildlife/garden-birds/a-z-garden-birds/tree-sparrow. 
[^9]:Raspberry Pi. “Raspberry Pi 4 Model B.” Raspberry Pi, https://www.raspberrypi.com/products/raspberry-pi-4-model-b/. 
[^10]:“Dht11–Temperature and Humidity Sensor.” Components101, https://components101.com/sensors/dht11-temperature-sensor. 
[^11]: “Visualization with Python.” Matplotlib, https://matplotlib.org/. 
[^12]: NumPy, https://numpy.org/. 
[^13]:“Download VNC Viewer: VNC® Connect.” RealVNC®, 9 Dec. 2022, https://www.realvnc.com/en/connect/download/viewer/. 
[^14]: Adafruit. “Adafruit/ADAFRUIT_PYTHON_DHT: Python Library to Read the DHT Series of Humidity and Temperature Sensors on a Raspberry Pi or Beaglebone Black.” GitHub, https://github.com/adafruit/Adafruit_Python_DHT. 

