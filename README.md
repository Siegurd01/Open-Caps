# Open Caps - Cheap and Powerful Supercapacitor UPS
## Introduction

Open Caps is an open-source project that aims to create a cheap and powerful supercapacitor-based UPS for safe shutdown and restore of your single-board computer (SBC) project. The project was born out of frustration with unreliable 18650-based UPS's and the need for a more robust solution that ensures reliable data safety when the external power is turned off.

I plan to built UPS using one of several supercapacitor charger ICs: the LTC3350, LTC3128, MAX38890, and others. It sould provide a 5V output with a current capacity of 3-10A, depending on the specific charger IC used. The UPS should communicates with the SBC via GPIO, I2C, or UART interface to enable safe shutdown of the SBC when external power is lost and to power on when input power is restored and supercapacitors charge to 100%.

## Features
Open Caps UPS should include the following features:
- Supercapacitor-based UPS for safe shutdown and restore of SBC projects;
- Input voltage range of 5-24V;
- Output voltage of 5V;
- Output current capacity of 3A-10A, depending on the specific charger IC used;
- Communication with SBC via GPIO, I2C, or UART interface for safe shutdown and power-on functionality;
- LED indicators for UPS working modes illustration (charging, full, discharging, input power present, input power lost);
- Optional STM32 MCU for UPS control and/or SBC communication;

## Development Plan
:black_square_button: **Choosing a supercapacitor charger IC to use in UPS design (LTC3350, LTC3128, MAX38890 etc);**    
:black_square_button: Choosing a buck-bust DC-DC converter if needed;    
:black_square_button: Designing and build the UPS circuit using the chosen charger IC and other necessary components, such as capacitors, resistors, and diodes. A schematic and PCB layout can be found in the "design" directory of this repository;    
:black_square_button: Chooseing a communication interface to use between the UPS and SBC, such as GPIO, I2C, or UART;    
:black_square_button: Implementing the necessary software communication protocol between the UPS and SBC;    
:black_square_button: Testing first design UPS with cosciloscope and load;    
:black_square_button: Making necessery changes to the design... and connecting the UPS to SBC and test the safe shutdown and power-on functionality using the chosen communication interface.    

## Updates
01.05.2023 - Overview of available supercapacitor charger IC's and studying datasheets of LTC3350, LTC3128, MAX38889 from Analog Devices: Power Management > [Supercapacitor Chargers](https://www.analog.com/en/parametricsearch/11413#/).  

LTC3128 offers 5V 3A backup power but needs a DC-DC step up converter cuz output voltage drops with Vcap voltage:
![LTC3128](https://user-images.githubusercontent.com/75634636/235470254-064b0a52-3e36-4328-a6bb-d8e9df26f020.jpg)

MAX38890 offers 5V 5A backup power with a single Cap:
![MAX38890](https://user-images.githubusercontent.com/75634636/235474956-4af02de0-d1c1-4b82-90d2-9d0bc5baecad.jpg)

Most powerful design LTC3350 5V 4A (30W) In addition, the step-down converter can run in reverse asa step-up converter to deliver power from the supercapacitor stack to the backup supply rail:
![LTC3350](https://user-images.githubusercontent.com/75634636/235479535-19fbea09-8caf-47f5-ac48-4ab1d6b73906.jpg)

Usefull info for super capacitor calculation:
![formula](https://user-images.githubusercontent.com/75634636/235483289-b0bff889-c889-4e6b-a2d1-2aa6396d9d01.jpg)

## Contributing
Contributions to the Open Caps project are welcome! If you would like to contribute, please fork this repository, make your changes, and submit a pull request.

## License
Open Caps is released under the MIT License. Please see the "LICENSE" file in this repository for more information.

