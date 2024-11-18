## Readme
The following repo contains the keymap files that are located in
`~/qmk_firmware/keyboards/splitkb/kyria/keymaps/my-kyria-keymap`

## Setup and flashing

### Check if qmk is ready
``` bash
qmk doctor
```

### 1. Visit [qmk configurator](https://config.qmk.fm/#/sofle/) and make your layouts!
Then donwload the keymap.json file

### 2. Compile the keymap.json you downloaded from qmk configurator
``` bash
# the following command will generate a keymap.c file in 
# ~/qmk_firmware/.build/obj_sofle_rev1_sofle_rev1_layout_mine/src
qmk compile layout.json
```

### 3. Create a new keymap if you don't already have one
``` bash
qmk new-keymap -kb softle
# and give it a name like my-softle-keymap
```

### 4. Update rules.mk
``` bash
# Add the following in
#  ~/qmk_firmware/keyboards/softle/keymaps/my-softle-keymap/rules.mk
MOUSEKEY_ENABLE = yes
ENCODER_ENABLE = yes
EXTRAKEY_ENABLE = yes
```

### 5. Update keymap.c
replace the default `keymap.c` in `~/qmk_firmware/keyboards/softle/keymaps/my-softle-keymap` with the one that you built manually in `~/qmk_firmware/.build/obj_sofle_rev1_sofle_rev1_layout_mine/src`

### 6. Compile & flash
``` bash
qmk compile -kb sofle -km my-sofle-keymap
qmk flash -kb sofle -km my-sofle-keymap
# connect one side of the keyboard and hit the reset button
# then repeat for the other side
```

