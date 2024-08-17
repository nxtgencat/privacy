# Device Management Scripts

This repository contains PowerShell commands and scripts for managing microphone and camera devices on Windows. These scripts allow you to easily retrieve, disable, and enable microphone and camera devices.

## Prerequisites

- **PowerShell**: Ensure you are using PowerShell on a Windows system.
- **Administrator Privileges**: The scripts must be run with elevated privileges (as an administrator) to manage device states.

## Usage

### Managing Microphone Devices

1. **Get all microphone devices:**

   ```powershell
   Get-PnpDevice -Class "AudioEndpoint" | Where-Object { $_.FriendlyName -match "Microphone" }
   ```

   This command lists all devices in the "AudioEndpoint" class that have "Microphone" in their friendly name.

2. **Disable all microphone devices:**

   ```powershell
   Get-PnpDevice -Class "AudioEndpoint" | Where-Object { $_.FriendlyName -match "Microphone" } | Disable-PnpDevice -Confirm:$false
   ```

   This command disables all microphone devices found on the system without prompting for confirmation.

3. **Enable all microphone devices:**

   ```powershell
   Get-PnpDevice -Class "AudioEndpoint" | Where-Object { $_.FriendlyName -match "Microphone" } | Enable-PnpDevice -Confirm:$false
   ```

   This command enables all microphone devices that were previously disabled.

### Managing Camera Devices

1. **Get all camera devices:**

   ```powershell
   Get-PnpDevice -Class "Camera"
   ```

   This command lists all devices in the "Camera" class.

2. **Disable all camera devices:**

   ```powershell
   Get-PnpDevice -Class "Camera" | Disable-PnpDevice -Confirm:$false
   ```

   This command disables all camera devices found on the system without prompting for confirmation.

3. **Enable all camera devices:**

   ```powershell
   Get-PnpDevice -Class "Camera" | Enable-PnpDevice -Confirm:$false
   ```

   This command enables all camera devices that were previously disabled.

## Notes

- Ensure to run these commands in PowerShell as an administrator to have the necessary permissions for managing device states.
- These commands are designed to work on Windows systems with the appropriate device classes ("AudioEndpoint" for microphones and "Camera" for cameras).
- If managing specific devices based on their names, adjust the `Where-Object` filtering accordingly.
