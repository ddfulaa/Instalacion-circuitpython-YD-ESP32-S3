# Instalación de CircuitPython en ESP32-S3 en Windows 10

Este documento proporciona instrucciones detalladas para instalar CircuitPython en la tarjeta YD-ESP32-S3 (versión 2022-v1.3) utilizando la herramienta esptool en un sistema Windows 10. Aunque las instrucciones se centran en Windows, ten en cuenta que el proceso es similar en otros sistemas operativos, pero los puertos USB pueden tener nombres diferentes en Linux o macOS.

## Paso 1: Instalación de esptool
Lo primero que necesitamos hacer es instalar la herramienta esptool. Abre tu terminal o línea de comandos y ejecuta el siguiente comando:

```pip install esptool```

Esto instalará esptool en tu sistema.

## Paso 2: Conexión de la tarjeta ESP32-S3
Conecta la tarjeta YD-ESP32-S3 a tu computadora a través de la entrada COM. La tarjeta tiene dos entradas USB-C, COM y USB. Asegúrate de usar la entrada COM para este proceso.

## Paso 3: Identificación del puerto COM
Es importante identificar a qué puerto COM se ha conectado la tarjeta. En Windows, esto generalmente es COM7 u otro número similar. Puedes verificar el puerto en el Administrador de dispositivos de Windows.

## Paso 4: Pruebas de conexión
Abre la terminal o línea de comandos y realiza las siguientes pruebas para asegurarte de que la tarjeta se ha conectado correctamente:

```esptool version``` 

```esptool --chip auto```

```esptool --chip auto --port <PUERTO> chip_id```

```esptool --chip auto --port <PUERTO> flash_id```

Reemplaza <PUERTO> con el número del puerto COM al que se ha conectado la tarjeta. Si todos los comandos funcionan sin errores, significa que la tarjeta se ha conectado correctamente.

## Paso 5: Borrado de la memoria flash
Antes de instalar CircuitPython, debemos borrar la memoria flash de la tarjeta. Ejecuta el siguiente comando:

```esptool --chip esp32s3 --port <PUERTO> erase_flash```

Nuevamente, reemplaza <PUERTO> con el número de puerto COM de la tarjeta.

## Paso 6: Descarga del binario de CircuitPython
Descarga el binario de CircuitPython específico para la tarjeta YD-ESP32-S3 desde la página de Adafruit. Asegúrate de seleccionar la versión correcta según la referencia de la memoria en tu ESP32-S3 (en este caso, n16r8).

## Paso 7: Escritura del binario en la tarjeta
Ejecuta el siguiente comando para escribir el binario de CircuitPython en la tarjeta:

```esptool --chip esp32s3 --port <PUERTO> write_flash -z 0x0 <ruta del binario>```

Reemplaza <PUERTO> con el número de puerto COM y <ruta del binario> con la ubicación del archivo binario de CircuitPython que descargaste.

## Paso 8: Cambio a la entrada USB
Desconecta la tarjeta de la entrada COM y conéctala a la entrada USB.

## Paso 9: Finalización de la instalación
Espera a que los controladores se carguen y la tarjeta aparezca como un dispositivo de memoria en tu sistema.

¡Listo! Has instalado CircuitPython en tu tarjeta ESP32-S3. Ahora puedes comenzar a desarrollar proyectos con CircuitPython en tu tarjeta.
