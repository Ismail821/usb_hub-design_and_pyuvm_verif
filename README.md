#USB3.2 to 16xUSB2.0 bridge IP Design and Verification Project.

Problem Defenition
> Develop and verify a DUT for a high speed USB to multiple low speed connections. 

Key Features
- The design is scalable with upto a configurable number of low speed devices, with which both the design and Verification enviroinment should scale accordingly creating the required number of interfaces, device UVC's etc
- This whole project is built using all open source tools

Folder structre inside the source
- rtl
    - Contains all the RTL and Design related files
- verif
    - scoreboard
        - Contains the scoreboard and coverage releated files needed for the checker and data verification part for the IP.
    - seqs
        - Has the sequences that should be extended from the uvc's sequence class for having more customizatation on the testcases.
    - tb
        - Contains the main testbench top file where the port connections are made and also contains the environment & vsequencer files.
    - testcases
        - Contains the various number of testcases which is needed and creation of the appropriate sequences
    - usb_uvc
        - Contains the uvc files that will drive the signals and talk with the DUT
        usb_driver
            - Contains the driver related code and manages the protocol
        usb_monitor
            - Contains the uvc monitor related files
        usb_scoreboard
            - Contains asertion related stuff that is used to monitor the USB protocol connect to the usb_monitor
            - monitors the protocol violation and keeps track of the outgoing and incoming transactions

Installation tools required
- python: Main Verification language
    - cocotb: Gives access to function to connection to the iverilog interface
    - PyUVM:  UVM implementation in python for cocotb
- gtkwave: To view waveform
- icarus iverilog: to simulate the RTL design with python
- yosys:   Synthesysing the design

RTL Architecture:
![RTL Architecture of the multiple slices in the Complete design](https://github.com/Ismail821/usb_hub-design_and_pyuvm_verif/blob/main_branch/documentation/Detailed_RTL_Architecture.png?raw=true)

A single slice of RTL Pipeline
![RTL Slice of 1 unit of the design showing sub components](https://github.com/Ismail821/usb_hub-design_and_pyuvm_verif/blob/main_branch/documentation/Single_data_chain.png?raw=true)

PyUVM Scalable Verification architecture 
![Scalable Verif Architecture with Pyuvm verification](https://github.com/Ismail821/usb_hub-design_and_pyuvm_verif/blob/main_branch/documentation/Testbench_Architecture.png?raw=true)
