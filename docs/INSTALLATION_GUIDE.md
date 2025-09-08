# Shutters Automation v1.0 - Installation Guide

## Prerequisites

1. **Home Assistant** with YAML configuration enabled
2. **Broadlink RM** integration configured and working
3. **RF shutters** with learned commands (On/Off/Pause)

## Installation Steps

### 1. Prepare Your Shutter RF Commands

Before installation, ensure you have learned the RF commands for your shutters in the Broadlink integration:
- **On** command (typically moves shutter DOWN)
- **Off** command (typically moves shutter UP)  
- **Pause** command (stops shutter movement)

### 2. Choose Your Configuration Method

#### Option A: Single Shutter Setup
Use this for one shutter installation.

#### Option B: Multiple Shutters Setup  
Use this if you want to control multiple shutters.

### 3. Configure Input Entities

Copy the relevant sections from the template files:

**For single shutter:**
1. Copy content from `templates/shutter_inputs.yaml`
2. Replace `{SHUTTER_NAME}` with your shutter name (e.g., `office`, `bedroom`)
3. Replace `{SHUTTER_DISPLAY_NAME}` with display name (e.g., `Office`, `Bedroom`)
4. Add to your `configuration.yaml` or separate YAML file

**For multiple shutters:**
1. Use the template multiple times for each shutter
2. Ensure each shutter has a unique name
3. See `examples/multi_shutter_example.yaml` for reference

### 4. Configure Sensors

1. Copy content from `templates/shutter_sensors.yaml`
2. Replace placeholders with your shutter names
3. Add to your sensor configuration

### 5. Configure Scripts

1. Copy content from `templates/shutter_scripts.yaml`
2. Replace placeholders:
   - `{SHUTTER_NAME}` - your shutter name
   - `{SHUTTER_DISPLAY_NAME}` - display name
   - `{BROADLINK_ENTITY}` - your Broadlink remote entity (e.g., `remote.broadlinkremote_remote`)
   - `{DEVICE_NAME}` - your RF device name in Broadlink (e.g., `OfficeShutter`)
3. Add to your `scripts.yaml`

### 6. Configure Automations

1. Copy content from `templates/shutter_automations.yaml`
2. Replace placeholders:
   - `{SHUTTER_NAME}` - your shutter name
   - `{SHUTTER_DISPLAY_NAME}` - display name  
   - `{UNIQUE_ID_PREFIX}` - unique prefix for automation IDs (e.g., `office_shutter`)
3. Add to your `automations.yaml`

## Configuration Parameters

### Travel Time Calibration

The `travel_time` parameter is crucial for accurate position tracking:

1. Set initial value to estimated full travel time
2. Test full up/down movement
3. Adjust value based on actual timing
4. Typical values: 15-25 seconds for most shutters

### Position Calibration

The system uses an exponential curve for position calculation:
- Formula: `position = 100 * (1 - e^(-0.198 * time))`
- This accounts for non-linear shutter movement
- Fine-tune the coefficient (0.198) if needed for your specific shutters

## Testing Your Setup

1. **Basic Movement Test:**
   - Use the manual scripts to test up/down/pause
   - Verify all commands work correctly

2. **Position Tracking Test:**
   - Move shutter to known position
   - Use pause command
   - Check if reported position matches reality

3. **Slider Control Test:**
   - Use the position slider in UI
   - Verify shutter moves to selected position
   - Test multiple positions (25%, 50%, 75%)

## Troubleshooting

### Common Issues:

1. **Shutter doesn't respond:**
   - Check Broadlink integration
   - Verify RF commands are learned correctly
   - Check entity_id references in scripts

2. **Position tracking inaccurate:**
   - Calibrate travel_time parameter
   - Ensure pause commands work reliably
   - Check automation triggers are firing

3. **UI shows wrong position:**
   - Restart Home Assistant after configuration changes
   - Check sensor templates for syntax errors
   - Verify input_number entity names match

### Debug Steps:

1. Check Home Assistant logs for errors
2. Test scripts individually from Developer Tools
3. Verify automation triggers in automation traces
4. Use template editor to test position calculations

## Next Steps

After successful installation:
1. Add shutter controls to your dashboard
2. Create scenes for common positions
3. Set up scheduling automations
4. Consider integration with weather data or sun position

## Support

For issues or questions:
1. Check the troubleshooting section
2. Review automation traces in Home Assistant
3. Validate YAML syntax in configuration files