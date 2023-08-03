# myKlipperE3v2
These are my klipper-settings: for **Ender 3 v2**, minimus, BLTouch, mesh bed leveling 5x5

## My hardware setup:

- Creality Ender 3 v2
- Raspberry Pi 4
- Sabrent HB-UMP3 USB-hub + power
- BTT HDMI5 V1.1 Touchscreen
- BLtouch
-Logitech C920


## Resources that helped me set this up:
1. My starting point: https://www.reddit.com/r/klippers/comments/kj2h5r/stepbystep_guide_for_ender_3_v2_klipper_w_bltouch/
2. https://gist.github.com/prcutler/9360ab01795c55f37a1063159c72813d

## Specific custom mods I had to adjust for:
- Hotend cooler system: I use the **Minimus** hotend cooler setup (https://cults3d.com/en/3d-model/tool/minimus-hotend-cooler-system)
  - 4010 dual
  - BLTouch holder: BLTouch offsets:
    - x-offset: -43.5
    - y-offset: -5.7
- BLTouch

## Adjustments I had to make:

### This line in resource 1:

```
z_hop: 10                 # Move up 10mm z_hop_speed: 5
```
shouldn't be on one line, now "z_hop_speed: 5" is commented out, it should have been:
```
z_hop: 10                 # Move up 10mm 
z_hop_speed: 5
```

### 

## Extra notes that are useful:

### - Start Kiauh again command in terminal:
```
./kiauh/kiauh.sh
```

### - Links to the your Mainsail/FLuidd GUI
1. http://my.mainsail.xyz/
2. http://app.fluidd.xyz
