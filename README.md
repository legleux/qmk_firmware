## Sanity Check

### Flash back to default

    cd qmk_firmware
    make gmmk/pro/rev1/ansi:default
    make gmmk/pro/rev1/ansi:default:flash

Hit `Fn` + `\` while it's looking for the bootloader


### Error

Missing some chibi header

`qmk doctor` showed some submodules were out of date

    qmk compile -kb clueboard/66/rev3 -km default

Now I have 
    obj_clueboar_66_rev3
    obj_clueboar_66_rev3_default
    clueboard_66_rev3_default.elf
    clueboard_66_rev3_default.hex
    clueboard_66_rev3_default.map


# My config

    $ qmk config
    multibuild.keymap=default
    user.keyboard=gmmk/pro/rev1/ansi
    user.keymap=legleux
    user.qmk_home=/home/emel/dev/qmk/qmk_firmware

## Create a new keymap

    $ qmk new-keymap -km legleux_test
    Ψ Generating a new keymap
    Ψ Created a new keymap called legleux_test in: /home/emel/dev/qmk/qmk_firmware/keyboards/gmmk/pro/rev1/ansi/keymaps/legleux_test.
    Ψ Compile a firmware with your new keymap by typing: qmk compile -kb gmmk/pro/rev1/ansi -km legleux_test.


Compile a keymap

    qmk compile -kb <keyboard> -km default

Where <keyboard> is the directory that contains the config.h, info.json, readme.md, .c and .mk file
E.g. /home/emel/dev/qmk/qmk_firmware/keyboards/clueboard/66/rev3/

# How to build a new keymap

ln -s qmk_firmware/my_keebs/pro/rev1/ansi
../keyboards/gmmk/pro/rev1/ansi

ln -s ../keyboards/drop/alt/ alt 
ln -s ../keyboards/gmmk/pro/rev1/ansi gmmk_pro


##  Hide all the keyboards I don't have

    ls -1 keyboards > all_keyboards.txt 
    # this won't work because I have subdirs in the links
    ls -1 my_keebs > all_my_keebs.txt 

    diff --new-line-format="%L" --old-line-format="%L" --unchanged-line-format="" all_keyboards.txt all_my_keebs.txt > all_hidden_keyboards.txt
