# To-Do List — Servidor MQTT (Eclipse Mosquitto) + App Flutter (VS Code)

## A. Prerrequisitos
- ✅ Instalar **Visual Studio Code**
- ✅ Instalar **Flutter SDK** (`flutter doctor`)
- ✅ Tener **Git** y **Node** (opcional)
- ✅ Conocer la **IP local** de la PC que será broker (`ipconfig` en Windows)

## B. Instalar Eclipse Mosquitto (Broker)
- ✅ Descargar e instalar **Mosquitto** (incluye `mosquitto.exe`, `mosquitto_pub`, `mosquitto_sub`)
- ✅ Crear carpeta de datos fuera de Program Files: `C:\mosquitto_data`

## C. Configurar Mosquitto (TCP + WebSockets)
- ✅ Abrir el **archivo de configuración** (`mosquitto.conf`)
- ✅ Añadir listeners para **1883 (TCP)** y **9001 (WebSockets)**
- ✅ Crear **usuario/contraseña** con `mosquitto_passwd`
- ✅ Reiniciar servicio Mosquitto
- ✅ Abrir **Firewall** para 1883 y 9001
- ✅ Verificar con `netstat` que los puertos estén en LISTENING

## D. Probar el broker por consola (TCP 1883)
- ✅ Suscriptor:  
  ```bash
  mosquitto_sub -h 127.0.0.1 -p 1883 -u appuser -P TU_CLAVE -t "test/#" -v
  ```
- ✅ Publicador:  
  ```bash
  mosquitto_pub -h 127.0.0.1 -p 1883 -u appuser -P TU_CLAVE -t "test/uno" -m "hola mqtt"
  ```
- ✅ Confirmar que el suscriptor ve el mensaje.

## E. Crear proyecto Flutter (VS Code)
- ✅ `flutter create greenhouse_mqtt`
- ✅ `cd greenhouse_mqtt`
- ✅ `flutter pub add mqtt_client flutter_dotenv`
- ✅ Crear archivo **.env** con HOST, PORT, USER, PASS
- ✅ Editar `pubspec.yaml` e incluir `.env` en assets

## F. Código base Flutter (MQTT por WebSockets)
- ✅ Configurar cliente MQTT en `main.dart` usando `ws://IP:9001`
- ✅ Suscribirse a tópicos: `status`, `sensor/ambient`, `actuator/lamp/state`
- ✅ Publicar comandos ON/OFF en `actuator/lamp/set`

## G. Ajustes Android/iOS
- ✅ Android: permitir tráfico claro (o usar WSS)
- ✅ iOS: configurar ATS si se usa `ws://`

## H. Ejecutar y probar Flutter
- ✅ `flutter run` en VS Code
- ✅ Conectar la app → ver `online`, lecturas y control de lámpara
- ✅ Confirmar logs en Mosquitto (`mosquitto.exe -v`)

## I. Convención de tópicos (recomendada)
- ❌ `greenhouse/1/status` → retain: `online`/`offline`
- ❌ `greenhouse/1/sensor/ambient` → JSON: `{ "temp":26.4, "hum":58.1 }`
- ❌ `greenhouse/1/actuator/lamp/set` → `ON`/`OFF`
- ❌ `greenhouse/1/actuator/lamp/state` → retain: `ON`/`OFF`

## J. Definition of Dond
- ✅ Mosquitto funciona en **1883**
- ✅ `netstat` muestra **1883** y **9001** en LISTENING
- ✅ La app Flutter conecta a `ws://IP_PC:9001`
- ❌ El ESP32 publica estados retenidos (`status` y `lamp/state`)
- ❌ El celular ve inmediatamente `status = online` al conectar

## K. Implementaciones Futuras
- ❌ Resultados diarios por WhatsApp


