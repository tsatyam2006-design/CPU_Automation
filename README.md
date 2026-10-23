# printer-automation

Connection	Wiring: 

RTC SDA	GPIO               21
RTC SCL	GPIO               22
RTC VCC	                   3.3
RTC GND                    ESP32 GND
CPU USB 5V                 through 1 kΩ resistor to GPIO 27
GPIO 27 junction           through 2 kΩ resistor to GND
GPIO 23                    through 1 kΩ resistor to 2N2222 base
2N2222 emitter/collector	 Across Power-button contacts


Conection of 2N2222A transistor:

                
                  GPIO 23
                     |
                   1 kΩ
                     |
                  Base (B) 2N2222A  

Collector (C) ----------------> UPS Button Pin A (3.3 V)

Emitter (E) ------------------> UPS GND (Button Pin B)


Connection of CPU USB 5V to esp32: We used voltage divider in the line
                  
                  CPU USB 5V 
                      |
                  1KΩ resistor 
                      |
                      | — ESP GPIO27 
                      |
                  2KΩ resistor 
                      |
                      GND
