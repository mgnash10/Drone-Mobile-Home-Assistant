# DroneMobile Home Assistant Integration

## Disclaimer

The code here is based off of an unsupported API from
[DroneMobile](https://www.dronemobile.com/) and is subject to change without
notice. The authors claim no responsibility for damages to your vehicle
by use of the code within.

## Install
Place the "drone_mobile" folder in the "custom_components" folder of your Home Assistant instance. Once the integration is installed go to your integrations and follow the configuration options to specify the below:
- Username (DroneMobile - This should be an email address)
- Password (DroneMobile)
- Units (Imperial or Metric. The default is Imperial [MPH, miles, farenheit])
- Update Interval (In Minutes)

## Usage
Your car must have a DroneMobile Remote Start system installed (from Firstech, Compustar, etc.) and you must be subscribed to a DroneMobile Plan.

###
Click on options and choose imperial or metric to display in km/miles. Takes effect on next restart of home assistant. Default is Imperial.

### Device Status Refresh
I have added a service to poll the DroneMobile device (the car) for updates, due to the battery drain and data limits on the amount of times you can call this, this service call will need to be called manually or in your own automations. The service to be called is "refresh_device_status" and can be accessed in home assistant using "drone_mobile.refresh_device_status" with no parameters.

### Clear Tokens
If you are experiencing any sign in issues, please trying clearing your tokens using the "clear_tokens" service call.


## Currently Working

Status Sensors:
- Odometer
- Last known GPS Coordinates/Map
- Temperature Status
- Battery Status
- Ignition Status
- Alarm Status
- Door Status
- Trunk Status
- Hood Status
- Last Car Refresh status
- Car Tracker

Triggers:
- Remote Start
- Lock/Unlock (This also counts as arming the alarm)
- Trunk Trigger
- Panic Trigger
- Aux1 Trigger
- Aux2 Trigger