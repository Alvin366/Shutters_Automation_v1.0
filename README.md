# Shutters Automation v1.0

A comprehensive Home Assistant package for intelligent RF shutter control via Broadlink RM integration.

## Quick Start

1. **Prerequisites**: Home Assistant + Broadlink RM integration
2. **Learn RF Commands**: Ensure Up/Down/Pause commands are learned
3. **Choose Template**: Single or multiple shutters
4. **Configure**: Replace placeholders in template files
5. **Deploy**: Add to your Home Assistant configuration
6. **Calibrate**: Set travel times for accurate positioning

## Features

- 🎛️ **Smart Position Control** - Slider-based positioning with exponential curve algorithm
- 🔄 **Automatic Tracking** - Real-time position calculation during movement
- 📱 **Manual Scripts** - Direct Up/Down/Pause control
- 🏠 **Multi-Shutter Ready** - Expandable template system
- 🛡️ **Safety Features** - Auto-recovery from stuck states
- 📡 **RF Integration** - Works with any Broadlink RM device

## Package Structure

```
templates/          # Generic YAML templates
examples/           # Ready-to-use configurations  
docs/              # Installation guide
RELEASE_NOTES.md   # Detailed release information
```

## Installation

See `docs/INSTALLATION_GUIDE.md` for complete setup instructions.

## Quick Configuration

1. Copy template files to your HA configuration
2. Replace these placeholders:
   - `{SHUTTER_NAME}` → Your shutter name (e.g., `office`)
   - `{SHUTTER_DISPLAY_NAME}` → Display name (e.g., `Office`)
   - `{BROADLINK_ENTITY}` → Your remote entity (e.g., `remote.broadlinkremote_remote`)
   - `{DEVICE_NAME}` → RF device name (e.g., `OfficeShutter`)
   - `{UNIQUE_ID_PREFIX}` → Unique automation ID prefix

## License

MIT - Free for personal and commercial use