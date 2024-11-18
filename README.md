## Readme
The following repo contains the keymap files that are located in
`~/qmk_firmware/keyboards/splitkb/kyria/keymaps/my-kyria-keymap`

## Setup and flashing

### Check if qmk is ready
``` bash
qmk doctor
```

### 1. Visit [qmk configurator](https://config.qmk.fm/#/sofle/) and make your layouts!
`keyboard is splitkb kyria rev3`
Then donwload the keymap.json file
I had to change the version from rev3 to rev 3 to make this work in `my-kyria-rev3-keymap.json`
`"keyboard": "splitkb/kyria/rev2",`

### 2. Compile the keymap.json you downloaded from qmk configurator
``` bash
# the following command will generate a keymap.c file in 
# ~/qmk_firmware/.build/obj_splitkb_kyria_rev2_my-kyria-rev3-keymap/src
qmk compile my-kyria-rev3-keymap.json
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

