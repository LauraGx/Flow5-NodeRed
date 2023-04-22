# Flow5-NodeRed
Este es otro ejercicio que consiste en tener información del clima por API  en openweathermap.org


## Introducción

El flow 5 consiste en representar el clima de forma grafica donde muestra la temperatura y humedad local con ayuda de API de openweathermap.org

## Material Necesario

Para realizar este flow necesitas lo siguiente:

- [Ubuntu 20.04](https://releases.ubuntu.com/20.04/)
- [NodeJS](https://nodejs.org/es/)
    - NPM
    - NodeRed
    - Nodos Dashboard
    - Cuenta de OpenWeather

## Material de referencia

En los siguientes enlaces puedes encontrar cursos en la plataforma de edu.codigoiot.com que te permitirán realiar las configuraciones necesarias

- [Instalación de Virutal Box y Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=812)
- [Instalación de NodeRed](https://edu.codigoiot.com/course/view.php?id=817)
- [Introducción a NodeRed](https://edu.codigoiot.com/course/view.php?id=278)
- [Introducción a MQTT](https://edu.codigoiot.com/enrol/index.php?id=851)
- [API de OpenWeather](https://openweathermap.org/api)

## Instrucciones

### Requisitos previos

Para que este flow funcione, debes cumplir con los siguientes requisitos previos

1. Instalación de NodeJS. Se recomienda tener instalado NodeJS en alguna versión LTS. Al momento de creación de este documento, se usó la versión 18.12LTS. Esta instalación debe incluir las Build-Tools para hacer uso de NPM
2. Instalación de NodeRed. La instalación se realiza por NPM. Al momento de la creación de este contenido, se usó la versión 3.0.2
3. Cuenta de OpenWeather donde tendremos información 
4. Coordenadas de un lugar.

### Instrucciones de preparación del entorno

Para ejecutar este flow es necesario lo siguiente: 
- Arrancar NodeRed con el comando node-red
- Clonar el flow4 
- Hecho esto agregar 1 nodo timestamp, 1 nodo http request, 1 nodo json, 2 nodos function, 2 nodos gauge y 1 nodo chart.
- Obtenemos la API KEY al hacer una cuenta gratis en openweathermap.org
- En la documentacion de APIs obtenemos: https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={API key} donde {lat} ponemos la latitud y en {Ion} longitud del lugar que elegimos y {API KEY} 
- La IP del público usamos el comando nslookup broker.hivemq.com y colocamos la URL en el nodo http request
- El nodo json se cambiará a la opción de convertir objetos javascript
- El nodo function 1 será Temperatura API y agregar un codigo:  global.set ("tempAPI",msg.payload.main.temp); msg.payload = msg.payload.main.temp; msg.topic = "Temperatura"; return msg;
- El nodo 2 será Humedad API y agregar el codigo: msg.payload = msg.payload.main.humidity; global.set ("humAPI",msg.payload); msg.topic = "Humedad"; return msg; en ambos nodos se agregan en la pestaña "on message"
- Agregar una tabla y cambiar al nombre de flow5 y dentro agregar 3 grupos que se llamen temperatura, humedad e historico API y relacionarlos con los grupos que se crearon, y los nodos de temperatura y humedad deben estar en mínimo y máximo. 
- Hacer clic en el botón Deploy.


### Instrucciones de operación

Para observar el resultado de este flow, sólo es necesario abrir el navegador y escribir la siguiente dirección http://localhost:1880/ui y dentro de la página hay un menú derecho y hacer clic en flow5, debemos hacer clic en el TimeStamp para enviar información al http request.

## Resultados

A continuación puede verse una vista previa del resultado de este flow.

![](https://github.com/Cecilia-X-M/flow5-NodeRed/blob/main/flow5API.png)
![](https://github.com/Cecilia-X-M/flow5-NodeRed/blob/main/flow5APIR.png)

# Créditos

Desarrollado por Diana Laura Aragon

- [GitHub](https://github.com/LauraGx)
