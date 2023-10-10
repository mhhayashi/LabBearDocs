Launching the app creates files in the directory that the app is run. 

In the config directory there are three important items:
1. hardware_device.yml : list of devices and their constructor arguments
2. drivers : folder for python drivers
3. RemoteDevice.py : The object used to access devices remotely

The hardware device list is already populated with examples. Example drivers are in the folder. 

To use:

Put RemoteDevice.py into the same folder as the experiment script.

```
from RemoteDevice import *

a = RemoteDevice("Mock1", "127.0.0.1:5000")

pos = a.laser_on()
```
