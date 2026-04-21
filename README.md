
# Proiect - Ink Time
**Autor:** Baltag Constantin

## 1. Diagramă Bloc
Diagrama reprezintă arhitectura sistemului InkTime, având în centru microcontrolerul nRF52840.Acesta este conectat prin magistrale dedicate (I2C, SPI, PWM) la senzorii de mișcare, ecranul E-Paper și motorul de vibrații, asigurând o gestionare eficientă a consumului și a interacțiunii.



## 2. Bill Of Materials (BOM)
Mai jos este tabelul cu componentele utilizate, conform specificațiilor proiectului și listei JLC Parts:

| Componentă / Valoare | Cant. | Capsulă | Producător / PN | Sursă (JLC Parts) | Datasheet |
| :--- | :---: | :--- | :--- | :--- | :--- |
| **nRF52840-QIAA** | 1 | aQFN-73 | Nordic | [C115598](https://jlcpcb.com/partdetail/NordicSemicon_nRF52840QIAA/C115598) | [Link](https://infocenter.nordicsemi.com/pdf/nRF52840_PS_v1.1.pdf)  |
| **LSM6DS3TR-C** | 1 | LGA-14L | ST | [C134015](https://jlcpcb.com/partdetail/STMicroelectronics_LSM6DS3TRC/C134015) | [Link](https://www.st.com/resource/en/datasheet/lsm6ds3.pdf)  |
| **Waveshare 1.54inch E-Paper Module** | 1 | FPC-24P | Waveshare | [C2904555](https://jlcpcb.com/partdetail/Waveshare_154inchE_PaperModule/C2904555) | [Link](https://www.waveshare.com/wiki/1.54inch_e-Paper_Module)  |
| **Fit0774** | 1 | SMD | DFRobot | [C3016423](https://jlcpcb.com/partdetail/Fit0774/C3016423) | [Link](https://wiki.dfrobot.com/Micro_Vibration_Motor_3_7V_SKU_FIT0774)  |
| **KH-TYPE-C-16P** | 1 | SMD | Kinghelm | [C710729](https://jlcpcb.com/partdetail/Kinghelm_KHTYPEC16P/C710729) | [Link](https://datasheet.lcsc.com/lcsc/2108132230_Kinghelm-KH-TYPE-C-16P_C710729.pdf)  |

## 3. Descriere Hardware și Funcționalitate
InkTime este un smartwatch proiectat pentru a fi ieftin și open-source, optimizat pentru consum minim de energie.

* **Microcontroler:** SoC nRF52840 gestionează procesarea și comunicarea radio (Bluetooth 5.0).
* **Senzori:** IMU LSM6DS3TR-C este utilizat pentru detecția mișcării, comunicând prin interfața **I2C**.
* **Display:** Ecranul E-Paper oferă o citire excelentă și consum minim, fiind conectat prin **SPI**.
* **Feedback:** Motorul de vibrații (shaker) oferă notificări haptice controlate prin semnal **PWM**.
* **Alimentare:** Include un circuit de încărcare pentru bateria LiPo, mufa USB-C fiind utilizată pentru alimentare și debug.

## 4. Configurație Pini (nRF52840)
Alocarea pinilor a fost realizată pentru a respecta cerințele de design și rutare:

| Pin | Funcție | Destinație | Motivație |
| :--- | :--- | :--- | :--- |
| **P0.17** | CS | Display SPI | Selecția cipului pentru comunicația SPI. |
| **P0.19** | CLK | Display SPI | Semnal de ceas sincronizat. |
| **P0.26** | SDA | IMU I2C | Transfer serial de date I2C. |
| **P0.27** | SCL | IMU I2C | Semnal de ceas I2C. |
| **P1.01** | PWM | Shaker | Controlul intensității vibrațiilor. |
| **P0.13** | Input | Buton | Detectarea interacțiunii utilizatorului. |

