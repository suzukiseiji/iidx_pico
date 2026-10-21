# Beatmania IIDX Pico - Custom MX Hand-Wired Edition

Mini controlador de Beatmania IIDX estilo arcade, baseado no projeto open-source [whowechina/iidx_pico](https://github.com/whowechina/iidx_pico) adaptado para montagem **Hand-Wired (sem PCB comercial)** com **Switches Mecânicos MX Brown** e microcontrolador **RP2040-Zero**.

---

## 🛠️ Especificações do Hardware

* **Microcontrolador:** Estardyn RP2040-Zero (Raspberry Pi RP2040, 2MB Flash, USB-C, 1000Hz polling rate).
* **Switches:** 7x Switches mecânicos padrão MX (Outemu/Cherry/Gateron Brown).
* **Keycaps:** Teclas 3D estilo arcade retangulares com haste em cruz (`Keycap - Pico Choc V2.stl`).
* **Switch Plate:** Placa de sustentação 1.6mm com recortes padrão 14x14mm (`Keyboard - Switch_Plate_MX.stl`).
* **Turntable (Disco):** 
  * Sensor Magnético: **AS5600 12-bit I2C** + Ímã neodímio 5x2mm diametral/radial.
  * Rolamento: **61804-2RS / 6804-2RS** (20x32x7mm).

---

## ⚡ Pinout e Ligações Elétricas (RP2040-Zero)

O firmware utiliza pull-up interno ativo. Todos os switches fecham contato com o **GND**.

### 1. Teclas Principais (Switches MX)

| Tecla IIDX | Cor Tradicional | Pino no RP2040-Zero | Outro Terminal do Switch |
| :--- | :--- | :--- | :--- |
| **Key 1** | Branca | **GP8** | GND |
| **Key 2** | Preta | **GP7** | GND |
| **Key 3** | Branca | **GP6** | GND |
| **Key 4** | Preta | **GP5** | GND |
| **Key 5** | Branca | **GP4** | GND |
| **Key 6** | Preta | **GP3** | GND |
| **Key 7** | Branca | **GP2** | GND |

### 2. Sensor do Turntable (Módulo AS5600)

| Pino no Módulo AS5600 | Pino no RP2040-Zero | Função |
| :--- | :--- | :--- |
| **VCC** | **3V3** (3.3V) | Alimentação de energia |
| **GND** | **GND** | Terra de referência |
| **SCL** | **GP27** | Clock I2C |
| **SDA** | **GP26** | Dados I2C |
| **DIR** | **GND** | Sentido horário padrão |

---

## 📂 Estrutura de Arquivos

* 📁 **`3DPrint/`**
  * `Keyboard - Panel.stl` — Painel superior (moldura guia das teclas)
  * `Keyboard 1P - Base.stl` — **Base inferior já estendida em +6 mm (13 mm total) para acomodar perfeitamente os switches Outemu MX Brown e a fiação manual**
  * `Keyboard - Switch_Plate_MX.stl` — **Placa de sustentação 1.6 mm com furos 14x14 mm para os switches MX**

  * `Keycap - Pico Choc V2.stl` — Teclas (4x Brancas, 3x Pretas)
  * `Turntable Pico - Base.stl` — Base do disco
  * `Turntable Pico - Disc.stl` — Disco giratório
  * `Turntable Pico - Banner.stl` — Plaquinha superior de acabamento
  * `Turntable - Bearing Seat.stl` — Berço para o rolamento 61804 (20x32x7mm)
  * `Turntable - Disc Seat.stl` — Acoplador entre rolamento e disco
  * `Turntable - Magnet Seat.stl` — Eixo com alojamento para o ímã 5x2mm
* 📁 **`Firmware/`**
  * `iidx_pico.uf2` — Firmware compilado pronto (1000Hz HID Gamepad)
* 📁 **`Docs/`**
  * `IIDX_Pico_Manual.pdf` — Manual oficial do projeto
  * `PECAS_PARA_IMPRESSAO_3D.txt` — Lista completa com instruções para fatiamento e impressão

---

## 🚀 Como Gravar o Firmware no RP2040-Zero

1. Conecte a placa ao PC segurando o botão **BOOT** e aperte **RESET** uma vez.
2. O Windows abrirá a unidade removível **`RPI-RP2`**.
3. Copie o arquivo `Firmware/iidx_pico.uf2` para dentro da unidade `RPI-RP2`.
4. A placa reiniciará instantaneamente como um **Controlador de Jogo USB de 1000Hz**.
