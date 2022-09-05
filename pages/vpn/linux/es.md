@title = "RiseupVPN para Linux"
@this.alias = '/vpn/linux'

## Requisitos

Para usar el servicio VPN de Riseup, necesitarás instalar el programa RiseupVPN. En Linux, está disponible como «snap», o como paquete en la versión estable de Debian.

RiseupVPN está probado actualmente en **Ubuntu LTS** (18.04) y **Debian Stable**. Si usas otra distribución, puede que funcione o puede que no.

## Instalación a través de Snap

Si usas Ubuntu, snap ya está instalado. De lo contrario, ejecuta:

```
sudo apt install snapd gnome-software-plugin-snap
```

Luego, busca **RiseupVPN** en **Centro de software** o haz clic en este enlace:

<a class="btn btn-default btn-lg" href="snap://riseup-vpn">
  <i class="fa fa-reply-all"></i>
  Abrir RiseupVPN en el centro de software
</a>

Si el enlace de arriba no te funciona, puedes instalarlo por medio de la línea de comandos:

```
sudo snap install --classic riseup-vpn
```

Si te devuelve un error sobre que falta el componente "python" en /usr/bin/env, necesitarás instalar python. Este es el caso de Lubuntu, al menos, desde la versión 19.04.

## Instalación a través de Apt

Ejecuta las siguientes órdenes en una terminal para instalar el paquete correspondiente a la versión estable de Debian.

       sudo apt install leap-archive-keyring
       echo "deb https://deb.leap.se/client release buster" | sudo tee -a /etc/apt/sources.list.d/leap.list
       sudo apt update
       sudo apt install riseup-vpn

## Solución de problemas

### Informe de errores y peticiones de nuevas funcionalidades

RiseupVPN se construye a partir de un programa libre llamado <b>bitmask-vpn</b>.

**Paso 1:** [[Busca en => https://0xacab.org/leap/bitmask-vpn/issues]] si ya se ha informado del error.

**Paso 2:** [[Registra una cuenta => https://0xacab.org/users/sign_in]] con [[0xacab.org => https://0xacab.org]] y accede.

**Paso 3:** Crea un [[informe de fallo o petición de nueva funcionalidad => https://0xacab.org/leap/bitmask-vpn/issues/new]].

Por favor, incluye la siguiente información en el informe de error:

* Pasos para reproducir el error
* Cuál es el comportamiento esperado y qué es lo que ves
* Una captura de pantalla si se trata de un elemento visual
* Tu distribución de Linux y su versión
* El registro del programa

### Obtener los registros

El registro de RiseupVPN se encuentra en tu carpeta «Home»:

```
~/.config/leap/systray.log
```

Al informar de un fallo, es muy útil incluir este archivo de registro.

### Forzar la salida del programa

Si algo deja de funcionar, ejecuta estas órdenes e inténtalo de nuevo.

```
sudo pkill -e -f riseup-vpn
```

### ¿No funciona?

Si el lanzador no funciona, puedes ejecutar RiseupVPN desde la línea de comandos para identificar el problema:

```
/snap/bin/riseup-vpn.launcher
```

La terminal mostrará cualquier error que impida la correcta ejecución del programa.

### Tener un icono visible en la bandeja en GNOME

En las versiones recientes de GNOME no se muestran los iconos en la bandeja del sistema o se muestran en un área muy pequeña en la parte inferior derecha de la pantalla. Para tener visible el icono de RiseupVPN en la esquina superior derecha de la pantalla, puedes instalar la extensión `AppIndicator`
de GNOME y habilitarla:

Para las distribuciones basadas en Debian (solo probado Debian Buster):
* Instala el paquete `gnome-shell-extension-appindicator`, desde el gestor de paquetes o usando esta orden en la terminal: `sudo apt install gnome-shell-extension-appindicator`
* Cierra tu sesión y reábrela, o reinicia tu ordenador
* Abre la aplicación `Tweaks` y, en el panel derecho, selecciona «Extensiones».
* Habilita "Kstatusnotifieritem/appindicator support"
* Disfruta :)

### RiseupVPN en Linux Mint

En Linux Mint, Snap está deshabilitado por defecto, así pues, tienes que habilitarlo primero ejecutando la siguiente orden:

```
sudo mv /etc/apt/preferences.d/nosnap.pref /etc/apt/preferences.d/nosnap.pref.disabled
```

Luego instala Snap:

```
sudo apt install snapd
```

Instala RiseupVPN a través de Snap:

```
sudo snap install --classic riseup-vpn
```

Crea una entrada para RiseupVPN en el menú de Linux Mint:

```
cp /var/lib/snapd/desktop/applications/riseup-vpn_riseup-vpn.desktop /usr/share/applications/
```


### Probar una versión de prelanzamiento

Si quieres ayudarnos con el desarrolloso usando una versión de prelanzamiento de RiseupVPN, puedes instalarla usando esta orden:

```
sudo snap install --classic --beta riseup-vpn
```

### Eliminar archivo PID

A veces, RiseupVPN no se iniciará si cree que hay otra instancia ya ejecutándose.

Si te devuelve este error, ejecuta esta orden:

```
sudo pkill -e -f riseup-vpn
test -f ~/.config/leap/systray.pid && rm -v ~/.config/leap/systray.pid
```

## Código fuente
Los clientes de RiseupVPN están basados en el programa libre Bitmask. El código del cliente para Linux se encuentra [[aquí => https://0xacab.org/leap/bitmask-vpn]].
