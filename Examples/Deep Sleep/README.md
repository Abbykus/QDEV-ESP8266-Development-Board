## ESP8266 DEEP SLEEP / WAKEUP FROM TIMER
The ESP8266 can enter a deep sleep mode which reduces the ESP8266 current consumption to around 20 microamps.
In deep sleep all MCU peripherals are powered down except the Real Time Clock (RTC). 

The ESP8266 can wake from deep sleep by connecting GPIO16 to the Reset (RST) breakout pin. See the sketch 'main_1.cpp' for a simple example.