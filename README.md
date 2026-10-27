# Dos60S
DosBoards 60 key split keyboard.

## Building the firmware

The QMK keyboard definition lives in `QMK/dosboards`. It gets symlinked into a local QMK install so you can build it without copying files around or passing path flags.

1. Install the QMK CLI, toolchains, and flashing tools:

    ```sh
    curl -fsSL https://install.qmk.fm | sh
    ```

2. Set up the QMK firmware repo (clones to `~/qmk_firmware`):

    ```sh
    qmk setup
    ```

3. Add the community modules: the default keymap uses `getreuer/socd_cleaner`, and
   `brandondoster/which_layer` to report layers and toggles to the
   [which_layer](https://github.com/BrandonDoster/which_layer) overlay:

    ```sh
    git clone https://github.com/getreuer/qmk-modules.git ~/qmk_firmware/modules/getreuer
    git clone https://github.com/BrandonDoster/which_layer.git ~/which_layer
    ln -s ~/which_layer/qmk_module ~/qmk_firmware/modules/brandondoster
    ```

4. Symlink this repo's keyboard folder into QMK (run from the root of this repo):

    ```sh
    ln -s "$(pwd)/QMK/dosboards" ~/qmk_firmware/keyboards/dosboards
    ```

5. Compile or flash:

    ```sh
    qmk compile -kb dosboards/dos60s -km default
    qmk flash -kb dosboards/dos60s -km default
    ```

Flash each half separately with the USB cable plugged into that half. See `QMK/dosboards/dos60s/readme.md` for entering the bootloader.
