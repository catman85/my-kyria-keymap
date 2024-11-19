## Readme
The following repo contains the keymap files that are located in
`~/qmk_firmware/keyboards/splitkb/kyria/keymaps/my-kyria-keymap`

## Setup and flashing

### Check if qmk is ready
``` bash
qmk setup
qmk doctor
```

### Troubleshooting
on this keyboard the master is right by default
messing with define master right, doesn't fix the problem
if you are getting any errors
you can remove and reinstall the qmk_firmware folder
``` bash
rm -rf ~/qmk_firmware
# this will also delete your keymaps!
sudo pacman -S qmk
```

### 1. Visit [qmk configurator](https://config.qmk.fm/#/sofle/) and make your layouts!
`keyboard is splitkb kyria rev3`
Then donwload the keymap.json file

### 2. Compile the keymap.json you downloaded from qmk configurator
``` bash
qmk compile my-kyria-rev3-keymap.json
# this command will generate a keymap.c file in 
# ~/qmk_firmware/.build/obj_splitkb_kyria_rev2_my-kyria-rev3-keymap/src
```

### 3. Create a new keymap if you don't already have one
``` bash
qmk new-keymap -kb kyria
# and give it a name like my-kyria-keymap
```

### 4. Update rules.mk
``` bash
# Add the following in
#  ~/qmk_firmware/keyboards/splitkb/kyria/keymaps/my-kyria-keymap/rules.mk
OLED_ENABLE = no
MOUSEKEY_ENABLE = yes
ENCODER_ENABLE = yes
EXTRAKEY_ENABLE = yes
BOOTLOADER = caterina
```

### 5. Update keymap.c
replace the default `keymap.c` in `~/qmk_firmware/keyboards/splitkb/kyria/keymaps/my-kyria-keymap` with the one that you built manually in `~/qmk_firmware/.build/obj_splitkb_kyria_rev2_my-kyria-rev3-keymap/src`

### 6. Compile & flash
``` bash
qmk compile -kb kyria -km my-kyria-keymap
qmk flash -kb kyria -km my-kyria-keymap
# connect one side of the keyboard and hit the reset button
# then repeat for the other side
```

