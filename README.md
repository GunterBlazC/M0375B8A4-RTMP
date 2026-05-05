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

Primero preparé la máquina virtual con Ubuntu e instalé Nginx junto con el módulo RTMP para poder crear un servidor de streaming. Durante esta parte instalé los paquetes necesarios usando apt.

<img src="https://github.com/user-attachments/assets/06a915da-6413-44d0-9c2a-925f49e3835c" />

Después comprobé que la instalación se había realizado correctamente revisando la salida de la terminal y verificando que no había errores.

<img src="https://github.com/user-attachments/assets/d8d32eb2-d6c2-487a-947b-37c624e61916" />

Una vez instalado, accedí al archivo de configuración de Nginx para poder modificarlo y añadir la configuración del módulo RTMP.

<img src="https://github.com/user-attachments/assets/bb81faa7-7923-457e-9bcd-8c0dd76b1329" />

En este archivo añadí el bloque RTMP donde se define el puerto y la aplicación de streaming.

<img src="https://github.com/user-attachments/assets/bb0bac05-cf95-4d97-8809-cc36cbb941d6" />

Después guardé los cambios y comprobé que la configuración era correcta.

<img src="https://github.com/user-attachments/assets/64a517fc-5476-4255-a00f-6ed1fe5d0dd6" />

A continuación reinicié el servicio de Nginx para aplicar la nueva configuración.

<img src="https://github.com/user-attachments/assets/7efd9ce2-f166-46d0-96fc-06adb1205af3" />

Después comprobé que el servicio estaba activo y funcionando correctamente.

<img src="https://github.com/user-attachments/assets/7fe3cf3f-5033-4f2d-9f2b-bd7ebc1c5837" />

Una vez hecho esto, verifiqué que el servidor estaba preparado para recibir conexiones RTMP.

<img src="https://github.com/user-attachments/assets/056b345f-b798-44a2-8787-bf8d256927cd" />

Finalmente revisé la configuración completa para asegurarme de que todo estaba correctamente definido.

<img src="https://github.com/user-attachments/assets/7c452ce3-2b6e-4aee-80cd-c6872d79ac0e" />

---

Después pasé a configurar OBS para enviar el streaming al servidor.

Primero abrí OBS y accedí a la configuración.

<img src="https://github.com/user-attachments/assets/32362746-be2c-402b-acf8-680d5bc3ba97" />

Luego configuré el servidor RTMP introduciendo la dirección IP del servidor y la clave de transmisión.

<img src="https://github.com/user-attachments/assets/8c30a8b5-716b-432a-a339-8b72a05b0a2f" />

Después ajusté los parámetros básicos de emisión.

<img src="https://github.com/user-attachments/assets/fcf35587-40c6-4532-91c5-4ec931feadc8" />

A continuación inicié la transmisión desde OBS.

<img src="https://github.com/user-attachments/assets/d548cf5d-b100-4621-9397-76f9526bbc6e" />

Finalmente comprobé que el streaming llegaba correctamente al servidor y se podía visualizar sin problemas.

<img src="https://github.com/user-attachments/assets/b5a3ff0d-1504-4d56-9716-138df27512d8" />

### Errores y soluciones

Durante la práctica me encontré con varios problemas:

**Error al conectar OBS con el servidor**  
✔️ Solución: revisar la IP y el puerto en la configuración RTMP  

**El streaming no se veía en VLC**  
✔️ Solución: comprobar la URL completa del stream  

**Problemas con el firewall**  
✔️ Solución: abrir el puerto correspondiente en el sistema  

**Error en la configuración de Nginx**  
✔️ Solución: revisar la sintaxis del archivo de configuración  

---

### Conclusiones

En esta práctica he aprendido a configurar un servidor de streaming utilizando RTMP y Nginx.

También he entendido cómo funciona la transmisión de vídeo en tiempo real y cómo se puede enviar contenido desde OBS a un servidor propio.

Uno de los puntos más importantes ha sido comprender la importancia de la configuración de red y de los puertos para que el streaming funcione correctamente.

En general, la práctica me ha servido para entender mejor cómo funcionan los sistemas de streaming en directo.

---

### Webgrafía

- https://nginx.org/en/docs/
- https://obsproject.com/
- https://ffmpeg.org/
- https://punkymo.gitbook.io/miwiki




