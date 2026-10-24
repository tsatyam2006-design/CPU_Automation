### ESP32 AUTOMATIC COMPUTER POWER CONTROLLER

🧰 Components Required

1	ESP32 Dev Module
2	HW-111 DS1307 RTC Module
3	CR2032 coin-cell battery
4	2N2222 NPN Transistor
5	1 kΩ Resistor
6	2 kΩ Resistor
7	Computer with an available USB port
8	Suitable ESP32 power supply

Behaviour:
  - Turn PC ON at scheduled start.
  - During active hours, recover unexpected shutdowns.
  - Retry every 2 minutes if PC remains OFF.
  - At stop time, press power button once if PC is ON.
  - Wait for PC to turn OFF.
  - Enter deep sleep until the next start time.

IMPORTANT:
  RTC time is NOT reset by this program.


### Connection Wiring:

| Component | Connection / Details |
| --- | --- |
| RTC SDA | ESP GPIO 21 |
| RTC SCL | ESP GPIO 22 |
| RTC VCC | 3.3V |
| RTC GND | ESP32 GND |
| CPU USB 5V | through 1 kΩ resistor to GPIO 27 |
| ESP GPIO 27 junction | through 2 kΩ resistor to GND |
| ESP GPIO 23 | through 1 kΩ resistor to 2N2222 base |
| 2N2222 emitter/collector | Across Power-button contacts |

### Connection of 2N2222A transistor:

| Pin / Connection | Details |
| --- | --- |
| Collector (C) | PowerSW Button Pin A (3.3 V) |
| Emitter (E) | PowerSW GND (Button Pin B) |
| Base (B) | through 1kΩ to GPIO 23 |



Conection of 2N2222A transistor:

                
                  GPIO 23
                     |
                   1 kΩ
                     |
                  Base (B) 2N2222A


Connection of CPU USB 5V to esp32:
                  
                  CPU USB 5V 
                      |
                  1KΩ resistor 
                      |
                      | — ESP GPIO27 
                      |
                  2KΩ resistor 
                      |
                      GND


## RTC Time Configuration
``` To set the time on the DS1307 RTC module, follow these steps:
1. In the code, set the SET_RTC_TIME constant to true.
2. Upload the code to your board. This will configure the RTC with the current time from your computer.
3. After the upload is complete, change the SET_RTC_TIME constant back to false.
4. Upload the code again. This prevents the time from being reset if the board restarts.
```

# Note:

Do not remove the coin cell battery from the RTC module after this setup, otherwise the time will be reset.
