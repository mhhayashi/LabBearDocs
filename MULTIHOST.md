# Multi-host usage

Use more than one lab PC when devices are connected to different computers. Each PC runs its own LabBear server for the devices plugged into it. A script on any PC can then ask for a device by name without knowing which PC it is on.

Read [Limitations](LIMITATIONS.md) first: all servers must be on the isolated lab network.

## Setup

1. Install and configure LabBear on each PC that has devices (see [Install](INSTALL.md)). Each PC has its own `hardware_config.yml` listing only its own devices.
2. Give every device a **unique name** across all PCs. If two PCs list the same name, the first one found is used.
3. On each PC, edit `peers.txt` in the instance folder. List the other LabBear servers, one `host:port` per line, with no `http://`:
   ```
   192.168.1.21:5000
   192.168.1.22:5000
   ```
   Use the lab network addresses. Blank lines are ignored (version 0.1.3 and later; older versions need exactly one host and no trailing newline).
4. Start each server so the other PCs can reach it, using the PC's lab network address:
   ```
   flask --app LabBearApp run --host 192.168.1.20 --port 5000
   ```
   Do not use `--debug`.
5. Allow the port (default 5000) through the PC's firewall for the lab network only.

## Using a device from a script

Put `RemoteDevice.py` next to your script. Give any one server's address, not necessarily the PC that has the device:

```
from RemoteDevice import *

laser = RemoteDevice("Mock1", "192.168.1.20:5000")
laser.laser_on()
```

`RemoteDevice` asks that server where "Mock1" lives. If the device is on that PC it is used directly. Otherwise the server asks each host in its own `peers.txt`, and your script then connects straight to the host that has the device.

To mark a device as in use while your script runs, add `True`:

```
laser = RemoteDevice("Mock1", "192.168.1.20:5000", True)
```

The reservation is released when the script exits. It is advisory only (see [Limitations](LIMITATIONS.md)).

## Things to know

- Lookup is one level deep. A server only checks the hosts in its own `peers.txt`, and does not ask the peers' peers. Lists are not shared, so if PC A lists PC B, B does not automatically list A.
- Each lookup contacts peers one at a time with no timeout. If a listed PC is off or unreachable, remove it from `peers.txt` or lookups through that server may hang.
- If you get "Device not found", check the device name (case matters), that the PC with the device is running and connected to it on the dashboard, and that the address is in the `peers.txt` of the server you asked.
- Large data (for example streaming a histogram or event file) is not designed to pass through RPC. Keep bulk data collection on the PC with the device.
