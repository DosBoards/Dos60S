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

3. Add the community modules (the default keymap uses `getreuer/socd_cleaner`):

    ```sh
    git clone https://github.com/getreuer/qmk-modules.git ~/qmk_firmware/modules/getreuer
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
