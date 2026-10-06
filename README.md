cat << 'EOF' > README.md
# Ajazz AK820 - Linux RGB & Driver Protocol

Documentación y herramientas de ingeniería inversa para el control de iluminación RGB y configuración del teclado **Ajazz AK820 (Wired Version)** de forma nativa en Linux sin depender del software propietario de Windows.

---

## 1. Identificación del Hardware

A través de `lsusb` se identificó que el teclado utiliza la controladora USB de **China Resource Semico Co., Ltd (EVVision / Sinowealth)**:

* **Vendor ID (VID):** `0x1a2c`
* **Product ID (PID):** `0x6e81`
* **Dispositivo:** China Resource Semico Co., Ltd AK820
* **Protocolo:** HID a través de tramas de 64 bytes.

---

## 2. Tabla de Modos de Iluminación (`default_light.json`)

Obtenida directamente tras descompilar los recursos del driver original (`DefaultData/default_light.json`).

| ID (`value`) | Nombre Interno | Modo de Luz |
| :---: | :--- | :--- |
| `1` | `light_mode_wave_text` | Ola / Wave |
| `2` | `light_mode_cloud_text` | Nube / Cloud |
| `3` | `light_mode_vortex_text` | Vórtice / Vortex |
| `4` | `light_mode_mix_color_text` | Color Mixto / Mix Color |
| `5` | `light_mode_breath_text` | Respiración / Breath |
| `6` | `light_mode_static_text` | Estático / Static |
| `7` | `light_mode_reaction_text` | Reacción / React |
| `8` | `light_mode_stone_text` | Gota de agua / Ripple |
| `9` | `light_mode_traverse_text` | Barrido / Traverse |
| `10` | `light_mode_stars_text` | Estrellas / Stars |
| `11` | `light_mode_firework_open_text` | Fuegos artificiales / Fireworks |
| `12` | `light_mode_roll_text` | Desplazamiento / Roll |
| `13` | `light_mode_wave_bar_text` | Barra de ola / Wave Bar |
| `14` | `light_mode_cartoon_text` | Cartoon |
| `15` | `light_mode_rain_text` | Lluvia / Rain |
| `16` | `light_mode_scan_text` | Escáner / Scan |
| `17` | `light_mode_zzcc_text` | Zzcc |
| `18` | `light_mode_speed_text` | Speed |
| `20` | `light_mode_custom_text` | Personalizado / Custom |
| `29` | `light_mode_audiorecord_text` | Ritmico de Audio |
| `30` | `light_mode_capturecolor_text` | Captura de Color |

---

## 3. Configuración del Sistema (Sin `sudo`)

Para poder enviar comandos HID al teclado desde tu usuario sin permisos de root, añade la regla de `udev`:

```bash
echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="1a2c", ATTR{idProduct}=="6e81", MODE="0666"' | sudo tee /etc/udev/rules.d/99-ak820.rules
sudo udevadm control --reload-rules && sudo udevadm trigger
```
