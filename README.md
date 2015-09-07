
Emulation Station Setup
=======================

Requirements
------------

A intel machine with Arch Linux and `aurget` to install packges from the Arch Linux User repository.

Setup
-----

- Install dependencies:

    ```
    sudo pacman -S gcc-multilib
    sudo pacman -S make
    sudo pacman -S cmake
    sudo pacman -S sdl2
    sudo pacman -S boost
    sudo pacman -S freeimage
    sudo pacman -S freetype2
    sudo pacman -S eigen
    sudo pacman -S curl
    ```

- Clone repository:

    ```
    cd /tmp
    git clone https://github.com/Aloshi/EmulationStation.git
    ```

- Build it:

    ```
    cd EmulationStation
    cmake .
    make
    ```

- Copy to `/opt`:

    ```
    cd ..
    sudo mv EmulationStation /opt
    sudo chown root:root -R /opt/EmulationStation
    sudo ln -s /opt/EmulationStation/emulationstation /usr/local/bin/emulationstation
    ```

- Run `emulationstation` to create the configuration files for your user.

- Install the emulators:

    ```
    sudo pacman -S pcsxr
    sudo pacman -S pcsx2
    aurget -S retroarch
    aurget -S libretro-fceumm-git
    aurget -S libretro-gambatte-git
    aurget -S libretro-genesis-plus-gx-git
    aurget -S libretro-mupen64plus-git
    aurget -S libretro-snes9x-next-git
    aurget -S libretro-vba-next-git
    ```

- Copy the emulator configurations file.

    ```
    cd this/repo
    cp es_system.cfg ~/.emulationstation
    ```

- Create ROM directories:

    ```
    mkdir -p ~/roms/snes
    mkdir -p ~/roms/nes
    mkdir -p ~/roms/n64
    mkdir -p ~/roms/megadrive
    mkdir -p ~/roms/gb
    mkdir -p ~/roms/gbc
    mkdir -p ~/roms/gba
    mkdir -p ~/roms/psx
    mkdir -p ~/roms/ps2
    ```

- Configure RetroArch to exit when `select + start` is pressed:

    * Edit the file `~/.config/retroarch/retroarch.cfg`.

    * And change the values:

        ```
        input_enable_hotkey_btn = "8"
        input_exit_emulator_btn = "9"
        ```

- Configure your joystick for `emulationstation`, `retroarch` and any other emulator.

