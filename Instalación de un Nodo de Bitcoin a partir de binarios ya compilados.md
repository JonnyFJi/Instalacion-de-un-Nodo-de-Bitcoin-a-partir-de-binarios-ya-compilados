---
title: Instalación de un Nodo de Bitcoin a partir de binarios ya compilados.
tags: [bitcoin, cli, nodo, node, macos, talleres, ubuntu]

---

# Instalación de un Nodo de Bitcoin a partir de binarios ya compilados
###### tags: `bitcoin` `cli` `nodo` `Linux` `MacOS` `Windows` `node`

Instalación de un `nodo` a partir de binarios ya compilados.
* En bitcoincore.org existen instaladores binarios para varios sistemas operativos, es cuestión de descargarlos y seguir las instrucciones para instalarlo en tu equipo.
* Esta guía describe esas instrucciones.

**Tabla de contenido**
[TOC]

## Autores
Jonny_Ji. 
Twitter para correcciones, comentarios o sugerencias: [@JonnyJi50127056](https://x.com/JonnyJi50127056)

El presente tutorial fue elaborado para el curso [Nodes from zero to hero](https://libreriadesatoshi.com/courses/nodes-from-zero-to-hero) a través de [@libreriadesatoshi](https://twitter.com/libdesatoshi).

En el siguiente enlace puedes encontrar la documentación de referencia:
[Running A Full Node](https://bitcoin.org/en/full-node)

[BitcoinCore](https://bitcoincore.org/)

## Qué es un nodo completo?
Un nodo completo es un programa que valida completamente transacciones y bloques. Casi todos los nodos completos también ayudan a la red al aceptar transacciones y bloques de otros nodos completos, validando esas transacciones y bloques, para luego retransmitirlos a otros nodos completos.

La mayoría de los nodos completos también atienden a clientes livianos al permitirles: transmitir sus transacciones a la red y notificándoles cuando una transacción afecta su billetera. Si no hay suficientes nodos que realicen esta función, los clientes no podrán conectarse a través de la red peer-to-peer y tendrán que utilizar servicios centralizados.

## Instrucciones para Linux
Las siguientes instrucciones describen la instalación de `Bitcoin Core` mediante herramientas disponible en la mayoría de las distribuciones principales de `Linux`.

Usando cualquier computadora, vaya a la Página de descarga de Bitcoin Core y verifique que ha realizado una conexión segura al servidor.

[BitcoinCore](https://bitcoincore.org/en/download/)

En la sección *“Linux (tgz)”* de la página *Descargar*, elija el archivo apropiado para su instalación de Linux y descargue el archivo. Si es necesario, mueva el archivo a la computadora que desee usar para ejecutar Bitcoin Core.

**Opcional**: *Verificar las firmas de liberación*

- Si sabe cómo utilizar PGP, también debe *Verificar las Firmas del Lanzamiento*. En la misma página puede encontrar las instrucciones para realizar la verificación.

Si aún no ha iniciado sesión en la computadora donde desea instalar Bitcoin, inicia sesión ahora. Asegúrese de utilizar una cuenta que pueda utilizar `su` o `sudo` para instalar software en directorios propiedad del usuario root.

Si inició sesión gráficamente, abre una terminal. 

También puede descargar el archivo directamente si conoce la versión que desea instalar

- Descarga la última versión oficial:
```shell
wget https://bitcoincore.org/bin/bitcoin-core-29.1/bitcoin-29.1-x86_64-linux-gnu.tar.gz
```

Localice el archivo que descargó y extráigalo usando el comando `tar` seguido del argumento `xzf` seguido del `nombre del archivo`. El argumento **xzf** significa extraer el archivo **tar** comprimido. Por ejemplo:
```shell
tar xzf bitcoin-29.1-x86_64-linux-gnu.tar.gz
```

Esto creará el directorio `bitcoin-29.1` dentro de la carpeta. Si es necesario mueva la carpeta a su Carpeta Personal `Home`. Instalaremos el contenido del subdirectorio `bin` hacia el directorio `/usr/local/bin` utilizando el comando `install`. El directorio  `/usr/local/bin` es una ubicación estándar para ejecutables autoinstalados (puede editar el comando a continuación para utilizar una ubicación diferente).

Si usas `sudo` para ejecutar comandos como root, utilice el siguiente comando:
```shell
sudo install -m 0755 -o root -g root -t /usr/local/bin bitcoin-29.1/bin/*
```
Si usas `su` para ejecutar comandos como root, utilice la siguiente línea de comando:
```shell
su -c 'install -m 0755 -o root -g root -t /usr/local/bin bitcoin-29.1/bin/*'
```

Esto instalará los archivos binarios necesarios para ejecutar Bitcoin Core.

A continuación solo debe decidir si desea ejecutar el nodo en modo gráfico `bitcoin-qt` o en una terminal `bitcoind`. Tenga en cuenta que no puede ejecutar ambos al mismo tiempo usando el mismo directorio. 

Para interactuar con `bitcoind`, debes utilizar `bitcoin-cli` (Bitcoin interfaz de línea de comandos) seguido del comando que desea ejecutar. Utilizando el comando `help`puedes encontrar una lista de ordenes para ejecutar con el nodo.
```shell
bitcoin-cli help
```
Para comprobar el progreso del nodo, utilice este comando:
```shell
bitcoin-cli getblockchaininfo
```

Si inicia `bitcoin-qt` por primera vez, se le pedirá que elija un directorio para almacenar la cadena de bloques de Bitcoin y su billetera. A menos que tenga una partición o unidad separada que desee utilizar, haga clic en **Aceptar** para utilizar el valor predeterminado.

Una vez completada la descarga de la cadena de bloques, puedes usar Bitcoin Core como tu billetera o puedes simplemente dejarlo funcionar para ayudar a respaldar la red Bitcoin.

## Instrucciones para Windows
Las siguientes instrucciones describen la instalación de `Bitcoin Core` mediante herramientas disponible en la mayoría de las versiones de `Windows`.

Usando cualquier computadora, vaya a la Página de descarga de Bitcoin Core y verifique que ha realizado una conexión segura al servidor.

[BitcoinCore](https://bitcoincore.org/en/download/)

Haga clic en el botón azul `Descargar Bitcoin Core` para descargar el Instalador de Bitcoin Core en su carpeta `Descargas`.

**Opcional**: *Verificar las firmas de liberación*

- Si sabe cómo utilizar PGP, también debe *Verificar las Firmas del Lanzamiento*. En la misma página puede encontrar las instrucciones para realizar la verificación.

Después de descargar el archivo a su carpeta Descargas `(C:\Users\<YOUR USER NAME>\Downloads)`, ejecútelo haciendo doble clic en su icono. 

Windows le pedirá que confirme que desea ejecutarlo. Haga clic en `Sí` y el `instalador de Bitcoin` se iniciará. Es un instalador típico de Windows y lo guíará a través de las decisiones que debes tomar sobre dónde instalar Bitcoin Core.

Se le pedirá que elija un directorio para almacenar la cadena de bloques de Bitcoin y su billetera. A menos que tenga una partición o unidad separada que desee utilizar, haga clic en **Aceptar** para utilizar el valor predeterminado.

Su firewall puede impedir que Bitcoin Core realice conexiones salientes. Es seguro permitir que Bitcoin Core utilice todas las redes.

Una vez que finalice el proceso, se cerrará el instalador y se abrirá automaticamente la GUI de Bitcoin Core.

**Nota**: Si desea utilizar el demonio Bitcoin Core (bitcoind), que es útil para programadores y usuarios avanzados, primero abra una ventana de terminal y si instaló Bitcoin Core en el directorio predeterminado, escriba a continuación del símbolo del sistema el siguiente comando:
```shell
C:\Program Files\Bitcoin\daemon\bitcoind
```
Para interactuar con `bitcoind`, debes utilizar `bitcoin-cli` (Bitcoin interfaz de línea de comandos) seguido del comando que desea ejecutar. Utilizando el comando `help`puedes encontrar una lista de ordenes para ejecutar con el nodo.
```shell
bitcoin-cli help
```
Para comprobar el progreso del nodo, utilice este comando:
```shell
bitcoin-cli getblockchaininfo
```
Tenga en cuenta que no puede ejecutar ambos al mismo tiempo, `bitcoind` y `GUI`.

Una vez completada la descarga de la cadena de bloques, puedes usar Bitcoin Core como tu billetera o puedes simplemente dejarlo funcionar para ayudar a respaldar la red Bitcoin.

**Advertencia**: Para evitar la corrupción de datos, no fuerce el cierre de su computadora desde la pantalla de apagado de Windows cuando tienes Bitcoin Core en funcionamiento.

## Instrucciones para MacOS X
Las siguientes instrucciones describen la instalación de `Bitcoin Core` mediante herramientas disponible en la mayoría de las versiones de `MacOS`.

Usando cualquier computadora, vaya a la Página de descarga de Bitcoin Core y verifique que ha realizado una conexión segura al servidor.

[BitcoinCore](https://bitcoincore.org/en/download/)

Haga clic en el botón azul `Descargar Bitcoin Core` para descargar el Instalador de Bitcoin Core en su carpeta `Descargas`.

**Opcional**: *Verificar las firmas de liberación*

- Si sabe cómo utilizar PGP, también debe *Verificar las Firmas del Lanzamiento*. En la misma página puede encontrar las instrucciones para realizar la verificación.

Después de descargar el archivo a su carpeta Descargas `(/Users/<YOUR USER NAME>/Downloads)`, ejecútelo haciendo doble clic en su icono. OS X abrirá una ventana del Finder para que puedas arrastrar Bitcoin Core a tu Carpeta de aplicaciones.

La primera vez que corra Bitcoin Core, Max OS X le pedirá que confirme que quiere ejecutarlo, selecciones **Open** y se iniciará el asistente que le guiará en el proceso de instalación e inicio de Bitcoin Core.

Se le pedirá que elija un directorio para almacenar la cadena de bloques de Bitcoin y su billetera. A menos que tenga una partición o unidad separada que desee utilizar, haga clic en **Aceptar** para utilizar el valor predeterminado.

La GUI de Bitcoin Core se iniciará y comenzará a descargar la cadena de bloques.

**Nota**: El demonio de Bitcoin Core (bitcoind) no está incluido en el archivo .dmg que hayas descargado para instalar Bitcoin-QT.

- `bitcoind`, junto con sus binarios de soporte, está incluido en el archivo `.tar.gz` de OS X que aparece en la página oficial de descarga de Bitcoin Core. Para descargar este archivo usando Terminal, ejecute el siguiente comando:
```shell
curl -O https://bitcoin.org/bin/bitcoin-core-29.1/bitcoin-29.1-osx64.tar.gz
```
**Opcional**: *Verificar las firmas de liberación*

- Si sabe cómo utilizar PGP, también debe *Verificar las Firmas del Lanzamiento*. En la misma página puede encontrar las instrucciones para realizar la verificación.

Una vez completada la descarga. Extraiga bitcoind y sus binarios de soporte del archivo que acabamos de descargar ejecutando este comando en Terminal:
```shell
tar -zxf bitcoin-29.1-osx64.tar.gz
```
Ahora moveremos los ejecutables a su ruta predeterminada para facilitar la ejecución y detección de bitcoind. Para mover los ejecutables, corra estos comandos (tenga en cuenta que tenemos que usar `sudo` para ejecutar estos comandos ya que estamos modificando directorios propiedad de `root`):
```shell
sudo mkdir -p /usr/local/bin
sudo cp bitcoin-29.1/bin/bitcoin* /usr/local/bin/.
```
Ahora deberías poder iniciar tu nodo completo ejecutándo `bitcoind -daemon` en cualquier ventana de Terminal. Si necesita detener `bitcoind` por cualquier motivo, el comando es `bitcoin-cli stop`

Para interactuar con `bitcoind`, debes utilizar `bitcoin-cli` (Bitcoin interfaz de línea de comandos) seguido del comando que desea ejecutar. Utilizando el comando `help`puedes encontrar una lista de ordenes para ejecutar con el nodo.
```shell
bitcoin-cli help
```
Para comprobar el progreso del nodo, utilice este comando:
```shell
bitcoin-cli getblockchaininfo
```

Tenga en cuenta que no puede ejecutar ambos al mismo tiempo, `bitcoind` y `bitcoin-qt`.

Una vez completada la descarga de la cadena de bloques, puedes usar Bitcoin Core como tu billetera o puedes simplemente dejarlo funcionar para ayudar a respaldar la red Bitcoin.

## Actualizaciones de Bitcoin Core
Si está ejecutando una versión anterior de Bitcoin Core, apáguela. Espere hasta que esté completamente apagada (lo que puede tardar unos minutos para versiones anteriores) y luego ejecute el instalador (en Windows) o simplemente copie/Aplicaciones/Bitcoin-Qt (en Mac) o bitcoind/bitcoin-qt (en Linux). Eso actualizará la aplicación Bitcoin Core y todas sus dependencias.

Los archivos de la cadena de bloques y de la billetera en el directorio de datos son compatibles entre versiones, por lo que no es necesario realizar ningún cambio en el directorio de datos al actualizar.

Ocasionalmente el formato de esos archivos cambia, pero la nueva versión de Bitcoin Core incluirá código que actualiza automáticamente los archivos al nuevo formato, por lo que no se requiere intervención manual.

## Consideraciones finales

- Con 6 horas al día en las que su nodo completo pueda dejarse funcionando es suficiente para mantenerlo sincronizado. (Puedes hacer otras cosas con tu computadora mientras ejecutas un nodo completo). Más horas sería mejor, y lo mejor de todo sería si pudieras correr tu nodo continuamente, 24/7 es lo ideal para apoyar la red.

**Nota**: Muchos sistemas operativos actuales (Windows, Mac y Linux) entran en un modo de bajo consumo después de que se activa el protector de pantalla, esto desacelera o detiene el tráfico de red. Esta suele ser la configuración predeterminada en computadoras portátiles y en todas las computadoras portátiles y de escritorio MacOS X. Comprueba la configuración de tu protector de pantalla y desactive las opciones automáticas de “dormir” o “suspender” para asegurarse. Apoye la red siempre que su computadora esté en funcionamiento.

Si has llegado hasta aquí, felicitaciones, ahora tienes un nodo Bitcoin listo para usar. Este es el primer pilar para comenzar a construir tu soberanía monetaria.

# Team "Librería de Satoshi"