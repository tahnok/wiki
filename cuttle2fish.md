# Cuttle2Fish

[[https://github.com/tahnok/cuttle2fish]]


## STM32F103

[datasheet](https://www.st.com/resource/en/datasheet/stm32f103c8.pdf)

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

## References

![order information](https://i.imgur.com/LTHdG1Q.png)

![pinout for LQFP64](https://i.imgur.com/edXdVsk.png)

## similar projects

Bluepill: [schematic](https://wiki.stm32duino.com/images/c/c1/Vcc-gnd.com-STM32F103C8-schematic.pdf)

MMDVM_HS Pi Hat: https://github.com/mathisschmieder/MMDVM_HS_Hat