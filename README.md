# water-temp-sensor

Water temperature sensor service for reading temperature from a serial device.

## Installation (Arch Linux)

Build and install the package using makepkg:

```bash
makepkg -si
```

This will:
- Install the `water-temp-sensor` script to `/usr/bin/water-temp-sensor`
- Install the systemd service file to `/usr/lib/systemd/system/water-temp-sensor.service`
- Install the config file to `/etc/water-temp-sensor.conf`

## Service Management

After installation, enable and start the service:

```bash
sudo systemctl enable --now water-temp-sensor.service
```

Check service status:

```bash
sudo systemctl status water-temp-sensor.service
```

View logs:

```bash
sudo journalctl -u water-temp-sensor.service -f
```

## Configuration

The service runs as root and reads temperature data from the serial device, writing the result to the configured output path.

Configuration is done via `/etc/water-temp-sensor.conf`:

```
SERIAL_DEV=/dev/serial/by-id/<your-device-id>
SENSOR_OUTPUT_PATH=/tmp/water_temp
```

- `SERIAL_DEV`: Full path to the serial device (typically in `/dev/serial/by-id/`)
    - Could be any serial /dev, but I would recommend sticking to 'by-id'
- `SENSOR_OUTPUT_PATH`: Path where the temperature value will be written (as integer in millidegrees)
    - The script will output (overwrite) this file everytime it reads a new value from the serial device.
    - Output value is multiplied by 1000 because CoolerControl needs it in milidegrees. (20.5C -> 20500mC)
SENSOR_OUTPUT_PATH=/tmp/water_temp

Edit this file to configure your serial device and output path. After making changes, restart the service:

```bash
sudo systemctl restart water-temp-sensor.service
```
