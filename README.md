# Voicemeeter Node.js API

![NPM](https://img.shields.io/npm/v/voicemeeter-rmc?style=for-the-badge)
![Github Stars](https://img.shields.io/github/stars/Unknown-user-dev/VoiceMeeter-RMC?style=for-the-badge)
![GitHub issues](https://img.shields.io/github/issues-raw/Unknown-user-dev/VoiceMeeter-RMC?style=for-the-badge)

This project provides a Node.js API for interacting with Voicemeeter using the `VoicemeeterRemote64.dll` DLL. It allows you to control audio inputs and outputs, manipulate Voicemeeter parameters, and interact with macro buttons.

## 🚀 **Setup**

To use this API, you must have Voicemeeter installed on your Windows system. The path to the DLL (`VoicemeeterRemote64.dll`) is determined automatically based on Voicemeeter's registry keys.

And then, you can install the API using npm:

```bash
npm install voicemeeter-rmc
```

## 📦 **Dependencies**

- [winreg](https://www.npmjs.com/package/winreg): For reading Windows registry keys.
- [koffi](https://www.npmjs.com/package/koffi): For loading and using the Voicemeeter DLL.

## 🛠️ **Configuration**

Ensure that Voicemeeter is installed and that the `VoicemeeterRemote64.dll` file is accessible. The API will automatically find the DLL based on the registry settings of Voicemeeter.

## 📋 **Features**

Here’s what you can do with the API:

### Initialization and Connection
- `init()`: Initializes the API and loads the DLL.
- `login()`: Logs in to Voicemeeter.
- `logout()`: Logs out from Voicemeeter.

### Voicemeeter Control
- `runVoicemeeter(runVoicemeeterType)`: Runs Voicemeeter with a specified type.
- `showVoicemeeter()`: Displays the Voicemeeter interface.
- `shutdownVoicemeeter()`: Shuts down Voicemeeter.
- `restartVoicemeeterAudioEngine()`: Restarts the Voicemeeter audio engine.
- `ejectVoicemeeterCassette()`: Ejects the Voicemeeter cassette.
- `resetVoicemeeterConfiguration()`: Resets the Voicemeeter configuration to default.
- `saveVoicemeeterConfiguration(filename)`: Saves the current Voicemeeter configuration to a file.
- `loadVoicemeeterConfiguration(filename)`: Loads a Voicemeeter configuration from a file.
- `lockVoicemeeterGui(lock)`: Locks or unlocks the Voicemeeter GUI.

### Macro Buttons
- `setMacroButtonState(button, state)`: Sets the state of a macro button.
- `setMacroButtonStateOnly(button, state)`: Sets the state of a macro button, without affecting other buttons.
- `setMacroButtonTrigger(button, trigger)`: Sets the trigger for a macro button.
- `setMacroButtonColor(button, color)`: Sets the color of a macro button.

### Audio Device Management
- `getOutputDeviceNumber()`: Gets the number of output devices.
- `getInputDeviceNumber()`: Gets the number of input devices.
- `updateDeviceList()`: Updates the list of input and output devices.

### Parameters Management
- `getRawParameterFloat(parameter)`: Gets the float value of a parameter.
- `getRawParameterString(parameter)`: Gets the string value of a parameter.
- `setRawParameterFloat(parameter, value)`: Sets the float value of a parameter.
- `setRawParameterString(parameter, value)`: Sets the string value of a parameter.
- `setRawParameters(parameters)`: Sets multiple parameters at once.

### Strip and Bus Control
- `setStripParameter(stripNumber, name, value)`: Sets a parameter for a specific audio strip.
- `getStripParameter(stripNumber, name)`: Gets a parameter value for a specific audio strip.
- `setBusParameter(busNumber, name, value)`: Sets a parameter for a specific bus.
- `getBusParameter(busNumber, name)`: Gets a parameter value for a specific bus.

### Level Control
- `getLevel(type, channel)`: Gets the level of a specified type and channel.

## ⚙️ **Enums**

The API provides enums to help with configuration:

- `VoicemeeterType`
- `RunVoicemeeterType`
- `InterfaceType`
- `LevelType`
- `DeviceType`
- `MacroButtonState`
- `MacroButtonTrigger`
- `MacroButtonColor`

## 📝 **Usage Example**

Here's a basic example of how to use the API:

```javascript
const voicemeeter = require('voicemeeter-rmc');

// Initialize the API
await voicemeeter.init();

// Login to Voicemeeter
voicemeeter.login();

// Show Voicemeeter interface
voicemeeter.showVoicemeeter();

// Get the level of the first bus
const busLevel = voicemeeter.getBusLevel(0);
console.log(`Bus 0 Level: ${busLevel}`);

// Set the mute state of the first strip
voicemeeter.setStripMute(0, true);

// Logout from Voicemeeter
voicemeeter.logout();
