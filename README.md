# OpenBook E-book Reader

#### Autor: Voicu Andrei-Silviu

## Descriere generală

OpenBook este un e-reader open-source construit în jurul microcontrollerului ESP32-C6. Dispozitivul folosește un ecran e-paper de 7.5", senzori de mediu, monitorizare baterie și conectivitate USB-C & Wi-Fi.

## Diagramă bloc

```plaintext
         +---------------------+
         |      Li-Po Cell     |
         +---------+-----------+
                   |
                   v
         +---------------------+
         |   Battery Charger   |  <--- USB-C 5V
         |    MCP73832 IC      |
         +---------+-----------+
                   |
                   v
         +---------------------+
         |   3.3V Regulator    | ---> VCC (3.3V Rail)
         +---------+-----------+
                   |
        +----------+-----------+-----------------------+
        |          |           |                       |
        v          v           v                       v
   +---------+ +------------+ +------------------+ +------------------+
   | ESP32-C3| | E-Ink Disp | |   BME688 Sensor  | |   Push Buttons   |
   |   -C6   | |  (SPI 4W)  | |    (I2C Comm)    | |  (GPIO + RC net) |
   +----+----+ +------------+ +--------+---------+ +--------+---------+
        |                           ^                        ^
        |                           |                        |
        |                     Pull-up Res.             Debounce Filter
        |
        v
   +-----------------------------+
   |     USB Type-C Connector    |
   | ↔ USB Data to ESP32 UART    |
   |    + ESD & Termination      |
   +-----------------------------+
```

## Listă de componente (BOM)

| Componenta    | Link | Datasheet
| -------- | ------- |--------|
|BUTTON_CUSYOMV1|https://industry.panasonic.com/global/en/downloads?tab=cad&small_g_cd=203&part_no=EVQPUJ02K&q=RVZRUFVKMDJLJTdDMTMlN0MyMDMlN0MzNDU5JTdDMSU3QyU3QyU3Q2ZhbHNl|https://industry.panasonic.com/global/en/downloads?tab=catalog&small_g_cd=203&part_no=EVQPUJ02K&q=RVZRUFVKMDJLJTdDMTMlN0MyMDMlN0MzNDU5JTdDMSU3QyU3QzIlN0NmYWxzZQ%3D%3D
|ESP32_WROVER_EAGLE-LTSPICE_CC0402|https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO|https://componentsearchengine.com/Datasheets/2/CC0402MRX5R5BB106.pdf
| QWIIC_CONNECTORJS-1MM | https://www.snapeda.com/parts/PRT-14417/SparkFun/view-part/     |https://www.snapeda.com/parts/PRT-14417/SparkFun%20Electronics/datasheet/
|112A-TAAR-R03_ATTEND|https://store.comet.bg/en/Catalogue/Product/43497/|https://store.comet.bg/en/Catalogue/Product/43497/|
|ADAFRUIT_LEDCHIP-LED0603|https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603|https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/datasheet/
|744043680IND_4828-WE-TPC_WRE|https://www.digikey.sg/en/models/1638515|https://www.we-online.com/components/products/datasheet/744043680.pdf
|ESP32_WROVER_EAGLE-LTSPICE_CC0402|https://componentsearchengine.com/Datasheets/2/CC0402MRX5R5BB106.pdf|https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO|
|CPH3225A|https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda|https://www.snapeda.com/parts/CPH3225A/Seiko%20Instruments/datasheet/|
|DS3231SN|https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=eda|https://www.snapeda.com/parts/DS3231SN%23/Analog%20Devices/datasheet/|
|SJ|https://grabcad.com/library/solder-jumpers-1||
|CPH3225A|https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda|https://www.snapeda.com/parts/CPH3225A/Seiko%20Instruments/datasheet/|
|MCP73831|https://www.digikey.com/en/models/1874108|https://ww1.microchip.com/downloads/aemDocuments/documents/APID/ProductDocuments/DataSheets/MCP73831-Family-Data-Sheet-DS20001984H.pdf|
|RCL_CPOL-EUCT3528|https://ro.mouser.com/ProductDetail/Vishay-Sprague/TR3B106K025C1300?qs=jCGqFXxTmLdffnuDkXzk1g%3D%3D|https://www.vishay.com/docs/40080/tr3.pdf|
|ESP32_WROVER_BME680_BME680|https://www.snapeda.com/parts/BME680/Bosch/view-part/?welcome=home|https://www.snapeda.com/parts/BME680/Bosch%20Sensortec/datasheet/|
|ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_PCH-DMG2305UX-7|https://componentsearchengine.com/part-view/DMG2305UX-7/Diodes%20Incorporated|https://www.diodes.com//assets/Datasheets/DMG2305UX.pdf|
|BD5229G-TR|https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor|https://datasheet.datasheetarchive.com/originals/distributors/Datasheets_SAMA/f2b9741ef86007909f138d561a359946.pdf|
|ESP32C6_VARISTORCN1812|https://www.mouser.co.uk/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D|https://www.tdk-electronics.tdk.com/inf/75/db/CTVS_14/Surge_protection_series.pdf|
|USBLC6-2SC6Y|https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda|https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/datasheet/|
|W25Q512JVEIQ|https://www.snapeda.com/parts/W25Q512JVEIQ/Winbond+Electronics/view-part/?ref=eda|https://www.snapeda.com/parts/W25Q512JVEIQ/Winbond%20Electronics/datasheet/|
|XC6220A331MR-G|https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex|https://product.torexsemi.com/system/files/series/xc6220.pdf|
|ESP32-C6-WROOM-1-N8|https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda|https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif%20Systems/datasheet/
| ESP32_WROVER_EAGLE-LTSPICE_RR0402  | https://www.snapeda.com/parts/RC0402FR-07226RL/Yageo/view-part/    |https://www.snapeda.com/parts/RC0402FR-07226RL/Yageo/datasheet/
|FH34SRJ-24S-0.5SH_99_|https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex|https://product.torexsemi.com/system/files/series/xc6220.pdf|
|SAMACSYS_PARTS_USB4110-GF-A|https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY)|https://gct.co/files/drawings/usb4110.pdf|
|MAX17048G+T10|https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=eda|https://www.snapeda.com/parts/MAX17048G+T10/Analog%20Devices/datasheet/|
|PGB1010603MR|https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda|https://www.snapeda.com/parts/PGB1010603MR/Littelfuse%20Inc./datasheet/|
|SI1308EDL-T1-GE3|https://componentsearchengine.com/part-view/SI1308EDL-T1-GE3/Vishay|https://componentsearchengine.com/Datasheets/1/SI1308EDL-T1-GE3.pdf|
|MBR0530|https://ro.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D|https://ro.mouser.com/datasheet/2/40/schottky-3165252.pdf|

## Componente principale

#### ESP32-C6-WROOM-1-N8
- MCU principal, Wi-Fi 6, Bluetooth 5
- Interfețe: SPI, I2C, UART, GPIO
- 160MHz, 512KB SRAM, 8MB Flash

#### Senzor BME688
- Măsoară: temperatură, umiditate, presiune, VOC
- I2C, consum redus: <1mA

#### Ecran E-Paper
- Diagonală: 7.5”
- Conectare prin SPI
- Consum 0 în stare statică

#### Sistem de Alimentare
- Baterie: 3.7V Li-Po 2500mAh
- Încărcare: MCP73831, max 1A
- Monitorizare: MAX17048 (Fuel Gauge)
- Consum tipic:
- Activ: ~150mA
- Standby: ~10mA
- Deep Sleep: <50µA
- Autonomie: ~250h la 10mA

#### Conectivitate USB-C
- Încărcare & date (USB 2.0)
- Protecție ESD: USBLC6-2SC6Y

## Alocare pini ESP32-C6

| *Pin ESP32-C6* | *Funcție*         | *Componentă*         | *Rol*                                    |
|------------------|--------------------|------------------------|--------------------------------------------|
| GPIO0           | BOOT_BUTTON        | Buton                  | Mod boot la inițializare                   |
| GPIO1           | RESET_BUTTON       | Buton                  | Reset manual                               |
| GPIO2           | CHANGE_BUTTON      | Buton                  | Schimbare meniuri                          |
| GPIO3           | EPD_CS             | Display E-Paper        | Chip Select pentru SPI                     |
| GPIO4           | EPD_DC             | Display E-Paper        | Control Date/Comenzi                       |
| GPIO5           | EPD_RST            | Display E-Paper        | Reset display                              |
| GPIO6           | EPD_BUSY           | Display E-Paper        | Detectare stare refresh                    |
| GPIO7           | SPI_MOSI           | Display, Flash, SD     | Linii de date SPI                          |
| GPIO8           | SPI_MISO           | Display, Flash, SD     | Linie de date SPI (citire)                 |
| GPIO9           | SPI_SCK            | Display, Flash, SD     | Semnal de ceas SPI                         |
| GPIO10          | FLASH_CS           | Memorie Flash          | Chip Select pentru memorie                 |
| GPIO11          | SD_CS              | Card Micro SD          | Chip Select pentru card SD                 |
| GPIO12          | I2C_SDA            | BME680, MAX17048, DS3231 | Linie de date pentru I2C                   |
| GPIO13          | I2C_SCL            | BME680, MAX17048, DS3231 | Linie de ceas pentru I2C                   |
| GPIO14          | CHG_LED            | LED                    | Indică procesul de încărcare               |
| GPIO15          | UART_TX            | Debugging              | Transmitere date seriale                    |
| GPIO16          | UART_RX            | Debugging              | Recepție date seriale                       |
| GPIO17          | USB_D+             | USB-C                  | Linie de date USB pozitivă                  |
| GPIO18          | USB_D-             | USB-C                  | Linie de date USB negativă                  |
