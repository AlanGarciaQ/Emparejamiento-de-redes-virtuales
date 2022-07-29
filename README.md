# Emparejamiento de redes virtuales
**Objetivo:** Emparejar dos redes virtuales localizadas cada una en diferentes maquinas virtuales.  

![](/imagenes/virtual_.png)

**Requisitos**
- Cuenta de Azure con una suscripción activa
- Equipo de cómputo con sistema operativo: Windows, Linux o MacOs. 

**Pasos**  
Se inicia sesión en Portal.Azure.com  
En la barra de búsqueda escribimos “Grupos de Recursos” y lo seleccionamos.  
Damos clic en el apartado crear.  
En la pestaña datos básicos, llenamos lo siguiente:

**En Detalles del proyecto**  
Suscripción: La suscripción que queramos utilizar.  
Grupo de recursos: Podemos crear uno o seleccionar uno ya existente.

**En Detalles del recurso**  
Región: Podemos escoger cualquiera, pero si no queremos que haya mucha latencia escogemos uno cercano a donde vivimos. 

Para terminar, damos clic en el botón de revisar y crear, y luego en crear.  
![Imagen 1](/imagenes/Imagen1.png)

Cuando se termine de crear nuestro grupo de recursos, buscaremos en la barra de búsqueda “Redes virtuales” y lo seleccionamos.  
Damos clic en el apartado crear.  
En la pestaña datos básicos, llenamos lo siguiente:

**En Detalles del proyecto**  
Suscripción: La suscripción que utilizamos anteriormente.  
Grupo de recursos: Utilizamos el grupo de recursos que creamos hace unos momentos.

**En Detalles de Instancia**  
Nombre: Pondremos el que queramos.  
Región: Podemos escoger cualquiera, pero si no queremos que haya mucha latencia escogemos uno cercano a donde vivimos.(Nota: Como vamos a crear máquinas virtuales más adelante , la región debe ser la misma tanto en redes virtuales como en máquinas virtuales). 

Damos clic en el botón de Siguiente: Direcciones IP.  
![](/imagenes/Imagen2.png)

Nota: Este paso puede ser optativo ya que se puede utilizar la subred que viene por defecto. De no querer hacerlo puede dar clic en el botón de revisar y crear, y después en crear. Si quiere realizarlo continue leyendo. 

En la pestaña Direcciones IP, haremos lo siguiente:  
Seleccionaremos el botón agregar subred, en seguida en la parte derecha aparecerá un apartado donde tendremos que colocar:  
Nombre de la subred: Pondremos el nombre que queramos.  
Intervalo de esa subred: Pondremos el intervalo que queramos. (Nota: si queremos poner la subred 10.0.0.0/24 antes tenemos que eliminar la subred que viene por defecto).  
Daremos clic en el botón de agregar. 

Para terminar, damos clic en el botón de revisar y crear, y luego en crear.  
![](/imagenes/Imagen3.png)

Cuando se termine de crear nuestro recurso, procederemos a crear otra red virtual, siguiendo los mismos pasos que utilizamos para crear la red virtual anterior.

Cuando se termine de crear nuestra nueva red virtual, procederemos a crear una maquina virtual, este proceso ya se describió anteriormente en la práctica llamada “Creación de una máquina virtual”(Dar clic sobre el nombre para que los lleve a esta práctica mencionada.) Seguiremos los mismos pasos que se describen en esa practica solo que en esta ocasión en lugar de seleccionar Windows en la opción de Imagen seleccionaremos Linux y en tipo de Autentificación va a ser con contraseña (Guardamos esta contraseña, ya que se utilizara más adelante).  
En esta ocasión también nos iremos a la pestaña de redes en donde seleccionaremos en el apartado de red virtual, la primer red virtual que creamos. 

Para terminar, damos clic en el botón de revisar y crear, y luego en crear.  
![](/imagenes/Imagen4.png)

Cuando se termine de crear nuestro recurso, procederemos a crear otra máquina virtual como la que se creo anteriormente, solo que esta vez en la pestaña de redes pondremos la segunda red virtual que hicimos.

Cuando se termine de crear esta nueva maquina virtual,  nos iremos al grupo de recursos que contiene a las dos máquinas virtuales. Seleccionaremos la primer máquina virtual que hicimos.  
En el menú de la parte de la izquierda le damos clic en la opción de conectar, a continuación, en el menú de la parte de arriba le damos clic en conectar y seleccionamos la opción de SSH.  
Copiaremos el código que se muestra en el apartado 4 y daremos clic en el botón de Cloud Shell, el icono que está al lado de la barra de búsqueda. Si nos aparece que no tenemos un almacenamiento montado seleccionaremos la opción de crear.  
![](/imagenes/Imagen5.png)

Se nos abrirá una ventana de comandos, en la parte superior izquierda de esa ventana, seleccionaremos la opción de Bash (Este sería el SSH), en la línea de comandos pegaremos lo habíamos copiado anteriormente y daremos enter.  
Nos preguntara si queremos continuar, le podremos que yes. En seguida se nos pedirá la contraseña que pusimos al crear nuestra máquina virtual. 

Con todos los pasos descritos anteriormente habremos ingresado a nuestra máquina virtual. Si queremos comprobar que estamos dentro pondremos sudo apt-get moo, si nos aparece una vaquita es que estamos dentro.  
![](/imagenes/Imagen6.png)

Nos iremos al grupo de recursos que contiene nuestros recursos que hemos creado. Seleccionaremos la primer red virtual que hicimos.  
En el menú de la izquierda le daremos en emparejamientos, ahí dentro le daremos en agregar. 
![](/imagenes/Imagen7.png)

En la ventana que se nos abrió modificaremos los siguientes aspectos:  
Nombre del vínculo de emparejamiento: Pondremos este nombre: redvirtual1-redvirtual2.  
Red Virtual Remota(Nombre del vínculo de emparejamiento): Pondremos el mismo nombre que el anterior, pero al revés: redvirtual2-redvirtual1.  
Red virtual: seleccionaremos la segunda red virtual que es la que queremos emparejar.

Damos clic en agregar.  
![](/imagenes/Imagen8.png)

Cuando en estado del emparejamiento diga conectado, nos iremos a Cloud Shell de la máquina virtual 1(Donde nos encontrábamos anteriormente) y haremos una prueba con ping para saber si ya está conectado.
![](/imagenes/Imagen9.png)

Con esto emparejamos dos redes virtuales exitosamente.


