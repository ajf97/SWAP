# Práctica 1. Preparación de las herramientas

### Alejandro Jerónimo Fuentes

## Instalación

En primer lugar, lo que hacemos es instalar ubuntu server 18.04. Lo marcamos todo con la configuración por defecto e instalamos `OpenSSH Server`:

![](images/Anotación&#32;2020-02-18&#32;175321.png)

Dado que no se puede instalar el servidor LAMP (Apache + PHP + MySQL) desde el asistente de instalación de ubuntu, lo que haremos será instalar el paquete `tasksel`:

```shell
$ sudo apt update
$ sudo apt install tasksel
$ sudo tasksel
```

Ahora podremos instalar la pila LAMP:

![](images/Anotación&#32;2020-02-18&#32;183443.png)

A continuación, activamos la cuenta del usuario root para no tener que usar sudo:

```shell
$ sudo passwd root
```

Comprobamos que Apache está instalado y ejecutándose:

![](images/Anotación&#32;2020-02-18&#32;184222.png)

No es necesario instalar `curl` porque ya se encuentra instalado por defecto. A continuación, comprobamos si Apache funciona correctamente. Para ello creamos el siguiente código en `/var/www/html`:

```html
<html>
<body>
Página de ejemplo para ajf97 en mv1
</body>
</html>
```

Anotamos la direcciones IP del servidor:

![](images/Anotación&#32;2020-03-09&#32;164132.png)

La dirección `10.0.2.4` corresponde a la red NAT y `192.168.56.12` a la red solo-anfitrión.

Vemos como Apache funciona correctamente al acceder a la página a través de la IP `10.0.2.4`:

![](images/Anotación&#32;2020-03-09&#32;170629.png)


## Configuración de la red NAT y modo solo-anfitrión

Después de hacer todos los pasos de la sección anterior, creamos otra máquina virtual con la misma configuración.

Para crear una red NAT nos vamos a la configuración de virtualbox y creamos la red con la siguiente configuración:

![](images/Anotación&#32;2020-02-18&#32;195751.png)

Después nos vamos a la configuración específica de cada máquina virtual y cambiamos el adaptador de red a red NAT para cada una de las máquinas virtuales:

![](images/Anotación&#32;2020-02-18&#32;193920.png)

Por último, añadimos otro adaptador de red en cada máquina virtual y seleccionamos el adaptador del anfitrión:

![](images/Anotación&#32;2020-03-09&#32;163234.png)

Para la configuración de la red solo-anfitrión con `netplan`, he seguido la guía de este [enlace](https://askubuntu.com/questions/293816/in-virtualbox-how-do-i-set-up-host-only-virtual-machines-that-can-access-the-in/1013467#1013467).


## Cuestiones a resolver

Por último, accedemos por ssh de una máquina a otra:

![](images/Anotación&#32;2020-02-18&#32;200608.png)

![](images/Anotación&#32;2020-02-18&#32;200704.png)

Y accedemos con `curl` de una máquina a otra a las páginas que hemos creado anteriormente:

![](images/Anotación&#32;2020-03-09&#32;171012.png)
![](images/Anotación&#32;2020-03-09&#32;170958.png)

También podemos acceder desde el anfitrión desde el navegador:

![](images/Anotación&#32;2020-03-09&#32;171154.png)
![](images/Anotación&#32;2020-03-09&#32;171131.png)

Y mediante `ssh`:

![](images/Anotación&#32;2020-03-09&#32;165318.png)
![](images/Anotación&#32;2020-03-09&#32;165402.png)
