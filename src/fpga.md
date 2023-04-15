## FPGA cheat sheet

### Lattice iCE-40HX1K (icestick)
* Model: ICE40HX1K-STICK-EVN
* [Datasheet](../docs/icestick.pdf)
* [apio documentation](https://github.com/FPGAwars/apio)

#### Installation (Ubuntu 18.04 LTS)
To install apio ecosystem follow the instructions from the [official documentation](https://github.com/FPGAwars/apio/wiki/Quick-start#apio-installation)

#### Installation/Usage Issues
Some problems (and solutions) I encountered during apio installation and prject build/upload:
* ```sh: iceprogduino: command not found```:
    **When**: After running "apio upload"
    **Solution**:
    ```
    git clone https://github.com/OLIMEX/iCE40HX1K-EVB.git 
    cd iCE40HX1K-EVB/programmer/iceprogduino
    make
    sudo make install
    ```
* ```board icestick not connected```:
    **When**: After running "apio upload"
    **Solution**:
    Check the description of your board using "apio system --lsftdi". 
    ```bash
    $ apio system --lsftdi
        Number of FTDI devices found: 1
        Checking device: 0
        Manufacturer: FTDI, Description: Dual RS232-HS
    ```
    Update the ```boards.json``` file with the correct FTDI description.
    ```bash
    $ vim /home/$USER/.local/lib/python3.6/site-packages/apio/resources/boards.json
    ...
      "icestick": {
        "name": "iCEstick Evaluation Kit",
        "fpga": "iCE40-HX1K-TQ144",
        "programmer": {
          "type": "iceprog"
        },
        "usb": {
          "vid": "0403",
          "pid": "6010"
        },
        "ftdi": {
          "desc": "Dual RS232-HS" # !!! UPDATE THIS LINE !!!
        }
      },
    ...
    ```
