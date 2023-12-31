# DroneMobile Home Assistant Integration

## Disclaimer

The code here is based off of an unsupported API from
[DroneMobile](https://www.dronemobile.com/) and is subject to change without
notice. The authors claim no responsibility for damages to your vehicle
by use of the code within.

## Install
Place the "drone_mobile" folder in the "custom_components" folder of your Home Assistant instance. This essentially installs the integration for Home Assistant to use. You may need to restart your Home Assistant instance to get Home Assistant to see that a new integration has been installed. Once the integration is installed go to your integrations (By clicking "Settings", then "Devices & Services", then clicking on the "Add Integration" button, and searching for the "DroneMobile" Integration) and follow the configuration options to specify the below:
- Username (DroneMobile - This should be an email address)
- Password (DroneMobile)
- Units (Imperial or Metric. The default is Imperial [MPH, miles, farenheit])
- Update Interval (In Minutes)
- Whether or not you want to send lock commands regardless of what state they are already reporting to be in (default is unchecked, or false)

## Usage
Your car must have a DroneMobile Remote Start system installed (from Firstech, Compustar, etc.) and you must be subscribed to a DroneMobile Plan.

###
Click on options and choose imperial or metric to display in km/miles. Takes effect on next restart of home assistant. Default is Imperial.

### Device Status Refresh
I have added a service to poll the DroneMobile device (the car) for updates, due to the battery drain and data limits on the amount of times you can call this, this service call will need to be called manually or in your own automations. The service to be called is "refresh_device_status" and can be accessed in home assistant using "drone_mobile.refresh_device_status_[Vehicle Name With Spaces Replaced By Underscores]" with no parameters.

### Dump Device Data
This service allows simple debugging to be able to dump the currently stored json payload for a vehicle/device. This will output a json file to your Home Assistant config folder. You can then move it wherever you want and open it with a text editor as needed. Access it in Home Assistant using "drone_mobile.dump_device_data_[Vehicle Name With Spaces Replaced By Underscores]" with no parameters.

### Clear Temporary Token
If you are experiencing any sign in issues, please trying clearing your tokens using the "clear_temp_token" service call. Access it in home assistant using "drone_mobile.clear_temp_token" with no parameters.

### Replace Token
If you need to replace the stored token, use the the "replace_token" service call. Access it in home assistant using "drone_mobile.replace_token" with no parameters. WARNING: This method will delete your token file located in your home assistant config directory before re-authorizing and replacing that file. If something goes wrong in this call, that file will be deleted and if it isn't backed up first, you will have to delete the integration in home assistant and re-add it in order to re-authenticate. Please only use this service call if you know what you're doing and have backed up your token file first!

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
