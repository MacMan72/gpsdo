LARS GPSDO Programming
- Arduino Nano ATmega328p
- Plug in board, should recognize as "USB-SERIAL CH340 (COM##)"
- Use "Arduino Nano" as Board Type
- Use "ATmega328p (Old Bootloader)" as Processor
- Use "Blank" as Programmer (nothing should be selected)
- Check then upload code
- Should reboot and start running code after upload complete
- New COM port should show up after code upload, select board type and COM port to connect and see scrolling mesages
- Enter h1 to get min DAC value
- Enter H65536 to get max DAC value
- Calculate range of DAC and divide by 65536 to calculate gain
- Enter g### to enter value for gain
- Enter s1 to save gain value
- Enter r to run closed loop
- See printed notes for more info
- Lars GPSDO Info: https://github.com/paulvee/Lars-GPSDO-V1

AndrewBCN GPSDO Programming
- STM32F411ceu6 BlackPill
- https://github.com/AndrewBCN/STM32-GPSDO
- Plug in and reboot while holding boot0 (hold both buttons down, release RST button, then almost immediately boot0) 
- Should recognize in Device Manager as "STM Bootloader" device, no COM port assigned
- Choose "Generic STM32F4 series" as board in Arduino IDE
- Choose Board part Number as "BlackPill F411CE"
- Choose upload method as "STM32CubeProgrammer (DFU)"
- Check and upload code (no com port or connection to board required) (Change Code revision to OXCO Type. e.g. "GPSDO - Trimble OCXO")
- Should reboot and start running code after upload complete
- Make sure generic serial is enabled for both USB and USART

- for dst...
-     if (gps.time.hour() > 3)   // change time zone
      hours = gps.time.hour() - 4;
      else    
      hours = gps.time.hour() + 20; 

GPS Programming
- Download and install U Center
- If needed install driver for CP2102 TTL Module
- Connect Module to GPS (+5V, GND, Rx->Tx, Tx->Rx)
- Connect U Center to TTL Module (Look up COM Port in Device Manager)
- In View->Configuration View Select TP5(Timepulse 5)
- In 0-TIMEPULSE set the following:
  - Freq: 1 Hz
  - Duty Cycle: 50%
  - Lock to GNSS: Checked
  - Other Settings: Checked
  - Align Pulse to TOW=0: Checked
  - Rising Edge: Checked
- Click SEND button
- Select Receiver->Action->Save Config
(Does this store permanently or just to capacitor memory?)
 
