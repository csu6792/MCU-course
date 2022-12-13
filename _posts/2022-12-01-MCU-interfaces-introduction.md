---
layout: post
title: MCU Interfaces Introduction /微控制器介紹
author: [Sheng Jie]
category: [Lecture]
tags: [jekyll, ai]
---

Introduction to MCU interfaces including GPIO, ADC, PWM, I2C, SPI, I2S, UART.

---
## MCU - Micro Control Unit (Microcontroller)
A MCU consist of a processor core, memory and I/O interfaces

---
### [8051 Microcontroller Architecture](https://www.javatpoint.com/embedded-system-8051-microcontroller-architecture)
![](https://www.javatpoint.com/embeddedsystem/images/es-8051-microcontroller2.png)

---
### Cortex-M0 MCU
**NUC140 Functional Block Diagram**
![](https://github.com/csu6792/MCU-course/blob/main/images/NUC140_functional_block_diagram.png?raw=true)

---
### ESP32
![](https://upload.wikimedia.org/wikipedia/commons/9/92/Espressif_ESP32_Chip_Function_Block_Diagram.svg)

---
### RPi4
![](https://heise.cloudimg.io/width/2000/q75.png-lossy-75.webp-lossy-75.foil1/_www-heise-de_/ct/imgs/04/2/7/4/3/7/8/1/RPi4-Block-e4359fdb4be588cf.png)

---
## GPIO (General Purpose I/O)
![](https://github.com/csu6792/MCU-course/blob/main/images/GPIO_circuit_diagram.png?raw=true)

Each IO pad drive/sink **~25mA**, Entire Chip drive/sink **~200mA**<br>
![](https://github.com/csu6792/MCU-course/blob/main/images/GPIO_LED_circuit.png?raw=true)

![](https://i1.wp.com/randomnerdtutorials.com/wp-content/uploads/2018/10/LED_PWM_Example.jpg?w=700&quality=100&strip=all&ssl=1)

---
## ADC (Analog Digital Converter)
![](https://rockuapps.com/wp-content/uploads/2020/11/c-1-791x613.jpg)

**Vin** is input voltage for ADC to sample<br>

**Vref** is reference voltage for ADC to compare with Vin<br>

**2-bit ADC**
<table>
<tr>
<td><img src="https://www.electronics-tutorials.ws/wp-content/uploads/2020/09/comb74.gif"></td>
<td><img src="https://qph.fs.quoracdn.net/main-qimg-fa7473dd759a220592359c69ca8408a2"></td>
</tr>
</table>

**12-bit ADC** : output is a 12-bit binary code, so its value = 0 ~ 4095<br>
![](https://github.com/csu6792/MCU-course/blob/main/images/ADC_12bit_table.png?raw=true)

### Direct-Conversion ADC
![](https://www.maximintegrated.com/content/dam/images/design/tech-docs/634/E33Fig01.gif)

### Successive-Approximation ADC
![](https://github.com/rkuo2000/MCU-course/blob/main/images/SA_ADC_block_diagram.png?raw=true)

### Sigma-Delta ADC
![](https://github.com/csu6792/MCU-course/blob/main/images/Sigma-Delta_ADC_block_diagram.png?raw=true)

<img width="50%" height="50%" src="https://www.electronicwings.com/public/images/user_images/images/NodeMCU/NodeMCU%20Interfaces/NodeMCU%20Thermistor/NodeMCU_Thermistor_Interfacing_Diagram.png">
![](https://www.rfwireless-world.com/images/ESP32-Interfacing-with-Gas-Sensor.jpg)

---
## DAC (Digital to Analog Converter)
[Introduction to Digital-Analog Conversion](https://www.allaboutcircuits.com/textbook/digital/chpt-13/digital-analog-conversion/)

### Binary-Weighted Resistor DAC
![](https://www.allaboutcircuits.com/uploads/articles/inverting-summing-circuit-diagram.jpg)
![](https://www.allaboutcircuits.com/uploads/articles/6-bit-binary-weighted-DAC.jpg)

### [Sigma-Delta Digital Audio Converters (DAC)](https://www.audiosciencereview.com/forum/index.php?threads/sigma-delta-digital-audio-converters-dac.1928/)
![](https://www.audiosciencereview.com/forum/index.php?attachments/upload_2017-9-13_19-3-41-png.8688/)

Ref. [淺談 Delta-Sigma 之工作原理](https://picture.iczhiku.com/resource/eetop/WhiGYWWUksgpUBVn.pdf)

---
## PWM (Pulse Width Modulation)
![](https://github.com/csu6792/MCU-course/blob/main/images/PWM_functional_diagram.png?raw=true)
CMRx+1 >= CNR: PWM output high <br>
CMRx+1 <  CNR: PWM output low <br>

**PWM Frequency** = PWM_Clock/(prescale+1)*(clock divider)/(CNR+1) <br>

**Duty ratio** = (CMR+1)/(CNR+1)<br>

![](https://microcontrollerslab.com/wp-content/uploads/2019/04/Servo-motor-pinout-esp32.png)

--- 
## I2C (Inter-Integrated Circuit bus)
[I2C bus 簡介 ](https://magicjackting.pixnet.net/blog/post/173061691-i2c-bus-%E7%B0%A1%E4%BB%8B-(inter-integrated-circuit-bus)-)
<table>
<tr>
<td><img src="https://pic.pimg.tw/magicjackting/1447382351-2909185260.png"></td>
<td><img src="https://pic.pimg.tw/magicjackting/1447739085-239160220.png"></td>
</tr>
</table>
![](https://pic.pimg.tw/magicjackting/1450787341-3597609114_n.png?v=1461809344)
![](https://pic.pimg.tw/magicjackting/1461659401-258467416.png)

![](https://i1.wp.com/randomnerdtutorials.com/wp-content/uploads/2020/12/ESP32-MPU6050-Module-Accelerometer-Gyroscope-Temperature-Sensor-Arduino.jpg?resize=1024%2C576&quality=100&strip=all&ssl=1)

---
## SPI (Serial peripheral interface)
[Introduction to SPI Interface](https://www.analog.com/en/analog-dialogue/articles/introduction-to-spi-interface.html)<br>
4-wire SPI devices have four signals:<br>
* **CS**  : Chip select
* **SCLK**: SPI Clock
* **MOSI**: Master out, slave in
* **MISO**: Master in, slave out

![](https://www.analog.com/-/media/images/analog-dialogue/en/volume-52/number-3/articles/introduction-to-spi-interface/205973_fig_01.png?la=en&imgver=2)

**SPI Mode 0**, CPOL = 0, CPHA = 0: CLK idle state = low, data sampled on rising edge and shifted on falling edge.
![](https://www.analog.com/-/media/images/analog-dialogue/en/volume-52/number-3/articles/introduction-to-spi-interface/205973_fig_02.png?la=en&imgver=1)

**SPI Mode 1**, CPOL = 0, CPHA = 1: CLK idle state = low, data sampled on the falling edge and shifted on the rising edge.
![](https://www.analog.com/-/media/images/analog-dialogue/en/volume-52/number-3/articles/introduction-to-spi-interface/205973_fig_03.png?la=en&imgver=1)

**SPI Mode 2**, CPOL = 1, CPHA = 1: CLK idle state = high, data sampled on the falling edge and shifted on the rising edge.
![](https://www.analog.com/-/media/images/analog-dialogue/en/volume-52/number-3/articles/introduction-to-spi-interface/205973_fig_04.png?la=en&imgver=1)

**SPI Mode 3**, CPOL = 1, CPHA = 0: CLK idle state = high, data sampled on the rising edge and shifted on the falling edge.
![](https://www.analog.com/-/media/images/analog-dialogue/en/volume-52/number-3/articles/introduction-to-spi-interface/205973_fig_05.png?la=en&imgver=1)

**Multislave Configuration**
![](https://www.analog.com/-/media/images/analog-dialogue/en/volume-52/number-3/articles/introduction-to-spi-interface/205973_fig_06.png?la=en&imgver=2)

**Daisy-Chain Configuration**
![](https://www.analog.com/-/media/images/analog-dialogue/en/volume-52/number-3/articles/introduction-to-spi-interface/205973_fig_07.png?la=en&imgver=2)

![](https://alexlubbock.com/images/esp32-sd-card-wiring.jpg)
![](https://blog.jmaker.com.tw/content/images/2020/03/rfid-4.jpg)

---
## I2S (Inter-IC Sound bus)
[Introduction to the I2S Interface](https://www.allaboutcircuits.com/technical-articles/introduction-to-the-i2s-interface/)
![](https://www.allaboutcircuits.com/uploads/articles/introduction-to-the-i2s-interface_rk_aac_image1.jpg)
![](https://www.allaboutcircuits.com/uploads/articles/introduction-to-the-i2s-interface_rk_aac_image2.jpg)
![](https://diyi0t.com/wp-content/uploads/2020/08/I2S-ESP32-Play-from-Memory_Steckplatine.png)

---
## UART（Universal Asynchronous Receiver/Transmitter）序列埠
[BASICS OF UART COMMUNICATION](https://www.circuitbasics.com/basics-uart-communication/)
<img width="50%" height="50%" src="https://www.circuitbasics.com/wp-content/uploads/2016/01/Introduction-to-UART-Data-Transmission-Diagram.png">
![](https://makerpro.cc/wp-content/uploads/2019/08/2.png)

**DB9 Connector**<br>
<table>
<tr>
<td><img src="https://github.com/csu6792/MCU-course/blob/main/images/UART-DB9-pinout.png?raw=true"></td>
<td><img src="https://github.com/csu6792/MCU-course/blob/main/images/UART-DB9-signal_names.png?raw=true"></td>
</tr>
</table>

**Protocol 通訊協定**<br>
![](https://www.circuitbasics.com/wp-content/uploads/2016/01/Introduction-to-UART-Packet-Frame-and-Bits-2.png)
* Standard Packet : 8 data bits, even parity, 1 stop bit
  - If the parity bit is a 0 (even parity), the 1 bits in the data frame should total to an even number. 
  - If the parity bit is a 1 (odd parity), the 1 bits in the data frame should total to an odd number.
![](https://makerpro.cc/wp-content/uploads/2019/08/4.png)
RS232 的Vpp電壓較高，有 6V~30V；UART 則是較低的 3.3V 或 5V<br>
RS232 為負邏輯， UART 為正邏輯，因此兩者波形是反相的<br>
**Baud Rate**<br>
![](https://github.com/csu6792/MCU-course/blob/main/images/UART-baudrates.png?raw=true)

[The main differences between RS-232, RS-422 and RS-485](https://ipc2u.com/articles/knowledge-base/the-main-differences-between-rs-232-rs-422-and-rs-485/)
![](https://github.com/csu6792/MCU-course/blob/main/images/UART-RS232_RS422_RS485.png?raw=true)
![](https://ipc2u.com/upload/medialibrary/341/34187d2b0bb31eeb5b3fdfdb17745526.jpg)

---
## Sensors
### Photoresistor
Photoresistors, also known as light dependent resistors (LDR), are light sensitive devices most often used to indicate the presence or absence of light, or to measure the light intensity. In the dark, their resistance is very high, sometimes up to 1 MΩ, but when the LDR sensor is exposed to light, the resistance drops dramatically, even down to a few ohms, depending on the light intensity. 
![](https://eepower.com/uploads/education/photoresistor.png)

---
### Thermistor
[What is a Thermistor? Types of Thermistors and Applications](https://www.electricaltechnology.org/2021/11/thermistor.html)
![](https://www.electricaltechnology.org/wp-content/uploads/2021/11/What-is-a-Thermistor-Types-of-Thermistors-Construction-and-Applications-768x408.jpg)
Two types of Thermistor:<br>
* PTC (Positive Temperature Coefficient) Thermistor
* NTC (Negative Temperature Coefficient) Thermistor

---
### [MQ series gas sensors](https://robu.in/mq-series-gas-sensor/)
* MQ-2 - Methane, Butane, LPG, smoke<br>
* MQ-3 - Alcohol, Ethanol, smoke<br>
* MQ-4 - Methane, CNG Gas<br>
* MQ-5 - Natural gas, LPG<br>
* MQ-6 - LPG, butane gas<br>
* MQ-7 - Carbon Monoxide<br>
* MQ-8 - Hydrogen Gas<br>
* MQ-9 - Carbon Monoxide, flammable gasses<br>
* MQ131 - Ozone<br>
* MQ135 - Air Quality (CO, Ammonia, Benzene, Alcohol, smoke)<br>
* MQ136 - Hydrogen Sulfide gas<br>
* MQ137 - Ammonia<br>
* MQ138 - Benzene, Toluene, Alcohol, Acetone, Propane, Formaldehyde gas, Hydrogen<br>
* MQ214 - Methane, Natural gas<br>
![](https://sc04.alicdn.com/kf/H640ef54079864d858e41db553fb3d4235.jpg)

![](https://www.researchgate.net/profile/Alaa-Jaber/publication/334363772/figure/fig4/AS:779067213230082@1562755506381/Interfacing-the-DS18b20-temperature-sensor-to-NodeMCU.jpg)


<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


