# 🌱 Greenhouse Control — MQTT + Flutter

## 📖 Descripción

Este proyecto tiene como objetivo crear un **sistema de monitoreo y control remoto para un invernadero**.  
Se basa en un **servidor MQTT (Eclipse Mosquitto)** y una **aplicación móvil desarrollada en Flutter**.  

La idea es que los sensores (ej. temperatura, humedad, humedad del suelo, luz) conectados a un **ESP32** publiquen sus lecturas en el broker MQTT.  
La aplicación móvil se conecta a ese broker vía **WebSockets**, permitiendo al usuario:

- 📊 **Visualizar en tiempo real** los datos del invernadero.  
- 💡 **Encender/apagar dispositivos** como lámparas, bombas de agua o ventiladores.  
- ⚙️ **Automatizar reglas** (ej: regar cuando la humedad del suelo es baja).  
- 🔔 **Recibir notificaciones/alertas** si algún valor se sale de rango.

---

## 🏗️ Arquitectura del Proyecto

- **ESP32** → Sensores + relés → se conecta por Wi-Fi al broker MQTT.  
- **Eclipse Mosquitto (Broker MQTT)** → Central de mensajes que recibe y distribuye datos.  
- **App Flutter (Android/iOS)** → Interfaz para el usuario, conexión por `ws://` o `wss://`.  

```
[ESP32 + Sensores] ↔ [Mosquitto Broker] ↔ [App Flutter]
```

---

## 🚀 Funcionalidades

- ✅ Publicación de datos de sensores vía MQTT.  
- ✅ Control de actuadores desde la app (ON/OFF).  
- ✅ Comunicación en tiempo real con baja latencia.  
- 🔜 Almacenamiento de históricos y visualización en gráficas.  
- 🔜 Configuración de reglas automáticas desde la app.  

---

## 🔧 Tecnologías utilizadas

- **Hardware**: ESP32, DHT22, relé, lámpara (ejemplo).  
- **Servidor**: Eclipse Mosquitto (broker MQTT).  
- **Frontend móvil**: Flutter + Dart.  
- **IDE**: Visual Studio Code.  
- **Protocolo**: MQTT sobre TCP (1883) y WebSockets (9001).  

---

## 📱 ¿Para qué sirve este proyecto?

- Para **automatizar invernaderos** y tener control en tiempo real desde el celular.  
- Para **aprender arquitectura IoT** usando MQTT.  
- Para **escalar** hacia sistemas más grandes: smart homes, domótica, control de energía.  
- Como **base didáctica** para proyectos de IoT en la universidad o personales.  

---

## ✅ Estado del Proyecto

Actualmente se encuentra en fase de:
- Instalación y configuración del **broker MQTT**.  
- Desarrollo del prototipo de **app Flutter** con conexión en tiempo real.  
- Integración inicial con un **ESP32 + sensor DHT22 + relé**.  

---

## 📌 Próximos pasos

1. Añadir más sensores (suelo, luz).  
2. Implementar automatizaciones (riego automático).  
3. Guardar históricos en una base de datos.  
4. Visualizar gráficas en la app.  
5. Implementar seguridad (TLS, usuarios y roles).  
