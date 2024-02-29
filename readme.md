# Sinclair QL Poseidon

Este es un port muy avanzado de la implementación de Sinclair QL para [MiST](https://github.com/mist-devel/mist-board/tree/master/cores/ql)

Source original: Marcel Kilgus: https://github.com/MarcelKilgus/QL_MiSTer

### Cambios de la implementación de MiST::
* CPU cambiada a núcleo fx68 de ciclo perfecto
* Velocidades de CPU QL/16 Mhz/24 Mhz/42 Mhz
* 896kB/4096kB de RAM
* Soporte para el sistema operativo SMSQ/E usando una implementación tipo GoldCard y una ROM de arranque ("MiSTer Gold Card", también contiene TK2). Habilitado automáticamente cuando se selecciona 4 MB de RAM
* Compatibilidad total con QL-SD utilizando una tarjeta QL-SD real en la ranura secundaria o imágenes QL-SD (a menudo denominadas archivos "QXL.WIN") en la tarjeta principal. Necesita el controlador QL-SD 1.08 o superior
* Permitir el montaje dinámico de imágenes QL-SD desde OSD
* Permitir cambiar el sistema operativo desde el OSD
*RTC

## Operating systems

Todos los sistemas operativos QL son compatibles. Hay más ROM disponibles en http://www.dilwyn.me.uk/qlrom/. El tamaño de la ROM debe ser 49152 para imágenes puras del sistema operativo o 65536 para el sistema operativo + ROM de extensión de 16 kB. QL-SD se puede utilizar si el controlador QL-SD está en la ROM de extensión, pero de lo contrario también se admiten ROM como TK2.

Además, ahora se admite el sistema operativo SMSQ/E, muy mejorado. La versión MiSTer SMSQ/E es básicamente una GoldCard SMSQ/E menos el controlador de disquete, ya que no está implementado. Descárguelo de https://www.kilgus.net/ql/mister/. Debe colocarse en una imagen QL-SD y luego ejecutarse usando LRESPR.

## QL-SD Imágenes de disco .WIN
​
El nuevo controlador QL-SD utiliza archivos de imagen de disco duro de tipo QLWA. Estos son los mismos archivos que también admiten la mayoría de los principales emuladores (QPC, QemuLator, SMSQmulator) y soluciones de hardware nativas (QL con QL-SD, Q40/Q60, Q68), por lo que el intercambio de datos es bastante sencillo. Las imágenes de una tarjeta SD secundaria deben ser contiguas o se pueden perder datos. Lo mejor es copiarlo en una tarjeta SD limpia. Las imágenes de la SD principal no se ven afectadas por esta limitación.
Cuando se monta una imagen desde la SD principal, la ranura SD secundaria permanece disponible como "tarjeta 2" y cualquier archivo llamado "QXL.WIN" se monta automáticamente como el dispositivo "WIN2" (por ejemplo, "DIR win2_"). Se pueden montar diferentes archivos usando el comando WIN_DRIVE; consulte el manual de QL-SD para obtener más detalles.

## Imágenes MDV QLAY

Archivos MDV en formato QLAY. Estos archivos deben tener exactamente 174930 bytes de tamaño.
