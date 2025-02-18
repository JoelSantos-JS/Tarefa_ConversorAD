# Projeto: Conversores A/D no Raspberry Pi Pico

Este projeto implementa a leitura de um **joystick analógico** usando um **Conversor Analógico-Digital (ADC)** no **Raspberry Pi Pico**. O joystick controla a **intensidade dos LEDs RGB** via **PWM** e move um quadrado na tela do **display OLED SSD1306** via **I2C**. Além disso, o projeto inclui **interrupções de botões (IRQ) com debounce**.

---

## 📌 **Funcionalidades**
✅ **Leitura do Joystick (ADC)**: Captura os valores dos eixos **X e Y**.  
✅ **Controle dos LEDs RGB (PWM)**: Ajusta a intensidade do **LED Vermelho e Azul** conforme o joystick.  
✅ **Display OLED (SSD1306 - I2C)**: Exibe um **quadrado móvel** que se desloca com o joystick.  
✅ **Botão do Joystick**: Alterna o **LED Verde** e muda a borda do display.  
✅ **Botão A**: Ativa/desativa o controle dos LEDs RGB.  
✅ **Debounce e Interrupções (IRQ)**: Evita leituras repetitivas nos botões.  

---

## 🛠 **Hardware Utilizado**
- **Microcontrolador:** Raspberry Pi Pico  
- **Joystick Analógico:** Conectado às portas **ADC 26 e ADC 27**  
- **LEDs RGB:** Conectados aos pinos **11, 12 e 13 (PWM)**  
- **Botões:**  
  - **Botão do Joystick:** GPIO **22**  
  - **Botão A:** GPIO **5**  
- **Display OLED SSD1306:** Comunicação via **I2C (GPIO 14 e 15)**  

### **📌 Mapeamento dos Pinos**
| Componente        | GPIO  |
|------------------|------|
| **LED Vermelho** | 11   |
| **LED Verde**    | 12   |
| **LED Azul**     | 13   |
| **Joystick X**   | 26 (ADC) |
| **Joystick Y**   | 27 (ADC) |
| **Botão Joystick** | 22 |
| **Botão A** | 5 |
| **I2C SDA (Display)** | 14 |
| **I2C SCL (Display)** | 15 |

---

## 🚀 **Compilação e Upload**
### **1️⃣ Instale o SDK do Raspberry Pi Pico**
Se ainda não tiver o SDK instalado, siga as instruções do [Raspberry Pi Pico SDK](https://github.com/raspberrypi/pico-sdk).

```bash
git clone https://github.com/raspberrypi/pico-sdk.git
cd pico-sdk
git submodule update --init
export PICO_SDK_PATH=$(pwd)
