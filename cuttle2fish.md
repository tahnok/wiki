# Cuttle2Fish

https://github.com/tahnok/cuttle2fish


## STM32F103

[datasheet](https://www.st.com/resource/en/datasheet/stm32f103c8.pdf)

Specifically the STM32F103RBT7 or STM32F103RBT6: the 128KB model in the 64 LQFP package

Order info on [digikey (CA)](https://www.digikey.ca/product-detail/en/stmicroelectronics/STM32F103RBT7/497-11526-ND/2035337)

### Oscillator

For USB we need an external clock source / crystal. Typically an 8 MHz crystal is used. MMVDM pi-hat uses 20pF caps, as does bluepill

Blue pill includes a 1M resistor

[oscillator design by ST](https://www.st.com/content/ccc/resource/technical/document/application_note/c6/eb/5e/11/e3/69/43/eb/CD00221665.pdf/files/CD00221665.pdf/jcr:content/translations/en.CD00221665.pdf)

Could add a spot for one and just not solder it

## References

![order information](https://i.imgur.com/LTHdG1Q.png)

![pinout for LQFP64](https://i.imgur.com/edXdVsk.png)

## similar projects

Bluepill: [schematic](https://wiki.stm32duino.com/images/c/c1/Vcc-gnd.com-STM32F103C8-schematic.pdf)

MMDVM_HS Pi Hat: https://github.com/mathisschmieder/MMDVM_HS_Hat