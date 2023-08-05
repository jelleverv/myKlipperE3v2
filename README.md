# myKlipperE3v2
These are my klipper-settings: for **Ender 3 v2**, minimus, BLTouch, mesh bed leveling 5x3

## My hardware setup:

- Creality Ender 3 v2
	- Motherboard: 4.2.2
	- Old screen type (replaced by BTT HDMI5 V1.1 Touchscreen after installing klipper): DACAI
	- Creality magnetic PEI bed
- Raspberry Pi 4
- Sabrent HB-UMP3 USB-hub + power
- BTT HDMI5 V1.1 Touchscreen
- BLtouch
-Logitech C920


## Resources that helped me set this up:
1. My starting point: https://www.reddit.com/r/klippers/comments/kj2h5r/stepbystep_guide_for_ender_3_v2_klipper_w_bltouch/
2. https://gist.github.com/prcutler/9360ab01795c55f37a1063159c72813d
3. FLuidd macros: https://docs.fluidd.xyz/configuration/initial_setup#printer-configuration

## Specific custom mods I had to adjust for:
- Hotend cooler system: I use the **Minimus** hotend cooler setup (https://cults3d.com/en/3d-model/tool/minimus-hotend-cooler-system)
  - 4010 dual
  - BLTouch holder: BLTouch offsets:
    - x-offset: -43.5
    - y-offset: -5.7
- BLTouch

## Adjustments I had to make:

### 1. This line in resource 1:

```
z_hop: 10                 # Move up 10mm z_hop_speed: 5
```
shouldn't be on one line, now "z_hop_speed: 5" is commented out, it should have been:
```
z_hop: 10                 # Move up 10mm 
z_hop_speed: 5
```

### 2. Z calibrate: Z "Move Out of Range"-error:
Because there is a z offset between the BLTouch & the nozzle you have to adjust the Z-height, I did this on the screen but got this error because under [stepper_z] position_min was set to 0. But I had to move beyond that point to get my nozzle further down than the point the BLTouch hit the bed. 
 
(Don't add the "...", they are just there to indecate other settings)

```
[stepper_z]
...
position_min: -4
...
```

### 3. Bed leveling X "Move Out of Range"-error:

Because of my Minimus setup, I had a BLTouch offset and to reach the last bed leveling mesh point, the suggested setting was to restrictive, so I adjusted the max position for the stepper_x to 249 (do not exceed 249!).

```
[stepper_x]
...
position_max: 249
...
```

## Extra notes that are useful:

### - Start Kiauh again command in terminal:
```
./kiauh/kiauh.sh
```

### - Links to the your Mainsail/FLuidd GUI
1. http://my.mainsail.xyz/
2. http://app.fluidd.xyz

### - Adding Raspberry Pi temperature to interface

Add this code to your printer.conf:

```
[temperature_sensor raspberry_pi]
sensor_type: temperature_host
min_temp: 10
max_temp: 100

[temperature_sensor mcu_temp]
sensor_type: temperature_mcu
min_temp: 0
max_temp: 100
```
