### initial setup

    $ brew tap px4/px4
    $ brew install gcc-arm-none-eabi
    $ brew install openocd

### compiling

Download the STM32F4 Cube library from st.com. 
In your shell, set `$STM32_ROOT` to the root directory of the downloaded library. 
Then run `./make.sh` to compile the elf/hex binaries. 

### connecting to the board

In a terminal window, run

    $ openocd  -f /usr/local/share/openocd/scripts/board/st_nucleo_f4.cfg

In a second terminal window:

    $ telnet localhost 4444

From here you can submit commands to the board. E.g. to halt the running program:

    > reset halt

To load the compiled binary:

    > flash write_image erase main.hex

To run the loaded binary:

    > reset run
