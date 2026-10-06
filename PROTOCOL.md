# Protocolo USB/HID - Ajazz AK820 Wired RGB

## Información del Dispositivo
- **VID:** `0x1a2c` (China Resource Semico Co., Ltd)
- **PID:** `0x6e81`
- **Tamaño de paquete (Report Size):** 8 bytes

## Mapeo de Modos de Luz (ID de Modo)
| Byte de Modo | Nombre | Descripción |
| :---: | :--- | :--- |
| `0x00` / `0x01` | Wave | Ola de color |
| `0x02` | Cloud | Efecto sombra / nube |
| `0x03` | Vortex | Vórtice / remolino |
| `0x04` | Mix Color | Mezcla multicolor |
| `0x05` | Breath | Respiración |
| `0x06` | Static | Color fijo estático |

## Estructura del Paquete (En Investigación)
`[ Byte 0 | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 ]`
