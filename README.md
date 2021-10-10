# pytemi
Control temi using Python scripts over MQTT.


## Prerequisites
* [Python 3](https://www.python.org/downloads/)
* [Connect app](https://github.com/hapi-robo/connect/releases) installed on temi
* MQTT broker. Free brokers for testing:
	* [Eclipse](http://test.mosquitto.org/)
	* [Mosquitto](http://mqtt.eclipse.org)
	* [HiveMQ](http://broker.hivemq.com)


## Setup
Clone this repository and install all dependencies with pip:
```
pip3 install -r requirements.txt
```

For Linux users, there's a script that will create a Python virtual environment (assuming it's installed) and install all dependencies:
```
./setup.sh
```


## Usage
Make sure the robot is connected to an MQTT broker via the [Connect app](https://github.com/hapi-robo/connect/releases).

Edit the `sample.py` script and adjust the `parameters` appropriately, then run:
```
python3 sample.py
```


## Sample Script  

Notice:   
- Please change MQTT_HOST to your own server to make the connection stable.  
- Please change TEMI_SERIAL to your own numbers. You can find it behind the robot Temi.  

```
import pytemi as temi
import time  

MQTT_HOST = "test.mosquitto.org"
MQTT_PORT = 1883
TEMI_SERIAL = "01234567890"

# connect to the MQTT broker
mqtt_client = temi.connect(MQTT_HOST, MQTT_PORT)

# create robot object
robot = temi.Robot(mqtt_client, TEMI_SERIAL)

# concern for the delay while using test server  
time.sleep(5)  

# command the robot to speak
robot.tts("Going to the Entrance")

# command the robot to go to a saved location
robot.goto("entrance")
```  
