# Cuttle2Fish

[[https://github.com/tahnok/cuttle2fish]]

## TODO

 - what pins are used for ADC?

## Ordering

[Digikey cart](https://www.digikey.ca/short/j1jpdr)

## STM32F103

[datasheet](/cuttle2fish/stm32f103c8.pdf)

Specifically the STM32F103RBT7 or STM32F103RBT6: the 128KB model in the 64 LQFP package

Order info on [digikey (CA)](https://www.digikey.ca/product-detail/en/stmicroelectronics/STM32F103RBT7/497-11526-ND/2035337)

### Oscillator

For USB we need an external clock source / crystal. Typically an 8 MHz crystal is used. MMVDM pi-hat uses 20pF caps, as does bluepill

 - [Blue pill includes a 1M resistor](https://wiki.stm32duino.com/images/c/c1/Vcc-gnd.com-STM32F103C8-schematic.pdf)
 - [openCM does not](http://support.robotis.com/en/baggage_files/opencm/opencm904_rev_10_final_schematic.pdf)
 - official st-link does not have reistors (seen in nucleo datasheet?)
 - nucleo board does have 2 resistors
 - [unofficial st-link v2](http://www.micromouseonline.com/wp/wp-content/uploads/2014/01/mini-st-link-v2.png)
 - [FST-01](https://www.gniibe.org/images/FST-01/Fst-01-schematic.png) has no resistors

[oscillator design by ST](https://www.st.com/content/ccc/resource/technical/document/application_note/c6/eb/5e/11/e3/69/43/eb/CD00221665.pdf/files/CD00221665.pdf/jcr:content/translations/en.CD00221665.pdf)

> 5 or 6 pF of stray capacitance is a good budget, I think - for hobby stuff, no need to actually calculate that. Use the load capacitance from the crystal data sheet (probably something like 12pF or 18pF), and find capacitor values that solve the equation. Choose the nearest standard value, and you're good.

> The way the math works out is that C = 2(Cl - Cs), where Cl is the load capacitance of the crystal. So an 18pF crystal needs 2(18-6) = 24pF load capacitors. I think 22pF is the closest standard value

Chose to use a 5mm x 3.2mm crystal with 4 leads (ground on pins 2,4)

The GX531S-8.000KKF1001 on OPL and equivalent package on [digikey](https://www.digikey.ca/product-detail/en/ecs-inc/ECS-80-10-30B-CWN-TR/XC2708TR-ND/8023325)

## RGB LEDs

### WS2812 (aka Neopixels)

https://octopart.com/search?q=ws2812-smd&start=0&oq=ws2812

[stm32 project with impl](https://github.com/hwhw/stm32-projects)

### APA102 / SK9822

[APA102 2020 datasheet](http://www.led-color.com/upload/201604/APA102-2020%20SMD%20LED.pdf)

[footprint from GreatScottGadgets](https://github.com/greatscottgadgets/gsg-kicad-lib/blob/master/gsg-modules.pretty/APA102-2020.kicad_mod)

[writeup of protocol](https://cpldcpu.wordpress.com/2014/08/27/apa102/) (basically SPI)

[avr lib](https://github.com/cpldcpu/light_ws2812/tree/master/light_apa102_AVR)

[SK9822 info](https://cpldcpu.wordpress.com/2016/12/13/sk9822-a-clone-of-the-apa102/)

[Adafruit product page](https://www.adafruit.com/product/3341)

Going to use the APA102 in 2020 package because it seems fun and SPI should be easy to use

## U2F

[u2f-token firmware](https://github.com/gl-sergei/u2f-token), which uses GNUK and [NEUG](https://www.gniibe.org/memo/development/gnuk/rng/neug.html)

Depends on button being on PB8

### ADC

Neug uses ADC1 and ADC2 with 2 channels. Current question, which pins are those channels on? Want to have nice long wavy traces out of those pins for Extra Noise

## Power

[PMIC / LDO / Voltage maker: LP2985](https://www.digikey.ca/product-detail/en/texas-instruments/LP2985-33DBVR/296-18476-1-ND/809911)

~70 mA for STM32F1 (in current consumption section), with max "draw" of 150 mA

APA102 2020 takes about 30 mA

## Button

Using a SPST button: B3U-1000P [digikey](https://www.digikey.ca/product-detail/en/omron-electronics-inc-emc-div/B3U-1000P/SW1020CT-ND/1534357)

## USB

Using a USB PCB footprint from [USBArmory](https://github.com/inversepath/usbarmory)

## Dimensions

23 x 47 mm

## References

[stm32f103 order information](https://i.imgur.com/LTHdG1Q.png)

[[/cuttle2fish/stmp32-64-lqfp.png]]

## similar projects

 - Bluepill: [schematic](https://wiki.stm32duino.com/images/c/c1/Vcc-gnd.com-STM32F103C8-schematic.pdf)
 - MMDVM_HS Pi Hat: [[https://github.com/mathisschmieder/MMDVM_HS_Hat]]
 - Black Magic Probe: [[https://github.com/blacksphere/blackmagic/wiki]]
 - FST-01: [[https://www.gniibe.org/FST-01/fst-01.html]]
 - micro-bmp: [[https://github.com/korken89/micro-bmp/blob/master/ubmp_v1.pdf]]
 - trinket m0: [schematic](https://cdn-learn.adafruit.com/assets/assets/000/045/723/original/adafruit_products_schem.png?1503525048) [learn](https://learn.adafruit.com/adafruit-trinket-m0-circuitpython-arduino/downloads)

