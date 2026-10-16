# Limitations

## No added security

LabBear does NOT provide any security. It has no authentication or encryption, and it assumes that the laboratory network is secure. Anyone who can reach a LabBear server can use it and the devices connected to it.

- Run LabBear only on a lab network that is isolated from the internet and from untrusted users. A properly configured router / firewall should block all connections from unauthorized devices. Ensure that only authorized devices are on the network.
- Do not run LabBear in debug mode or expose it beyond the lab network.
- Only install drivers that you trust. Drivers run with the permissions of the user running LabBear.
- LabBear uses Flask's built-in server, which is intended for small, trusted setups.

## No added safety

LabBear does NOT prevent you from destroying hardware devices or from injuring people. It does not add interlocks, confirmations or limits of its own, and devices can be controlled remotely. It is the responsibility of the driver to prevent misuse. However, even the strictest restrictions may not be able to prevent purposeful destruction of hardware devices.

You are responsible for the safety of personnel and equipment, including laser safety. Keep independent safety controls that do not depend on LabBear.

## Reservations are advisory

Reserving a device marks it as in use, but does not stop other users from controlling it.

## Network

- The lab should have its own network (devices connected to a lab router).
- Parts of the dashboard load scripts from the internet, so they may not display on a network without internet access. Controlling devices from scripts is not affected.
- Looking up devices on other computers can be slow or stall if a listed computer is unreachable. See [Multi-host usage](MULTIHOST.md).
