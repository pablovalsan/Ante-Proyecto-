# Ante proyecto Pablo Valle Sánchez - I.E.S Romero Vargas - Año 2022-2023 
* Os comento el software New Relic, cuando me puse a investigar sobre el proyecto pensaba que era software libre pero es privado y se usa a través de una plataforma en la nube como Openstacks y vale 130€ por lo que no es viable hacerlo de esa manera, lo podria hacer sin que se usara ese software pero ya seria algo mas simple el proyecto.
También he pensado si no veis bien eso en hacer algo que me parece mas interesante.

* Mi idea para este proyecto de manera general es tener un sistema montado en Windows server 2022 con clientes Windows e intentar si es posible con Linux sé que lanzar maquinas Linux es posible pero que las mismas sean accedidas desde una maquina Linux y no una Windows lo tendré que probar.

* Lo primero será añadir dos interfaces de red que simulará como si tuviera contratado movistar y Vodafone por ejemplo para ejecutar la formación de la NIC para crear un equipo en el que este ambas redes por si una de las dos fallas que el tráfico de toda la red pase a la otra.

* Tendré dos máquinas Windows Server con el Rol de controlador de dominio las cuales funcionaran como servidor DNS para las demás maquinas que configurare, estas también tendrán el rol de Hyper-V, el cual nos permite lanzar máquinas virtuales Windows y Linux las cuales una vez que instale el rol de clusters de conmutación por error podre asignarlas a un clusters que contenga el rol de máquinas virtuales, pero para esto quedan varios pasos previos.

* Para que la red sea lo más eficiente posible configurare una maquina con el rol de SAN ISCSI la cual simulara una red de fibra óptica por la que se accede a los discos donde se alojaran las máquinas virtuales, pero para que esto sea eficiente teniendo más de un nodo principal tengo que configurar dos redes distintas por si una de ellas fallas las cuales simularan como los nodos principales creados anteriormente acceden a ella a través de múltiples rutas gracias al MPIO y al algoritmo de Round Robín para que no haya problemas cuando se acceda al mismo dispositivo de manera simultánea..

* Una vez que tenga las dos máquinas Hyper-V y con una buena comunicación con los discos a través del iniciador ISCSI ya podemos iniciar los discos y darles un formato para que podamos cargar las máquinas virtuales en ellos ya que las mismas se dividen en 3 discos distintos ya que está pensado para miles de máquinas virtuales corriendo simultáneamente.

* En este punto ya puedo instalar el rol de clústeres de conmutación por error en los nodos principales en los que tengo instalado Hyper-v, en cualquiera de los nodos tengo que validar la configuración del sistema que he montado ya que son varias cosas las que depende la una de la otra para que la validación sea correcta, una vez sea validado ya puedo lanzar un clúster con alta disponibilidad por si uno de los nodos principales falla que el otro sea capaz de cargar las rutas de los discos y cargar el trabajo en el de manera automática.
 
* Ya me quedaría poco ya que a través del gestor de Hyper-V una vez validada toda la configuración puedo lanzar máquinas virtuales e instalarlas como si estuviera en un vbox pero dentro de Windows Server, una vez que tenga las máquinas virtuales ya puedo darle un rol a el clúster creado anteriormente de máquinas virtuales y añadir las máquinas virtuales creadas anteriormente, además de crear nuevas y añadirlas al rol de máquinas virtuales.

* Por ultimo quiero configurar un sistema de backup que creo que usare veam backup para ello en una maquina aparte ya que esos datos no pueden estar expuestos en el mismo sitio que el sistema principal. 

* Una vez instalado todo lo anterior quiero configurar una VPN con certificado de servidor en cada nodo Hyper-V y añadir certificado por usuario en cada máquina virtual, configurar la seguridad de Windows server a través de su firewall, crear unidades organizativas con distintas GPO para tener distintos permisos, crear perfiles móviles ya lo que se me vaya ocurriendo de añadido.

* El tiempo exacto no lo sé me lo inventaría si pusiera algo por cada bloque ya que esto puedes tardar 10 minutos en lo más complicado o en un paso simple pierdes 60 minutos por un error que te has dejado en un paso atrás depende de muchas cosas.
