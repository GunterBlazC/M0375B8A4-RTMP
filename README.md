# M0375B8A4-RTMP

## Parte teorica

### ¿Qué es RTMP?

El protocolo RTMP (Real-Time Messaging Protocol) es un protocolo de transmisión de vídeo y audio en tiempo real a través de Internet. Se utiliza principalmente para hacer streaming en directo desde una fuente, como por ejemplo OBS, hacia un servidor.

RTMP funciona enviando el contenido multimedia desde el cliente al servidor de forma continua, permitiendo que otros usuarios puedan acceder a ese contenido en tiempo real.

Este protocolo es muy utilizado en plataformas de streaming y en servidores propios configurados con herramientas como Nginx, ya que permite una transmisión estable y de baja latencia.

---

### Comparativa RTMP vs otros protocolos

RTMP es uno de los protocolos más utilizados para enviar vídeo en directo, pero no es el único. Existen otros como HLS o RTSP que se usan en diferentes situaciones.

RTMP destaca por su baja latencia y su facilidad de uso con herramientas como OBS. Sin embargo, no es el mejor para reproducir directamente en navegadores modernos.

Por otro lado, HLS es más compatible con navegadores y dispositivos, pero tiene más latencia, por lo que no es tan adecuado para streaming en tiempo real.

RTSP se utiliza más en cámaras de vigilancia y sistemas de videovigilancia, siendo más común en entornos de red interna.

En resumen, RTMP es ideal para enviar contenido en directo, mientras que otros protocolos como HLS se usan más para distribuirlo.

---

## Parte practica

Primero preparé la máquina virtual con Ubuntu e instalé Nginx junto con el módulo RTMP. Esto era necesario para poder convertir la máquina en un servidor de streaming.

<img src="https://github.com/user-attachments/assets/06a915da-6413-44d0-9c2a-925f49e3835c" />

Después continué con la instalación de los paquetes necesarios. En esta parte comprobé que el sistema descargaba e instalaba correctamente los componentes sin errores.

<img src="https://github.com/user-attachments/assets/d8d32eb2-d6c2-487a-947b-37c624e61916" />

Una vez instalado Nginx, abrí el archivo de configuración para añadir el bloque de RTMP. Este archivo es importante porque ahí se define cómo va a funcionar el servidor de streaming.

<img src="https://github.com/user-attachments/assets/bb81faa7-7923-457e-9bcd-8c0dd76b1329" />

Dentro del archivo añadí la configuración RTMP, indicando la aplicación `live`, activando la emisión con `live on` y desactivando la grabación con `record off`.

<img src="https://github.com/user-attachments/assets/bb0bac05-cf95-4d97-8809-cc36cbb941d6" />

Después reinicié el servicio de Nginx para aplicar los cambios realizados en la configuración.

<img src="https://github.com/user-attachments/assets/64a517fc-5476-4255-a00f-6ed1fe5d0dd6" />

A continuación instalé FFmpeg, ya que lo iba a utilizar para enviar un vídeo de prueba al servidor RTMP desde la terminal.

<img src="https://github.com/user-attachments/assets/7efd9ce2-f166-46d0-96fc-06adb1205af3" />

Luego lancé una prueba con FFmpeg usando un vídeo local. Con este comando envié el vídeo al servidor RTMP usando la ruta `rtmp://localhost/live/haven.local`.

<img src="https://github.com/user-attachments/assets/7fe3cf3f-5033-4f2d-9f2b-bd7ebc1c5837" />

Después instalé VLC para poder comprobar si la emisión RTMP se podía reproducir correctamente desde un cliente multimedia.

<img src="https://github.com/user-attachments/assets/056b345f-b798-44a2-8787-bf8d256927cd" />

En VLC abrí un flujo de red e introduje la URL `rtmp://localhost/live/haven.local`. Con esto comprobé que el contenido enviado por FFmpeg podía recibirse y visualizarse desde el reproductor.

<img src="https://github.com/user-attachments/assets/7c452ce3-2b6e-4aee-80cd-c6872d79ac0e" />

---

Después pasé a configurar OBS para hacer una emisión de pantalla hacia el servidor RTMP.

Primero instalé OBS Studio desde la terminal para poder usarlo como programa de emisión.

<img src="https://github.com/user-attachments/assets/32362746-be2c-402b-acf8-680d5bc3ba97" />

Luego abrí OBS y añadí una fuente de captura de pantalla. Esta fuente permite que OBS capture lo que ocurre en el escritorio y lo pueda enviar al servidor.

<img src="https://github.com/user-attachments/assets/8c30a8b5-716b-432a-a339-8b72a05b0a2f" />

Después configuré las propiedades de la captura de pantalla, seleccionando la pantalla correcta para que OBS pudiera mostrarla dentro de la escena.

<img src="https://github.com/user-attachments/assets/fcf35587-40c6-4532-91c5-4ec931feadc8" />

A continuación abrí los ajustes de OBS para configurar la emisión RTMP. En esta parte indiqué el servidor y la clave de transmisión para que OBS enviara el vídeo al servidor Nginx.

<img src="https://github.com/user-attachments/assets/d548cf5d-b100-4621-9397-76f9526bbc6e" />

Finalmente inicié la transmisión desde OBS y comprobé en VLC que el streaming llegaba correctamente. En la captura se ve OBS enviando la imagen y VLC reproduciendo el mismo contenido desde la URL RTMP.

<img src="https://github.com/user-attachments/assets/b5a3ff0d-1504-4d56-9716-138df27512d8" />

---

### Errores y soluciones

Durante la práctica me encontré con varios problemas:

### 🔹 Error al conectar OBS con el servidor
✔️ **Solución:** revisar la IP y el puerto en la configuración RTMP.

### 🔹 El streaming no se veía en VLC
✔️ **Solución:** comprobar la URL completa del stream (`rtmp://localhost/live/haven.local`) y asegurarse de que el servidor está activo.

### 🔹 Problemas con el firewall
✔️ **Solución:** abrir el puerto correspondiente (1935) en el sistema.

### 🔹 Error en la configuración de NGINX
✔️ **Solución:** revisar la sintaxis del archivo de configuración (`nginx.conf`) usando `nginx -t`.

### 🔹 OBS no se abría (error Wayland)
✔️ **Solución:** ejecutar OBS forzando X11:
```bash
QT_QPA_PLATFORM=xcb obs```

---

### Conclusiones

En esta práctica he aprendido a configurar un servidor de streaming utilizando RTMP y NGINX.

También he entendido cómo funciona la transmisión de vídeo en tiempo real y cómo se puede enviar contenido desde OBS a un servidor propio.

Uno de los puntos más importantes ha sido comprender la importancia de la configuración de red y de los puertos para que el streaming funcione correctamente.

En general, la práctica me ha servido para entender mejor cómo funcionan los sistemas de streaming en directo.

---

### Webgrafía

- https://nginx.org/en/docs/
- https://obsproject.com/
- https://ffmpeg.org/
- https://punkymo.gitbook.io/miwiki




