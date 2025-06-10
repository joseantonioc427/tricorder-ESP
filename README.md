# Tricorder ESP32-S3

Proyecto completo para construir un **Tricorder** con ESP32-S3, pantalla TFT, audio y 5 botones, inspirado en la tecnología de Star Trek.  
Incluye animaciones GIF, sonidos, y manejo de archivos en SPIFFS.  
Ideal para makers, fans de la ciencia ficción y aprendizaje de electrónica avanzada con ESP32.

---

## Tabla de Contenidos

- [Características](#características)
- [Lista de Materiales](#lista-de-materiales)
- [Esquema de Conexiones](#esquema-de-conexiones)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Instrucciones de Instalación](#instrucciones-de-instalación)
- [Uso del Tricorder](#uso-del-tricorder)
- [Recursos y Créditos](#recursos-y-créditos)
- [Licencia](#licencia)

---

## Características

- Basado en **ESP32-S3** compatible con Arduino IDE.
- Pantalla TFT 1.8" (ST7735S) para mostrar animaciones GIF.
- Salida de audio I2S usando MAX98357A y altavoz.
- 5 botones físicos para cambiar modos y sonidos.
- Almacenamiento de archivos en SPIFFS (GIFs y WAVs).
- Código bien documentado y modular.
- Incluye esquemas de conexión y guía en español.

---

## Lista de Materiales

- 1x ESP32-S3 DevKit (o equivalente)
- 1x Pantalla TFT 1.8" ST7735S (7 pines)
- 1x MAX98357A (DAC I2S a audio)
- 1x Altavoz 8Ω 1W
- 5x Botones pulsadores
- Cables Dupont y protoboard o PCB
- Fuente de alimentación 5V/USB
- (Opcional) Resistencias de pull-down para botones

---

## Esquema de Conexiones

### **Pantalla TFT (ST7735S 7 pines)**

| TFT Pin | ESP32-S3 GPIO |
|---------|---------------|
| VCC     | 3V3           |
| GND     | GND           |
| SCL     | 18            |
| SDA     | 23            |
| DC      | 5             |
| RST     | 4             |
| CS      | 15            |

### **Botones**

| Botón    | ESP32-S3 GPIO |
|----------|---------------|
| Botón 1  | 12            |
| Botón 2  | 13            |
| Botón 3  | 14            |
| Botón 4  | 16            |
| Botón 5  | 17            |

- Un extremo de cada botón a GND, el otro al GPIO correspondiente.
- (Opcional) Añadir resistencia de 10kΩ a GND si no usas INPUT_PULLUP.

### **MAX98357A (Audio I2S)**

| MAX98357A Pin | ESP32-S3 GPIO |
|---------------|---------------|
| VCC           | 3V3           |
| GND           | GND           |
| LRCK/WS       | 25            |
| BCLK          | 26            |
| DIN           | 22            |
| SD/GAIN       | Sin conectar  |

- Salida del MAX98357A a altavoz 8Ω.

---

### **Imagen de conexiones (Fritzing)**
Incluye el archivo `conexiones.png` y el esquema de texto en `Fritzing_Conexiones.txt`.  
Puedes usar Fritzing para visualizar y modificar el esquema.

---

## Estructura del Proyecto

```
tricorder-ESP/
├── tricorder_esp32s3.ino                 # Código principal de Arduino
├── README.md                             # Este archivo
├── Fritzing_Conexiones.txt               # Descripción textual del esquema
├── TRICORDER_ESP32S3_INSTRUCCIONES.txt   # Guía completa paso a paso
├── conexiones.png                        # Imagen de conexiones eléctrica
└── data/                                 # Carpeta para archivos SPIFFS
    ├── group1_1.gif
    ├── group1_1.wav
    ├── group1_2.gif
    ├── group1_2.wav
    ├── group1_3.gif
    ├── group1_3.wav
    ├── group2_1.gif
    ├── group2_1.wav
    ├── group2_2.gif
    ├── group2_2.wav
    ├── group2_3.gif
    ├── group2_3.wav
    ├── alarm.gif
    └── alarm.wav
```

---

## Instrucciones de Instalación

1. **Instala el ESP32 en el IDE Arduino**  
   - Ve a Archivo > Preferencias > URLs adicionales de tarjetas  
   - Añade: `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`  
   - Herramientas > Placa: ESP32S3 Dev Module

2. **Instala las librerías necesarias**  
   - Adafruit_ST7735 and ST7789 Library
   - Adafruit_GFX Library
   - ESP32-audioI2S (puede ser "ESP32-audioI2S" de schreibfaul1)
   - GIFDecoder
   - FS, SPIFFS (incluidas en ESP32)

3. **Carga el código y archivos SPIFFS**  
   - Copia el contenido de la carpeta `data/` en la tuya.
   - Usa "Herramientas > ESP32 Sketch Data Upload" para cargar archivos en SPIFFS.
   - Sube el sketch `tricorder_esp32s3.ino` al ESP32-S3.

4. **Conecta los componentes siguiendo el esquema.**

---

## Uso del Tricorder

- Al encender, la pantalla mostrará animaciones y sonidos según el botón pulsado.
- Puedes añadir o cambiar archivos GIF/WAV en la carpeta `data/` y re-cargar con "ESP32 Sketch Data Upload".
- Cada botón puede asociarse a una animación y sonido diferente (ver código `.ino`).

---

## Recursos y Créditos

- Basado en ejemplos de:
  - [ESP32-audioI2S](https://github.com/schreibfaul1/ESP32-audioI2S)
  - [Adafruit ST7735](https://github.com/adafruit/Adafruit-ST7735-Library)
  - [GIFDecoder](https://github.com/bitbank2/GifDecoder)
- Inspirado en el universo Star Trek.

---

## Licencia

Este proyecto es de código abierto y se distribuye bajo la licencia MIT.  
Puedes usarlo, modificarlo y compartirlo citando al autor original.

---

¿Dudas, mejoras o quieres contribuir?  
¡Abre un issue o pull request en este repositorio!
