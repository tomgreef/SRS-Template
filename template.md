# Especificación de requisitos 
## Del proyecto Clean-Up

Versión 0.1  
Generada por Tom van Greevenbroek 
Estudiante de la Universidad de Málaga (UMA)
11/04/2020 

Índice
=================
* [Versiones](#versiones)
* 1 [Introducción](#1-introducción)
  * 1.1 [Objetivo del documento](#11-objetivo-del-documento)
  * 1.2 [Ámbito del proyecto](#12-ámbito-del-proyecto)
  * 1.3 [Definiciones, acrónimos y abreviaturas](#13-definiciones-acrónimos-y-abreviaturas)
  * 1.4 [Referencias](#14-referencias)
  * 1.5 [Resumen del documento](#15-resumen-del-documento)
* 2 [Vista general del producto](#2-vista-general-del-producto)
  * 2.1 [Perspectiva del producto](#21-perspectiva-del-producto)
  * 2.2 [Funciones del producto](#22-funciones-del-producto)
  * 2.3 [Restricciones del producto](#23-restricciones-del-producto)
  * 2.4 [Perfiles de usuario](#24-perfiles-de-usuario)
  * 2.5 [Suposiciones y dependencias](#25-suposiciones-y-dependencias)
* 3 [Interfaces externas](#3-interfaces-externas)
    * 3.1 [Interfaces con el Usuario](#31-interfaces-con-el-usuario)
    * 3.2 [Interfaces con el Hardware](#32-interfaces-con-el-hardware)
    * 3.3 [Interfaces con el Software](#33-interfaces-con-el-software)
* 4 [Requisitos](#4-requisitos)
  * 4.1 [Precedencia y prioridad](#41-precedencia-y-prioridad) 
  * 4.2 [Funcionales](#42-funcionales)
  * 4.3 [Calidad de Servicio](#43-calidad-de-servicio)
    * 4.3.1 [Rendimiento](#431-rendimiento)
    * 4.3.2 [Seguridad](#432-seguridad)
    * 4.3.3 [Fiabilidad](#433-fiabilidad)
    * 4.3.4 [Disponibilidad](#434-disponibilidad)
  * 4.4 [Normativas aplicables](#44-normativas-aplicables)
  * 4.5 [Diseño e implementación](#45-diseño-e-implementación)
    * 4.5.1 [Instalación](#451-instalación)
    * 4.5.2 [Distribución](#452-distribución)
    * 4.5.3 [Mantenimiento](#453-mantenimiento)
    * 4.5.4 [Reusabilidad](#454-reusabilidad)
    * 4.5.5 [Portabilidad](#455-portabilidad)
    * 4.5.6 [Coste](#456-coste)
    * 4.5.7 [Fecha de Entrega](#457-fecha-de-entrega)
* 5 [Verificación](#5-verificación)
* 6 [Apendices](#6-apendices) 
  
## Versiones
| Nombre              | Date       | Motivos para el cambio                                 | Versión |
| ------------------- | ---------- | ------------------------------------------------------ | ------- |
|Tom van Greevenbroek | 11/04/2020 | Primera propuesta para la especificación de requisitos | 0.1     |

## 1. Introducción
Este documento contiene todos los requisitos de software que especifican el producto, incluyendo las distintas versiones, que nos servirá para satisfacer todas las necesidad de nuestro **cliente** *Joaquín Ballesteros*.

### 1.1 Objetivo del documento
El propósito de este documento es **mostrar de una forma clara las características o especificaciones** con que cuenta este software.

### 1.2 Ámbito del proyecto
El proyecto trata sobre una plataforma en la que los ciudadanos residentes de un área en concreto podrán publicar desperfectos ubicados en la vía pública, con la intención de que los responsables, en este caso, el Ayuntamiento, los arregle.

Este documento especificará por completo al sistema, ya que el software constará como intermediario entre los usuarios afectados por su zona y los agentes destinados a resolver esas incidencias, permitiendo al ayuntamiento y ciudadanos estar informado sobre todo lo que ocurre en su zona, y permitirá el arreglo de cualquier incidencia si fuese posible por parte del ayuntamiento.

Finalmente, este software podrá ser re-usado por empresas o residencias privadas para estar informado sobre sus zonas y poder mejorarlas. Se pagaría, en forma de suscripción, por cada agente que usaría el software.

### 1.3 Definiciones, acrónimos y abreviaturas
* Usuario - Serán los ciudadanos que usarán el software para comunicar desperfectos.
* Agente - Serán funcionarios del ayuntamiento que resolverán incidencias generadas por usuarios en un provincia de España.
* Subscripción - Pago por mensualidad, a través de adeudos por domiciliación.
* Interfaces - Es posible entenderlo como una superficie con el objeto de aportar información a través de su textura, forma o color. Más sobre esto en la sección de referencias.
* Cliente - Es el ayuntamiento en este caso, pero podría extenderse a cualquiera persona o empresa que quisiese adquirir nuestro sistema.
* RF - Requisitos Funcionales
* RNF - Requisitos No Funcionales


### 1.4 Referencias
Propuesta de proyecto
    : Clean-Up, 10/04/2020 [Documentación GitHub](https://github.com/tomgreef/clean-up/tree/master/Documentacion)

Guías de estilo de interfaz
    : 10/04/2020 [Balsamiq Website](https://balsamiq.com/wireframes/)

Planificación - V1
    : Clean-Up, 10/04/2020 [Documentación GitHub](https://github.com/tomgreef/clean-up/tree/master/Documentacion)

Interfaz
    : 10/04/2020 [Definición de un Interfaz](https://definicion.de/interfaz/)


**//Enumere y enlace cualquier otro documento o dirección web a la que se refiera este SRS. Estos pueden incluir guías de estilo de la interfaz de usuario, contratos, estándares a seguir, especificaciones de requisitos del sistema, documentos de casos de uso o un documento de visión y alcance. Proporcione suficiente información para que el lector pueda acceder a una copia de cada referencia, incluido el título, autor, número de versión, fecha y fuente o ubicación.**

### 1.5 Resumen del documento
Este documento contiene, como complemento a lo anterior, una vista general del producto donde se especifica varios aspectos del producto, al igual que se habrá una sección que trata sobre los interfaces dirigidos a las distintas entidades que usarán este software. Así mismo, tambien contendrá contenido sobre la verificación de todo lo mencionado es este documento.

## 2. Vista general del producto

### 2.1 Perspectiva del producto
El sistema será creado desde cero y consistirá en dos partes: una dirreccionado a los usuarios y otra a los agentes. Ambos accederán a la misma base de datos, aunque tendrían interfaces distintos. 

![example image](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/uml/deployment-diagram/deployment-diagram-example-700x412.jpeg)
*Gratis Omah - [Deployment Diagram Tutorial Lucidchart](https://gratisomah.blogspot.com/2018/08/contoh-hardware-server.html)*

### 2.2 Funciones del producto
Los usuarios podrán publicar incidencias a través de la plataforma web de manera rápida, siempre y cuando tengan una cuenta registrada con nosotros. Una vez publicada, esa incidencia podría ser editada o borrada.

Si la incidencia ya existiese, se le preguntará al usuario de verificar si fuese el mismo o no. En caso que lo fuese, su incidencia se subirá a la plataforma en forma de sub-incidencia, por lo que tendría una relación con la incidencia principal (o primera).

Un agente podrá trabajar con esas incidencias que llegan a su portal, permitiendoles responder a los usuarios para pedir más información o para indicar que esta arreglado, por lo que la incidencia cambiaría a otro estado (cerrado). Una vez cerrado, todas las sub-incidencias de esa incidencia principal serán cerrados también, notificando a todos los usuarios que crearon esas incidencias.

Los agentes también pueden ver en una representación geográfica todas las incidencias, permitiendoles saber que áreas están más afectados. 

### 2.3 Restricciones del producto
Cada incidencia permitirá adjuntar un total de 3 imágenes, con una descripción y título limitado por un número limitado de carácteres.

También se cumplimentará con las leyes sobre la protección de datos establecidos por [La Agencia Española de Protección de Datos](https://www.aepd.es/es).

Finalmente, los agentes debería poder trabajar de forma limitada, hasta sin conección de internet. Ya que podrían haber situaciones en la que no hubiese una coneccion a internet.

### 2.4 Perfiles de usuario
Los perfiles de usuarios serán aquellos ciudadanos que se preocupan por sus entornos, ya que la única forma en la que se pueda arreglar algo en la vía pública es a través del ayuntamiento.

El uso del software también se podrá ver afectado por la experiencia técnica de cada usuario y su nivel educativo.

Por lo tanto, podríamos concluir que solo tendríamos **un solo perfil de usuario** que es aquella que se preocupa por su entorno y sea mayor de edad.

### 2.5 Suposiciones y dependencias
Algunos de los factores asumidos que podría afectar los requisitos establecidos en este documento, son las tecnologías que usaremos. Ya que, podrían cambiar su forma de uso o cambiarlo a una tecnología por la cual se tendría que pagar.

Estas tecnologías son: [Firebase de Google](https://firebase.google.com/) y [Bulma](https://bulma.io/); usados para la base y el desarrollo, respectivamente, de nuestro software.

### 3 Interfaces externas
Esta subsección define todos las interfaces de entrada y salida del sistema de software. Esta sección facilita la comprensión de los requisitos.

#### 3.1 Interfaces con el usuario 
Todos usuarios serán presentados con la página de incidencias, que sería equivalente al de inicio, al entrar en la plataforma web. Si el usuario no ha inicado sesión, se le presentará la opción de iniciar sesión como viene a continuación.

![Login.png](https://www.dropbox.com/s/5iqinnsqjbjbv2m/Login.png?dl=0&raw=1)

Una vez haya iniciado sesión tendrá la opción de crear nuevas incidencias o editar/ver las que ya tenga creadas, y además podrá ver lo que sucede por lo demás en su alrededor. A continuación un ejemplo de una incidencia creada por un usuario:

![Incidencia.png](https://www.dropbox.com/s/0p698v8fhickxum/Incidencia.png?dl=0&raw=1)

Finalmente, los agentes accederán de la misma forma a la plataforma, pero tendrán un interfaz más ampliado respecto a los usuarios, ya que van tener la posibilidad de administrar todas las incidencias, y verlas en una mapa con detalles.

![Agente.png](https://www.dropbox.com/s/lyzt5r3bh2roel4/Agente.png?dl=0&raw=1)

#### 3.2 Interfaces con el Hardware
Dado que la página web no tienen ningún hardware designado, no tiene cualquier interfaz de hardware directa. El GPS físico es administrado por la aplicación GPS en el teléfono móvil usado sólo al crear incidencias, y la conexión de hardware al servidor de la base de datos es administrada por el sistema operativo subyacente en el teléfono móvil y el servidor web.

Por lo tanto, cualquier smartphone que soporte GPS debe ser compatible con las funcionalidades de nuestro sistema. Los datos obtenidos de la GPS serán coordenadas que se usarían para poder localizar la incidencia creada.

#### 3.3 Interfaces con el Software
La plataforma se comunica con el GPS del smartphone para obtener información geográfica sobre dónde se encuentra el usuario a la hora de crear una incidencia. La comunicación entre la base de datos y el portal web consiste en operaciones relacionadas tanto con la lectura como con la modificación de los datos.

## 4. Requisitos
Esta sección especifica los requisitos del producto a nivel de sistema y desglosa estos en diferentes categorías. Para cada requisito usamos el siguiente formato:

### ID - Nombre del requisito
Descripción
##### Dependencias 
##### Prioridad
###
###
***
***
###

### R1 - Tener una conexión al internet
Para el uso de la plataforma web, es necesario tener una conexión con el internet estable. En caso de no tenerla, se producirá un error indicando que no está conectado el internet, normalmente generado por el navegador web.
##### Ninguna
##### Fundamental
###
***

### R2 - Tener la aplicación escritorio
Los agentes podrán tener instalado la aplicación de escritorio para agentes en su PC, accesible desde la plataforma web. Deben tener un Sistema Operativo (OS) de Windows 10 Home o Pro. Además, la aplicación de escritorio tiene un caché para poder seguir resolviendo un número limitado de incidencias sin tener una conexión a internet.
##### R3
##### Fundamental
###
***

### R3 - Crear una cuenta Agente
Los agentes designados por el cliente podrán crear una cuenta poniéndose en contacto con el equipo de administradores. Estos tendrán que verificarlo con el cliente y después podrán ser cambiados a tipo Agente. El agente deberá aceptar las normas establecidas por Clean-Up sobre la ley de la protección de datos.
##### R1
##### Fundamental
###
***

### R4 - Crear una cuenta Usuario
Cualquier persona podrá crear una cuenta de tipo Usuario desde la plataforma web para poder crear incidencias. El usuario deberá aceptar las normas establecidas por Clean-Up sobre la ley de la protección de datos. Finalmente, los usuarios deben de verificar su teléfono móvil a través de un SMS para completar el proceso, y una vez completado, se deberá verificar el correo electrónico.
##### R1
##### Fundamental
###
***

### R5 - Iniciar Sessión
Cualquier persona registrado podrá iniciar sessión en el sistema siempre y cuando tenga una conexión con el internet. La sessión se mantendrá iniciada por un máximo de 1 hora después de que comience la inactividad.
##### R3 - R4
##### Fundamental
###
***

### R6 - Crear incidencias
El usuario y agente pueden crear incidencias con imágenes, título, descripción y coordenadas para ser resueltos por los agentes del cliente. El número máximo de imágenes que se pueden subir son 3 de formato .PNG y .JPG. Los textos estarán limitados a un número máximo de 300 caracteres. Las coordenadas se obtienen desde el GPS del móvil, pero si se solicita la incidencia desde otro lugar, entonces el sistema permitirá el uso de coordenadas. El sistema reconocerá si la incidencia ya existe en el base datos, por lo que pedirá al creador si es la misma. En caso afirmativo, se añadirá esa incidencia como sub-incidencia de la que estaba en la base de datos anteriormente. En caso contrario, se creará una nueva incidencia.
##### R5
##### Fundamental
###
***

### R7 - Información al Usuario
Se debe presentar al usuario toda información necesaria, tanto legal como el funcionamiento del mismo en la parte inferior de la plataforma.
##### Ninguna 
##### Deseable
###
***

### R8 - Editar/Eliminar una incidencia
Los agentes y usuarios podrán editar/eliminar las incidencias. Los usuarios sólo podrán modificar aquellos de los que sean propietarios, mientras que los agentes pueden cambiar cualquier incidencia. La opción de eliminar una incidencia se mostrará a través de un botón que hará que el sistema pida por una confirmación del usuario.
##### R5 
##### Fundamental
###
***

### R9 - Fusionar incidencias
Los agentes tendrán la posibilidad de fusionar una o varias incidencias, seleccionándolas y eligiendo la opción de fusionar. Esto permitirá al agente seleccionar una incidencia como principal y vincular los demás como un sub-incidencia de la principal seleccionado.
##### R10 
##### Deseable
###
***

### R10 - Seleccionar incidencias
Los agentes deberán poder seleccionar varias incidencias a la vez para poder gestionarlas simultáneamente.
##### R5 
##### Deseable
###
***

### R11 - Responder a incidencias
Tanto los usuarios como los agentes podrán comentar en la sección de comentarios de una incidencia. Tras cada respuesta, se notificará al agente o al usuario, dependiendo de quién comentó. Es decir, si el agente escribiera un comentario en una incidencia creado por un usuario, este usuario recibirá una notificación. Los comentarios serán limitados por un máximo de 300 caracteres.
##### R6 
##### Fundamental
###
***

### R12 - Recibir notificaciones
Los agentes y usuarios deberán recibir notificaciones con cualquier cambio que se haya generado a una incidencia de la cual es propietario o asignado. Estas notificaciones podrán ser cambiado en los ajustes de perfil.
##### R14 - R6
##### Deseable
###
***

### R13 - Asignación de incidencias
En el caso de haber múltiples agentes, se podrán asignar las incidencias a un agente. De esta forma, las notificaciones de incidencias asignados al agente llegarán solamente a este agente.
##### R6 
##### Deseable
###
***

### R14 - Ajustes de perfil
Los agentes y usuarios podrán ajustar su perfil en la sección de Ajustes. Aquí podrán cambiar sus datos, eliminar la cuenta, y cambiar la preferencia de notificaciones.
##### R5 
##### Fundamental
###
***

### R15 - Restablecer contraseña
Los usuarios y agentes podrán restablecer su contraseña en la pantalla para iniciar sessión y en los ajustes de perfil.
##### R5 - R14 
##### Fundamental
###
***

### R16 - Estado de incidencias
Los agentes podrán cambiar el estado de las incidencias de tal forma que solo trabajarían con aquellas incidencias que estén en estado "abierta". Y los finalizados estarían en estado "Cerrado".
##### R6 
##### Opcional
###
***

### R17 - Lista de incidencias creados/asignados
Los usuarios y agentes tendrán una pestaña donde podrán ver todas las incidencias que hayan creado/sido asignado. Esta lista enseñará un máximo de 10 incidencias por página.
##### R6 
##### Opcional
###
***

### R18 - Página de inicio
La página principal de la plataforma web para los usuarios será una lista de incidencias que se ubican en su código postal, mientras que para los agentes será una lista de todas las incidencias que quedan por resolver.
##### R16 - R6 
##### Fundamental
###
***

### R19 - Mapa con incidencias
Los agentes tendrán acceso a un mapa con todos las incidencias señalizados por ubicación, permitiendo el acceso a cualquier incidencia desde ese mapa.
##### R6 
##### Deseable
###
***

### R20 - Estadísticas
Los agentes podrán ver en una pestaña de estadísticas donde se verán los tiempos de respuestas y el tiempo en la que se tarda para resolver una incidencia.
##### Ninguna 
##### Opcional
###
***

### R21 - Archivar Incidencias
Las incidencias deberán ser archivados después de estar más de dos años en estado cerrado. Se archivarán a una localización especificado por el cliente o agentes.
##### R6 
##### Opcional
###
***

### ID - Nombre del requisito
Descripción
##### Dependencias 
##### Prioridad
###
***

### ID - Nombre del requisito
Descripción
##### Dependencias 
##### Prioridad
###
***

### ID - Nombre del requisito
Descripción
##### Dependencias 
##### Prioridad
###
***

### ID - Nombre del requisito
Descripción
##### Dependencias 
##### Prioridad
###
***

### ID - Nombre del requisito
Descripción
##### Dependencias 
##### Prioridad
###
***

### 4.1 Precedencia y prioridad
Esta sección está compuesta por una tabla que resumirá todos los requisitos especificados en las secciones siguientes. Se debe detallar un ID único, un nombre de requisito, su descripción, la prioridad de ese requisitos (es algo **Fundamental** a desarrollar; es **Deseable** tenerlo para que el cliente esté satisfecho; o es algo **Opcional** que estaría bien desarrollar si el tiempo lo permite), su precedencia (requisitos que deberán ser implementados antes) y el tipo (funcional o no funcional).

Esta tabla se generará en paralelo a las secciones correspondientes, y se completará cuando todas las secciones estén terminadas. Os recomiendo hacerla en excel e importarla en https://www.tablesgenerator.com/markdown_tables para generar la tabla en formato Markdown. Meter retornos de carro para que no se alarge mucho la tabla y usad la opción *_line break as <br>_* para que esos retornos de carro sean efectivos al copiarlos.


| Id 	| Nombre 	| Descripción 	| Priodidad 	| Precedencia 	| Tipo 	|
|:--:	|:----------------------------:	|:----------------------------------------------------------------------------------------------------------------------------------------------------------------:	|:-------------------:	|:-----------:	|-----------	|
| R3 	| Datos de clientes 	| El sistema deberá registar los datos de los clientes<br>para su posterior tratamiento. Estos incluirán su <br>nombre, DNI, fecha de nacimiento, género y e-mail. 	| <br>Fundamental<br> 	|  	| Funcional 	|
| R4 	| Modificar datos <br>clientes 	| El sistema permitirá modificar el e-mail del cliente. 	| Fundamental 	| R3 	| Funcional 	|
|  	|  	|  	|  	|  	|  	|
	


### 4.2 Funcionales
Esta sección especifica los requisitos funcionales de sistema que el futuro software debe tener en su entorno. Se aconseja poner un enlace al documento de casos de uso generado por magic draw para que el lector tenga una vista general de las funcionalidades del producto a generar.



### 4.3 Calidad de Servicio
Esta sección establece requisitos no funcionales relacionados con la calidad que deben presentar las funcionales del software.
 
#### 4.3.1 Rendimiento
Si existen requisitos no funcionales de rendimiento para el producto en varias circunstancias, indíquelos aquí y explique sus razones, para ayudar a los desarrolladores a comprender la intención y tomar las decisiones de diseño adecuadas. Especifique las restricciones de tiempo. Haga tales requisitos tan específicos como sea posible. Es posible que deba indicar los requisitos de rendimiento para requisitos funcionales o características individuales.

#### 4.3.2 Seguridad
Especifique los requisitos no funcionales relacionados con los problemas de seguridad o privacidad relacionados con el uso del producto. 
* Protección de los datos utilizados o creados por el producto.
* Requisitos de autenticación de identidad de usuario. 
* Políticas o regulaciones externas que contengan problemas de seguridad que afecten al producto. 
* Certificaciones de seguridad o privacidad que deben cumplirse.

#### 4.3.3 Fiabilidad
Especifique los requisitos no funcionales necesarios para establecer la fiabilidad requerida del sistema de software al momento de la entrega.

#### 4.3.4 Disponibilidad
Especifique los requisitos no funcionales necesarios para garantizar un nivel de disponibilidad definido para todo el sistema, tiempo mínimo disponible por día, máximos de reinicios permitidos por tiempo, etc.

### 4.4 Normativas aplicables
Especifique los requisitos no funcionales derivados de las normas o regulaciones existentes, que incluyen:
* Formato de informe
* Nombre de datos
* Procedimientos contables
* Seguimiento de auditoría

### 4.5 Diseño e implementación

#### 4.5.1 Instalación
Restricciones para garantizar que el futuro software se ejecutará sin problemas en la plataforma de implementación de destino.

#### 4.5.2 Distribución
Restricciones en los componentes de software para adaptarse a la estructura distribuida geográficamente de la organización en la que se va a instalar el software, la distribución de datos a procesar o la distribución de dispositivos a controlar.

#### 4.5.3 Mantenimiento
Especifique los atributos del software que se relacionan con la facilidad de mantenimiento del software en sí. Estos pueden incluir requisitos para cierta modularidad, interfaces o limitación de complejidad. Los requisitos no se deben colocar aquí solo porque son buenas prácticas de diseño.

#### 4.5.4 Reusabilidad
Software externo que deberá usarse.

#### 4.5.5 Portabilidad
Especifique los atributos del software que se relacionan con la facilidad de portar el software a otras máquinas host y / o sistemas operativos.

#### 4.5.6 Coste
Especifique las limitaciones en el costo del producto de software.

#### 4.5.7 Fecha de entrega
Especifique, si tiene, fecha de entrega del producto.

## 5. Verificación
Esta sección proporciona los enfoques y métodos de verificación planeados para calificar el software. Se recomienda que los elementos de información para verificación se proporcionen de manera paralela con los elementos de requisitos en la Sección 4. El propósito del proceso de verificación es proporcionar evidencia objetiva de que un sistema o elemento del sistema cumple con los requisitos y características especificados.


## 6. Apendices
### Apéndice A: Ejemplos de este documento relleno
Incluir y referenciar en el documento tantos apéndices como sea necesario. Los siguientes, son ejemplo de este documento (con algunas modificaciones), relleno:

[Ejemplo relleno en inglés 1](https://arxiv.org/pdf/1005.0330.pdf)
[Ejemplo relleno en inglés 2](http://www.cse.chalmers.se/~feldt/courses/reqeng/examples/srs_example_2010_group2.pdf)

### Apéndice B: Generar PDF usando un fichero MD
Hay multitud de herramientas online y offline, por ejemplo: https://www.markdowntopdf.com/
