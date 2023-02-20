*Ante proyecto Pablo Valle Sánchez - I.E.S Romero Vargas* - *Año 2022-2023*
***
### Implementación de aplicación web y página web realizada en IAW y su monitorización con New Relic utilizando kubernetes además de su administración remota por SSH
- Lo que tengo pensado hacer es montar una maquina Debian la cual va a funcionar como servidor donde voy a instalar los contenedores (pods), además voy a tener dos máquinas (workers) que serán las encargadas de replicar la carga de trabajo entre ellas teniendo un controlador desde el que las gestionaremos. 
-  Administrare la web que realice en IAW la cual la tendré alojada en un dominio externo, pero podremos ver su rendimiento a través de New Relic.
- En otro contenedor (pods) aislado del anterior voy a instalar alguna aplicación web como letsChat u otra que encuentre cuando lo realice.
- En otro contenedor (pods) aislado del anterior voy a intentar instalar ChatGPT, pero no sé si será posible he estado probando y me ha estado dando errores, pero he visto que se puede implementar seguiré investigando sobre ello.
- También tengo la idea de crear una vpn en mi servidor y crear un túnel hacia una maquina cliente la cual será la que use para acceder de manera remota al servidor lo cual provocará que sea un contenedor privado exclusivo de esa máquina. para aumentar su seguridad, pero nose si será posible ya que el proyecto lo realizare en mi casa con una direccion de red distinta a la del instituto o quizás cree dos túneles e inhabilite el del centro hasta el día de la presentación a modo de demostración ya que no se si habrá problemas en la comunicación entre los workers y el controlador.
 - Lo último que realizare será la instalación de la herramienta de New Relic la cual es capaz de medir el rendimiento de una infraestructura de servicios como puede la que orqueste en kubernetes con las distintas aplicaciones web que instale, con esta aplicación podemos realizar mediciones tanto del Fronted como del Backend viendo, así como es el acceso y la carga de los distintos archivos cargados en el servidor
   * Podemos monitorizar conexiones por HTTP (tiempo de espera, número de peticiones...)
   * Estadísticas de uso según el usuario que este en esa aplicación web o sistema.
   * Crear tareas para que se realicen procesos automáticamente
   * Fijar avisos por si el sistema no está funcionando como lo hace regularmente
   * Uso del hardware del sistema
   * Crear alertas y gestionar eventos
***
### Software necesario para realizar el proyecto
- Servidor Debian instalado en máquina virtual (Controlador)
  * Edición de la página web realizada en IAW para que quede mejor y con más funciones (5 Horas)
  * Instalar Debian, Openssh, Openssl para generar una clave pública y privada para posteriormente acceder de manera remota a la maquina *** (1 Hora)
  * Configurar los directorios /etc/hosts, /etc/hostname, /etc/resolv.conf *** (5 Minutos)
  * Instalacion del servicio de Bind9 por si tengo que gestionar la zona de la aplicación web que instale. *** (10 Minutos)
  * Configuración de la dirección IP estática de la máquina. *** (3 Minutos)
  * Instalacion de minikube *** (20 Minutos)
  * Instalación de Docker y sus dependencias (Viene bien por los paquetes que carga en su instalación para evitar errores posteriores de dependencias) *** (10 Minutos)
  * Instalacion de la herramienta Helm (Tratamiento de aplicaciones complejas en kubernetes) *** (3 Minutos)
  * Instalacion de Kubectl *** (10 Minutos)
  * Instalacion de k3s *** (15 Minutos)
  * Configurar los distintos servicios instalados previamente ya que por lo que he estado viendo a veces da errores según la versión que se esté usando. *** (6 Horas)
  * Comprobación de que los servicios instalados funcionan bien con algún pods de prueba *** (10 minutos)
  * Despliegue de la aplicación web *** (1 Hora)
  * Instalacion y configuración de la herramienta New Relic *** (1 Hora) 
  * Configuración de la seguridad de Kubernetes *** (30 minutos)
  * Configuración de la gestión de una página externa a través de New Relic ** (1 Hora)
  * Crear eventos a través de la herramienta New Relic *** (30 Minutos)
  * Gestión de Logs a través de New Relic creando avisos según los parámetros que este indicando en un momento especifico. *** (30 Minutos) 
  * Monitorización de las distintas aplicaciones instaladas. *** (30 Minutos)
  * Configuración de la repartición de trabajo entre los Workers *** (3 Horas)
  * Problemas que surjan con el desarrollo del proyecto (4 Horas)
***
### Servidor Debian instalado en máquina virtual (2 Maquinas(workers))
  * Instalar Debian Openssh, Openssl, pero esta vez exportare la clave privada y se la pondré a las dos máquinas también para no estar con dos claves públicas y dos privadas. *** (1 Hora)
  * Configurar los directorios /etc/hosts, /etc/hostname, /etc/resolv.conf *** (5 Minutos)
  * Instalacion del servicio de Bind9 por si tengo que gestionar la zona de la aplicación web que instale. (30 Minutos)
  * Configuración de la dirección IP estática de la máquina. *** (5 Minutos)
  * Instalacion de k3s *** (15 Minutos)
  * Instalación de Docker y sus dependencias (Viene bien por los paquetes que carga en su instalación para evitar errores posteriores de dependencias) *** (10 Minutos)
  * Insertar el token del controlador *** (15 Minutos)
  * Instalar Kubectl *** (10 Minutos)
  * Instalar distintos servicios que me iré encontrando que son necesarios *** (30 Minutos)
  * Configuración de los distintos servicios hasta que los workers sean nodos visibles desde el controlador, entonces podre desplegar las aplicaciones web *** (4 Horas)
  * Problemas que surjan con el desarrollo del proyecto (4 Horas)
***
**Hasta aquí la presentación de la idea de Proyecto de fin de ciclo**
***
#### Tiempo estimado para realizar el proyecto
* Mi calculo según lo que he estado mirando es de unas 45 Horas en principio sino salen demasiados errores si eso ocurriera ya en la entrega del proyecto reajustaría los tiempos de cada apartado ya que la configuración de los distintos servicios es compleja además del lanzamiento de los pods con la distribución de carga en los workers es algo que nunca he realizado, pero lo veo posible y factible para realizarlo como proyecto de ASIR.
***

