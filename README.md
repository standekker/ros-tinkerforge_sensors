### Tinkerforge Sensors

Mit diesem Paket können Tinkerforge Sensoren im ROS genutzt werden. Auch Sensoren des gleichen Typs werden erkannt. Durch Nutzung des "robusten Ansatzes" ist die Angabe von UIDs nicht notwendig. Die Sensorwerte werden in entsprechende ROS-Messages über automatisch generierte Topics verbreitet. Unter Verwendung eines Launch-Files können Topic per UID manuell festgelegt werden.

This package allows you to use TinkerForge sensors with ROS. Sensors of same type will be supported. Package used the "Rugged Approach", so it's not necessary to configure the sensor UIDs. Sensor values will be published over automatic generated topics with typical ROS message types. With a Launchfile a topic can be bind on an UID.

##### Hinweise / Hints

Es wird nicht empfohlen zwei Instanzen des Programmes zu starten (z.B. zwei Master Bricks), da sich die Sensor Topics sonst überlagern.

It's not recommended to run more than one instance of the program, because different sensors of same type will be published into one topic.

### Unterstütze Geräte / Supported Devices

Bricklets:

* Ambient Light => sensor_msgs/Illuminance
* Ambient Light 2.0 => sensor_msgs/Illuminance
* Distance IR => sensor_msgs/Range
* Distance US => sensor_msgs/Range
* GPS (Test) => sensor_msgs/NavSatFix
* Motion Detector (Test)
* Temperature => sensor_msgs/Temperature

Bricks:

* IMU => sensor_msgs/Imu
* IMU 2.0 => sensor_msgs/Imu

### Installation

Herunterladen des Git-Repository in das catkin workspace Verzeichnis.

clone the git repository to catkin workspace.

`git clone https://github.com/gus484/ros-tinkerforge_sensors`

Workspace kompilieren / build workspace

`catkin_make`

# Example
To start using the TinkerForge sensors node, use the example launch file:
`roslaunch tinkerforge_sensors tinkerforge_sensors.launch`

# Nodes

## tinkerforge_sensors
The tinkerforge_sensors node connects to the brickd application and publishes the data on the `/tfsensors/` topic.

### Subscribed topics

None.

### Published topics

tfsensors/imuN([sensor_msgs/Imu Message](http://docs.ros.org/melodic/api/sensor_msgs/html/msg/Imu.html))
  IMU message, in which N starts at 1 and counts up, if multiple imu's are connected.

tfsensors/magneticN([sensor_msgs/MagneticField Message](http://docs.ros.org/melodic/api/sensor_msgs/html/msg/MagneticField.html))
  IMU message, in which N starts at 1 and counts up, if multiple imu's are connected.

### Services

None.

### Parameters

~frame_id (string, default: imu_link)
  The frame ID to set in outgoing messages.
~linear_acceleration_stddev (double, default: 0.1)
  Square root of the linear_acceleration_covariance diagonal elements in m/s^2. Overrides any values reported by the sensor.
~angular_velocity_stddev (double, default: 0.1)
  Square root of the angular_velocity_covariance diagonal elements in rad/s. Overrides any values reported by the sensor.
~magnetic_field_stddev (double, default: 0.1)
  Square root of the magnetic_field_covariance diagonal elements in Tesla. Overrides any values reported by the sensor.
~orientation_stddev (double, default: 0.1)
  Square root of the orientation_covariance diagonal elements in rad. Overrides any values reported by the sensor.
~port (int, default: 4223)
  Port of the tinkerforge brickv server.
~ip (string, default: localhost)
  Ip of the tinkerforge brickv server.
~rate (int, default: 100)
  Sample frequency of the sensor in Hz.

### Required tf Transforms

None.

### Provided tf Transform

None.


# ToDo

* mehr Sensoren unterstützen / suport more sensors
* Kalibrierung für Distance US Sensor / calibration for Distance US sensor
* mehr Konfigurationsmöglichkeiten / more config options
* Verwaltung mehrerer Master / handle more than one master
