# TEF668X Headless Lite USB Tuner

USB radio tuner based on the STM32F072 MCU and TEF668X/V205 RF receiver with digital audio output over USB. This is the lite variant of our [Headless USB tuner](https://github.com/FMDX-org/tef668x-headless-usb-tuner). It is more compact, with a simplified RF input path and only one antenna input for AM/FM.

This design is optimized as a cost-efficient solution tailored for automated PCBA (Printed Circuit Board Assembly) processes.

Copyright (C) 2025 FMDX.org

You may redistribute and modify this source under the terms of the CERN-OHL-W v2 (see LICENSE file).

![Headless TEF Lite](https://github.com/FMDX-org/headless-tef-lite/blob/main/Headless_TEF_lite.png)

# Credits 

- Konrad Kosmatka - HW & FW architecture and development
- Sjef Verhoeven - HW development
- Marek Kraus - HW & FW prototyping
- Marek Farkaš - testing and integration with FM-DX Webserver
- Przemysław Korpas - HW consultation, reviews
- Sebastian Białkowski - HW consultation, reviews

# Firmware

The firmware is available in a separate repository: [FM-DX-Tuner](https://github.com/kkonradpl/FM-DX-Tuner).

Firmware dependencies:
- Board: STM32 MCU Based Boards ([STM32duino](https://github.com/stm32duino)) - download using board manager
- Library: [TinyUSB](https://github.com/hathach/tinyusb) - install manually to the Arduino libraries

During first firmware flashing, short BOOT to 3.3V, plug the USB cable and flash using Arduino IDE (DFU method). Once the firmware is running, it is not necessary to manually short BOOT pin. See [tef-bootloader](https://github.com/kkonradpl/tef-bootloader).

# Audio output

The baseline version of the tuner supports only digital audio over USB. You can access analog audio via the L and R solder points, but this output is unbuffered. Therefore, you will need to build an additional electronic circuit to achieve proper audio output.

# Important remarks

- TEF6687/V205 (F8705) chip is recommended for the best performance (FMSI, FULL SCAN RDS).
- RF circuits should contain NP0 (C0G) capacitors.
- Only V205 version of TEF668X are supported on this design!
- All capacitors and resistors are 0402.
