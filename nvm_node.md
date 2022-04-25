# Cambiar de versión de Node.js con NVM

Node Version Manager (NVM), es una herramienta que permite a los usuarios instalar rápidamente versiones de Node directamente desde la CLI y cambiar entre versiones.

Así como npm administra los paquetes de Node, NVM administra las versiones de Node. Esto significa que puede instalar varias versiones de Node en su máquina y cambiar entre ellas cuando sea necesario.

## Por qué los programadores de Node.js necesitan NVM

En ocasiones trabajamos en distintos proyectos que requieren distinta versión de node. En este caso, desea alternar entre diferentes versiones de Node, y la forma más fácil de hacerlo es usar un administrador de versiones de Node.

Veamos cómo funciona NVM.

## Instalación de NVM

Antes de instalar NVM, no necesita una versión de Node instalada en su máquina y, si tiene instalado Node, no importa. La instalación de NVM y su uso para instalar versiones de Node funcionarán por separado de la existente.

Para instalar NVM, ejecute el siguiente comando en su terminal:

```bash
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```

cURL viene con la mayoría de los sistemas operativos basados en Linux. Ejecutar el comando anterior descarga un script y lo ejecuta.

Esta secuencia de comandos descarga todo el repositorio de NVM en ~/.nvm y agrega las líneas fuente del fragmento a continuación a la secuencia de comandos de inicio de shell correcta, es decir,\ /.bash_profile, ~/.zshrc, ~/.profile o ~/. bashrc, dependiendo del programa de shell que esté utilizando.

En mi caso, estoy usando ~/.bashrc:

```bash
// Agregar al final
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

Después de eso, sal de la terminal y vuelve a abrirla.

Si se instaló correctamnete, al ejecutar nvm obtendremos

```
Node Version Manager (v0.39.0)
Note: <version> refers to any version-like string nvm understands. This includes:
  - full or partial version numbers, starting with an optional "v" (0.10, v0.1.2, v1)
  - default (built-in) aliases: node, stable, unstable, iojs, system
  - custom aliases you define with `nvm alias foo`

 Any options that produce colorized output should respect the `--no-colors` option.

Usage:
...
```

## Instalación y administración de versiones de Node.js

Para instalar una versión de Node, simplemente ejecute el siguiente comando:

```bash
$ nvm install --<versión de node>
```

Comencemos instalando la última versión de LTS. Esto se hace ejecutando:

```bash
$ nvm install --lts
```

Finalizada la instación, se establecerá automáticamente la versión de node predeterminada en el LTS que acabamos de descargar.

Para ver todas las versiones de node disponibles para instalar podemos ejecutar:

```bash
$ nvm ls-remote
# Para instalar la última versión disponible:
$ nvm install node
# Para instalar una versión particular:
$ nvm install v16.14.2
```

Mostrar una lista de versiones de Node.js

Ahora podemos ver todas las versiones que descargamos hasta ahora; actualmente, tenemos tres versiones de Node instaladas usando NVM.

Para ver la lista completa, ejecute el siguiente comando:

```bash
$ nvm ls

       v12.18.4
       v14.19.0
->     v18.0.0
default -> v14.19.0
iojs -> N/A (default)
unstable -> N/A (default)
node -> stable (-> v18.0.0) (default)
stable -> 18.0 (-> v18.0.0) (default)
lts/* -> lts/gallium (-> N/A)
lts/argon -> v4.9.1 (-> N/A)
lts/boron -> v6.17.1 (-> N/A)
lts/carbon -> v8.17.0 (-> N/A)
lts/dubnium -> v10.24.1 (-> N/A)
lts/erbium -> v12.22.12 (-> N/A)
lts/fermium -> v14.19.1 (-> N/A)
lts/gallium -> v16.14.2 (-> N/A)
```

Las primeras tres líneas muestran la lista de versiones de Node instaladas. La flecha apuntando a la versión 18.0.0 indica la versión que se encuentra actualmente en uso; cuando se usa una versión, se muestra en verde.

## Cambio entre la versión de Node.js

La mejor característica de NVM es la capacidad de cambiar fácilmente entre diferentes versiones de Node.

Digamos que debemos usar la versión v14.19.0:

```bash
$ nvm use v14.19.0
Now using node v14.19.0 (npm v6.14.16)
```

Tenga en cuenta que, dado que solo tenemos una versión que comienza con 12, 14 o 18, podemos cambiar de versión con un simple comando nvm use 18, nvm use 14 o nvm use 12.

## Eliminar una versión de Node.js

A menudo, es posible que no necesite una versión particular de Node para los proyectos en los que está trabajando. Con NVM, puede eliminar fácilmente las versiones que no necesita.

Para eliminar una versión, simplemente ejecute el siguiente comando:

```bash
nvm uninstall <el número de versión>
```

El terminal mostrará entonces que la versión está desinstalada.

Debe tener en cuenta que cada versión de la instalación es independiente, lo que significa que los paquetes globales de las versiones anteriores instaladas no estarán disponibles en una nueva instalación.

Si tiene la CLI de Gatsby instalada globalmente en la versión 14 de Node, por ejemplo, cuando cambia a la versión 16 o cualquier otra versión usando NVM, la CLI de Gatsby no estará disponible en la versión a la que acaba de cambiar.

Nuevamente, sepa que NVM está basado en Linux, lo que significa que las secciones de instalación y todo lo mencionado anteriormente solo funcionarán para macOS basado en Linux o distribución basada en Linux.

Si es usuario de Windows, consulte este proyecto de <a href="https://github.com/coreybutler/nvm-windows" _target="blanc">Corey Butler</a>, que proporciona NVM para Windows.
