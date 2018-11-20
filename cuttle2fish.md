# Cuttle2Fish

[[https://github.com/tahnok/cuttle2fish]]

## TODO

 - what pins to I need to expose for programming?
   - [SWDIO and SWCLK](https://madnessinthedarkness.transsys.com/blog:2017:0122_black_magic_probe_bmp_on_st-link_v2_clones), reset, power, gnd
 - do I want a user button?
 - what LEDs do I want to use? (APA or WS2812)
  - APA seem super hard to find, WS2812 instead
 - what do I use for 5V -> 3.3V conversion?


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

## RGB LEDs

### WS2812 (aka Neopixels)

https://octopart.com/search?q=ws2812-smd&start=0&oq=ws2812

[stm32 project with impl](https://github.com/hwhw/stm32-projects)

### APA102 / SK9822

[writeup of protocol](https://cpldcpu.wordpress.com/2014/08/27/apa102/) (basically SPI)

[avr lib](https://github.com/cpldcpu/light_ws2812/tree/master/light_apa102_AVR)

[SK9822 info](https://cpldcpu.wordpress.com/2016/12/13/sk9822-a-clone-of-the-apa102/)

## References

![order information](https://i.imgur.com/LTHdG1Q.png)

[[/cuttle2fish/stmp32-64-lqfp.png]]

## similar projects

 - Bluepill: [schematic](https://wiki.stm32duino.com/images/c/c1/Vcc-gnd.com-STM32F103C8-schematic.pdf)
 - MMDVM_HS Pi Hat: [[https://github.com/mathisschmieder/MMDVM_HS_Hat]]
 - Black Magic Probe: [[https://github.com/blacksphere/blackmagic/wiki]]
 - FST-01: [[https://www.gniibe.org/FST-01/fst-01.html]]
 - micro-bmp: [[https://github.com/korken89/micro-bmp/blob/master/ubmp_v1.pdf]]

