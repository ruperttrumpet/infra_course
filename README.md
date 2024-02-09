# infra_course
## Estructura de ficheros
### provider.tf
En este fichero se define el proveedor de la nube que utilizaremos y dónde vamos a guardar el estado de nuestra infraestructura.  
+ Primero definimos el bloque provider y le definimos el proveedor AWS.
    + Internamente definimos el argumento region para definir la región dónde vamos a trabajar.
+ El segundo bloque será el bloque terraform.
    + Dentro vamos a definir otro bloque llamado backend definido como local para que nuestro terraform state quede almacenado localmente.
        + Necesitamos del argumento path llamado terraform.tfstate que es el fichero en el que se almacena nuestra infraestructura. 
### vpc.tf
Es un fichero de recursos donde se pueden modelar partes de la infraestructura.  
+ Primero definimos el bloque resource después especificamos el tipo de recurso que en este caso es aws_vpc y le asignamos un label (nombre).
    + El primer argumento de este bloque será cidr_block que define el dominio de nuestras direcciones IP que se setean desde el fichero var.tf
    + El segundo argumento es enable_dns_hostnames como true y estó habilitará un servicio DNS de AWS para uso de nuestras máquinas en nuestra red privada.
    + El tercero será tags para asignar etiquetas a nuestro recurso y que sirven para identificar nuestro recurso.
### locals.tf
En este fichero se asignan nombres a algunas expresiones y después pueden ser reutilizados en otros recursos o ficheros.  
+ Primero definimos el bloque locals y dentro definimos algunas expresiones, les asignamos nombre para ser reutilizados.
### var.tf
En este fichero se declaran las variables de entrada que son parámetros de configuración.  
+ Se define el bloque variable y se le asigna un nombre.
    + Se puede agregar el argumento description.
    + Se puede agregar el argumento default para definir un valor por defecto.
    + Se puede agregar el argumento type para indicar el tipo de variable.
### tfvars.json
En este fichero se da un valor a cada variable definida en el fichero var.tf.  
### terraform.tfstate
No lo generamos nosotros pero podemos decidir dónde se crea si en local o en un repositorio externo.  
Almacena la información de los recursos que hemos desplegado usando Terraform
