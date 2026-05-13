# SGP40-AirGuard: Nodo Inteligente de Monitoreo Ambiental

## 🚀 Visión del Proyecto
**SGP40-AirGuard** es una solución de hardware de vanguardia diseñada para la medición precisa de la calidad del aire. Este nodo de detección combina la potencia de procesamiento del **ESP32-C6** con la alta sensibilidad del sensor **SGP40**, permitiendo a los usuarios convertir datos invisibles en acciones concretas para mejorar la salud respiratoria y la eficiencia en espacios cerrados.

## 🌟 ¿Por qué SGP40-AirGuard?
En un mundo donde la calidad del aire interior es crítica, este dispositivo ofrece:
* **Integración Versátil:** Su diseño circular ultra-compacto de 4 capas lo hace ideal para su despliegue en entornos residenciales, oficinas inteligentes o como un wearable de monitoreo personal.
* **Inteligencia Conectada:** Aprovechando el ecosistema del **ESP32-C6**, nuestro nodo es compatible con los protocolos de conectividad más modernos (Wi-Fi 6, Zigbee, Thread), facilitando su integración en redes domésticas existentes.
* **Eficiencia Energética:** Optimizado para ofrecer una autonomía extendida, permitiendo despliegues de bajo consumo en aplicaciones críticas de IoT.

## 📊 Aplicaciones de Alto Impacto
* **Salud y Bienestar:** Monitoreo preventivo para personas con condiciones respiratorias sensibles a los VOCs.
* **Ciudades Inteligentes:** Nodo base para redes de mapeo de calidad de aire distribuido en infraestructuras urbanas.
* **Seguridad Industrial:** Automatización de protocolos de ventilación basada en la detección real de contaminantes, optimizando el consumo energético en edificios comerciales.

## 🛠️ Especificaciones Técnicas
| Componente | Especificación |
| :--- | :--- |
| **Microcontrolador** | ESP32-C6 (Dual-core, BLE/Wi-Fi 6) |
| **Sensor VOC** | Sensirion SGP40 |
| **Gestión Energética** | Cargador MCP73831 + Regulador LDO AP2112 |
| **Formato** | PCB Circular 4 capas (SMD 0402) |
| **Interfaz** | Visual (LEDs 0402) + Sonora (Buzzer) |

---
## Arquitectura del Sistema
A continuación se presenta el diagrama de bloques del nodo de monitoreo:

```mermaid
graph LR
    subgraph Sensores
        SGP40[Sensor SGP40 VOC]
    end

    subgraph Procesamiento
        ESP32[ESP32-C6 <br/>Microcontrolador]
    end

    subgraph Interfaz
        LEDs[LEDs Estado 0402]
        Buzzer[Buzzer Magnético]
    end

    subgraph Potencia
        LIPO[Batería Li-Po]
        CHG[Cargador MCP73831]
        REG[Regulador AP2112]
    end

    SGP40 -- I2C --> ESP32
    ESP32 --> LEDs
    ESP32 --> Buzzer
    LIPO --> CHG
    CHG --> REG
    REG -- 3.3V --> ESP32
    REG -- 3.3V --> SGP40
    