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
  * 4.2 [Calidad de Servicio](#42-calidad-de-servicio)
    * 4.2.1 [Rendimiento](#421-rendimiento)
    * 4.2.2 [Seguridad](#422-seguridad)
    * 4.2.3 [Disponibilidad](#423-disponibilidad)
  * 4.3 [Diseño e implementación](#43-diseño-e-implementación)
    * 4.3.1 [Reusabilidad](#431-reusabilidad)
    * 4.3.2 [Fecha de Entrega](#432-fecha-de-entrega)
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
El proyecto trata sobre **una plataforma en la que los ciudadanos residentes de un área en concreto podrán publicar desperfectos ubicados en la vía pública**, con la intención de que los responsables, en este caso, el Ayuntamiento, los arregle.

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

### 1.5 Resumen del documento
Este documento contiene, como complemento a lo anterior, **una vista general del producto** donde se especifica **varios aspectos del producto**, al igual que se habrá una sección que trata sobre los interfaces dirigidos a las distintas entidades que usarán este software. Así mismo, también contendrá contenido sobre la verificación de todo lo mencionado es este documento.

## 2. Vista general del producto

### 2.1 Perspectiva del producto
El sistema será creado desde cero y consistirá en dos partes: una para los usuarios y otra para los agentes. Ambos accederán a la misma base de datos, aunque tendrían interfaces distintos. 

![example image](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/uml/deployment-diagram/deployment-diagram-example-700x412.jpeg)
*Gratis Omah - [Deployment Diagram Tutorial Lucidchart](https://gratisomah.blogspot.com/2018/08/contoh-hardware-server.html)*

### 2.2 Funciones del producto
Los usuarios podrán publicar incidencias a través de la plataforma web de manera rápida, siempre y cuando tengan una cuenta registrada con nosotros. Una vez publicada, esa incidencia podría ser editada o borrada.

Si la incidencia ya existiese, se le preguntará al usuario de verificar si fuese el mismo o no. En caso que lo fuese, su incidencia se subirá a la plataforma en forma de sub-incidencia, por lo que tendría una relación con la incidencia principal (o primera).

Un agente podrá trabajar con esas incidencias que llegan a su portal, permitiéndoles responder a los usuarios para pedir más información o para indicar que esta arreglado, por lo que la incidencia cambiaría a otro estado (cerrado). Una vez cerrado, todas las sub-incidencias de esa incidencia principal serán cerrados también, notificando a todos los usuarios que crearon esas incidencias.

Los agentes también pueden ver en una representación geográfica todas las incidencias, informando al agente sobre que áreas están más afectados. 

### 2.3 Restricciones del producto
Cada incidencia permitirá adjuntar un total de 3 imágenes, con una descripción y título limitado por un número limitado de carácteres.

También se cumplimentará con las leyes sobre la protección de datos establecidos por [La Agencia Española de Protección de Datos](https://www.aepd.es/es).

Finalmente, los agentes debería poder trabajar de forma limitada, hasta sin conexión de internet. Ya que podrían haber situaciones en la que no hubiese una conexión a internet.

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
#### Dependencias 
#### Prioridad
###
###
***
***
###

### R1 - Conexión al internet
Para el uso de la plataforma web, es necesario tener una conexión con el internet estable.
#### Ninguna
#### Fundamental
###
***

### R1.1 - Navegador Web
Para el correcto funcionamiento de la aplicación, es necesario que el navegador web soporte HTML5, geolocalización y subida de imágenes.
#### Ninguna
#### Fundamental
###
***

### R2 - Aplicación de escritorio
Los agentes podrán tener instalado la aplicación de escritorio para agentes en su PC, accesible desde la plataforma web. Además, la aplicación de escritorio tendrá un caché para poder seguir resolviendo un número limitado de incidencias sin tener una conexión a internet.
#### R3
#### Fundamental
###
***

### R2.1 - Sistema operativo
Deben tener un sistema operativo de Windows 10 Home o Pro.
#### R3
#### Fundamental
###
***

### R3 - Crear una cuenta Agente
Los agentes designados por el cliente podrán crear una cuenta poniéndose en contacto con el equipo de administradores. Estos tendrán que verificarlo con el cliente y después podrán ser cambiados a tipo Agente.
#### R1
#### Fundamental
###
***

### R4 - Crear una cuenta Usuario
Cualquier persona podrá crear una cuenta de tipo Usuario desde la plataforma web para poder crear incidencias.
#### R1
#### Fundamental
###
***

### R4.1 - GDPR
Los usuarios y agentes deberán aceptar las normas establecidas por Clean-Up sobre la ley de la protección de datos.
#### R1 - R22
#### Fundamental
###
***

### R4.2 - Verificación de cuenta Usuario
Los usuarios deben de verificar su teléfono móvil a través de un SMS para completar el proceso, y una vez completado, se deberá verificar el correo electrónico.
#### R1
#### Fundamental
###
***

### R5 - Iniciar sesión
Cualquier persona registrado podrá iniciar sesión en el sistema siempre y cuando tenga una conexión con el internet.
#### R3, R4
#### Fundamental
###
***

### R5.1 - Tiempo de inactividad
La sesión se mantendrá iniciada por un máximo de 1 hora después de que comience la inactividad.
#### R5
#### Fundamental
###
***

### R6 - Crear incidencias
El usuario y agente podrán crear incidencias con imágenes, título, descripción y coordenadas para ser resueltos por los agentes del cliente.
#### R5
#### Fundamental
###
***

### R6.1 - Imágenes en una incidencia
El número máximo de imágenes que se pueden subir son 3 de formato .PNG y .JPG con una capacidad máxima de 50 Mb por incidencia.
#### R5
#### Fundamental
###
***

### R6.2 - Amplitud del texto
Los textos estarán limitados a un número máximo de 250 caracteres.
#### R5
#### Deseable
###
***

### R6.3 - Coordenadas GPS
Las coordenadas se obtienen desde el GPS del móvil o a través del uso de coordenadas.
#### R5
#### Fundamental
###
***

### R6.4 - Duplicado de incidencia
El sistema reconocerá si la incidencia ya existe en la base datos, por lo que pedirá al creador si es la misma. En caso afirmativo, se añadirá esa incidencia como sub-incidencia de la que estaba en la base de datos anteriormente. En caso contrario, se creará una nueva incidencia.
#### R5
#### Fundamental
###
***

### R7 - Información al usuario
Se presentará al usuario toda información necesaria, tanto legal como el funcionamiento del mismo en la parte inferior de la plataforma.
#### Ninguna 
#### Fundamental
###
***

### R8 - Editar/Eliminar una incidencia
Los agentes y usuarios podrán editar/eliminar las incidencias. Los usuarios sólo podrán modificar aquellos de los que sean propietarios, mientras que los agentes pueden cambiar cualquier incidencia. La opción de eliminar una incidencia se mostrará a través de un botón que hará que el sistema pida por una confirmación del usuario.
#### R5 
#### Fundamental
###
***

### R9 - Fusionar incidencias
Los agentes tendrán la posibilidad de fusionar una o varias incidencias, seleccionándolas y eligiendo la opción de fusionar. Esto permitirá al agente seleccionar una incidencia como principal y vincular los demás como un sub-incidencia de la principal seleccionado.
#### R10 
#### Deseable
###
***

### R10 - Seleccionar incidencias
Los agentes deberán poder seleccionar varias incidencias a la vez para poder gestionarlas simultáneamente.
#### R5 
#### Deseable
###
***

### R11 - Responder a incidencias
Tanto los usuarios como los agentes podrán comentar en la sección de comentarios de una incidencia. Tras cada respuesta, se notificará al agente o al usuario, dependiendo de quién comentó. Es decir, si el agente escribiera un comentario en una incidencia creado por un usuario, este usuario recibirá una notificación.
#### R6 - R6.2
#### Fundamental
###
***

### R12 - Recibir notificaciones
Los agentes y usuarios deberán recibir notificaciones con cualquier cambio que se haya generado a una incidencia de la cual es propietario o asignado. Estas notificaciones podrán ser cambiado en los ajustes de perfil.
#### R14 - R6
#### Deseable
###
***

### R13 - Asignación de incidencias
Se podrán asignar las incidencias a un agente. De esta forma, las notificaciones de incidencias asignados al agente llegarán solamente a este agente.
#### R6 
#### Deseable
###
***

### R14 - Ajustes de perfil
Los agentes y usuarios podrán ajustar su perfil en la sección de Ajustes. Aquí podrán cambiar sus datos, eliminar la cuenta, y cambiar la preferencia de notificaciones.
#### R5 
#### Fundamental
###
***

### R15 - Restablecer contraseña
Los usuarios y agentes podrán restablecer su contraseña en la pantalla de inicio de sesión y en los ajustes de perfil.
#### R5 - R14 
#### Fundamental
###
***

### R16 - Estado de incidencias
Los agentes podrán cambiar el estado de las incidencias de tal forma que solo trabajarían con aquellas incidencias que estén en estado "abierta". Y los finalizados estarían en estado "Cerrado".
#### R6 
#### Deseable
###
***

### R17 - Lista de incidencias creados/asignados
Los usuarios y agentes tendrán una pestaña donde podrán ver todas las incidencias que hayan creado/sido asignado. Esta lista enseñará un máximo de 10 incidencias por página.
#### R6 
#### Deseable
###
***

### R17.1 - Máximo número de incidencias en una lista
Las listas enseñarán un máximo de 10 incidencias por página.
#### R6 
#### Opcional
###
***

### R18 - Página de inicio
La página principal de la plataforma web para los usuarios será una lista de incidencias que se ubican en su código postal, mientras que para los agentes será una lista de todas las incidencias que se les hayan asignado y estén abiertos.
#### R16 - R6 
#### Fundamental
###
***

### R19 - Mapa con incidencias
Los agentes tendrán acceso a un mapa con todos las incidencias señalizados por ubicación, permitiendo el acceso a cualquier incidencia desde ese mapa.
#### R6 
#### Deseable
###
***

### R20 - Estadísticas
Los agentes podrán ver en una pestaña de estadísticas donde se verán los tiempos de respuestas y el tiempo en la que se tarda para resolver una incidencia.
#### Ninguna 
#### Opcional
###
***

### R21 - Archivar incidencias
Las incidencias deberán ser archivados después de estar más de dos años en estado cerrado. Se archivarán a una localización especificado por el cliente o agentes.
#### R6 - R16
#### Opcional
###
***

### R22 - Certificación SSL
Para cumplir con las normas de GDPR, se usarán certificaciones SSL.
#### Ninguna 
#### Fundamental
###
***

### R23 - Rellenando datos
En cualquier proceso de rellenar datos como es la creación de una cuenta o una incidencia, se le permitirá un tiempo máximo de 10 minutos.
#### R3 - R4 - R6 
#### Deseable
###
###
***
***
###

### 4.1 Precedencia y prioridad

| **ID**    | **Nombre**                                      | **Descripción**                                                                                                                      | **Priodidad**   | **Precedencia** | **Tipo**         |
|-------|---------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|-------------|-------------|--------------|
| R1    | Conexión de internet                        | Deberán tener una conexión estable con el internet                                                                               | Fundamental |             | Funcional    |
| R1.1  | Navegador web                               | Es necesario que el navegador web soporte HTML5,  geolocalización y subida de imágenes                                           | Fundamental |             | No Funcional |
| R2    | Aplicación de  escritorio                   | Los agentes necesitan poder instalar la aplicación  en su PC                                                                     | Fundamental | R3          | Funcional    |
| R2.1  | Sistema Operativo                           | Deben tener un sistema operativo de Windows 10 Home  o Pro                                                                       | Fundamental | R3          | No Funcional |
| R3    | Crear una cuenta  Agente                    | Los agentes designados por el cliente podrán crear  una cuenta poniéndose en contacto con el equipo de  administradores          | Fundamental | R1          | Funcional    |
| R4    | Crear una cuenta  Usuario                   | Cualquier persona podrá crear una cuenta de tipo  Usuario desde la plataforma web                                                | Fundamental | R1          | Funcional    |
| R4.1  | GDPR                                        | Los usuarios y agentes deberán aceptar las normas  establecidas por Clean-Up sobre la ley de la  protección de datos             | Fundamental | R1, R22          | No Funcional |
| R4.2  | Verificación de  cuenta Usuario             | Los usuarios deben de verificar su teléfono móvil  y correo electrónico                                                          | Fundamental | R1          | No Funcional |
| R5    | Iniciar sesión                              | Cualquier persona registrado podrá iniciar sesión  en el sistema desde la plataforma web                                         | Fundamental | R3,R4       | Funcional    |
| R5.1  | Tiempo de  inactividad                      | La sesión se mantendrá iniciada por un máximo de  1 hora después de que comience la inactividad                                  | Fundamental | R5          | No Funcional |
| R6    | Crear incidencias                           | El usuario y agente podrán crear incidencias con  imágenes, título, descripción y coordenadas                                    | Fundamental | R5          | Funcional    |
| R6.1  | Imágenes en una  incidencia                 | El número máximo de imágenes que se pueden subir  son 3 de formato .PNG y .JPG con una capacidad  máxima de 50 Mb por incidencia | Fundamental | R5          | No Funcional |
| R6.2  | Amplitud del texto                          | Los textos estarán limitados a un número máximo  de 250 caracteres                                                               | Deseable    | R5          | No Funcional |
| R6.3  | Coordenadas GPS                             | Las coordenadas se obtienen desde el GPS del  móvil o a través del uso de coordenadas                                            | Fundamental | R5          | No Funcional |
| R6.4  | Duplicado de  incidencias                   | El sistema reconocerá si la incidencia ya existe  en la base datos, por lo que pedirá al creador  si es la misma                 | Fundamental | R5          | Funcional    |
| R7    | Información al  usuario                     | Se presentará al usuario toda información  necesaria                                                                             | Fundamental |             | Funcional    |
| R8    | Editar/Eliminar  una incidencia             | Los agentes y usuarios podrán editar/eliminar las  incidencias que se les hayan asignado o creado,  respectivamente              | Fundamental | R5          | Funcional    |
| R9    | Fusionar incidencias                        | Los agentes tendrán la posibilidad de fusionar  una o varias incidencias                                                         | Deseable    | R10         | Funcional    |
| R10   | Seleccionar  incidencias                    | Los agentes deberán poder seleccionar varias  incidencias a la vez                                                               | Deseable    | R5          | Funcional    |
| R11   | Responder a  incidencias                    | Tanto los usuarios como los agentes podrán  comentar en la sección de comentarios de una  incidencia                             | Fundamental | R6          | Funcional    |
| R12   | Recibir  notificaciones                     | Los agentes y usuarios deberán recibir  notificaciones con cualquier cambio que se haya  generado que esté relacionado a ellos   | Deseable    | R6, R14     | Funcional    |
| R13   | Asignación de  incidencias                  | Se podrán asignar las incidencias a un agente                                                                                    | Deseable    | R6          | Funcional    |
| R14   | Ajustes de perfil                           | Los agentes y usuarios podrán ajustar su perfil  en la sección de Ajustes                                                        | Fundamental | R5          | Funcional    |
| R15   | Restablecer  contraseña                     | Los usuarios y agentes podrán restablecer su  contraseña en la pantalla de inicio de sesión  y en los ajustes de perfil          | Fundamental | R5, R14     | Funcional    |
| R16   | Estado de  incidencias                      | Los agentes podrán cambiar el estado de las  incidencias                                                                         | Deseable    | R6          | Funcional    |
| R17   | Lista de  incidencias                       | Los usuarios y agentes tendrán una pestaña donde  podrán ver todas las incidencias que hayan  creado/sido asignado               | Deseable    | R6          | Funcional    |
| R17.1 | Máximo número de  incidencias en  una lista | Las listas enseñarán un máximo de 10 incidencias  por página                                                                     | Opcional    | R6          | No Funcional |
| R18   | Página de inicio                            | Muestra una lista de incidencias relevante al  usuario y agente                                                                  | Fundamental | R6, R16     | Funcional    |
| R19   | Mapa con incidencias                        | Los agentes tendrán acceso a un mapa con todos  las incidencias señalizados por ubicación                                        | Deseable    | R6          | Funcional    |
| R20   | Estadísticas                                | Los agentes podrán ver en una pestaña de  estadísticas sobre las incidencias                                                     | Opcional    |             | Funcional    |
| R21   | Archivar incidencias                        | Las incidencias deberán ser archivados después  de estar más de dos años en estado cerrado                                       | Opcional    | R6, R16     | No Funcional |
| R22   | Certificación SSL                              | Se usarán certificaciones SSL                                                                                                    | Fundamental |             | No Funcional |
| R23   | Rellenando datos                            | Se permitirá un tiempo máximo de 10 minutos  para rellenar un formulario                                                         | Deseable    | R3, R4, R6  | No Funcional |

Enlace a documento de [Casos de uso](https://github.com/tomgreef/SRS-Template/blob/master/CasosDeUso.pdf).

### 4.2 Calidad de Servicio

#### 4.2.1 Rendimiento
**R6.1** - El motivo por la cuál se ha optado esas especificaciones es para reducir el tamaño que ocupa cada incidencia en la base de datos, y a su vez optar por un formato específico de imágenes.

**R6.2** - Ayudará con el diseño del sistema, ya que sabiendo que habrá un límite al texto podremos definir un tamaño perfecto para cada sección.

**R17.1** - Reducirá el número de información que pide del base de datos.

**R21** - Reducirá el tamaño del base de datos.

#### 4.2.2 Seguridad
**R4.1** - Haremos que el sistema cumpla con las regulaciones sobre la ley de la protección de datos.

**R4.2** - Verificará que el nuevo Usuario verdaderamente es una persona y no un bot.

**R5.1** - Prevendrá de que alguien no autorizado consiga usar una cuenta que se haya olvidado de salir de la sesión antes de irse.

**R22** - Todo los datos que pasan desde el lado del usuario/agente hasta el sistema estarán encriptado.

**R23** - Esto nos permitirá que el acceso al base de datos no esté abierto más tiempo de lo necesario.

#### 4.2.3 Disponibilidad
**R2** - Los agentes siempre podrán seguir trabajando de forma limitado con las incidencias gracias al caché que almacenará un número limitado de incidencias abiertas, para que puedan ser resueltos y enviados al sistema una vez se haya restaurado la conexión al internet.

### 4.3 Diseño e implementación

#### 4.3.1 Reusabilidad
Para la implementación del sistema, se hará uso del servicio que ofrece Google, llamado [Firebase](https://firebase.google.com/).

#### 4.3.2 Fecha de entrega
El producto deberá ser entregado a fecha de **5 de Junio, de 2020**.

## 5. Verificación
Para verificar todos los requisitos mencionados en este documento haremos uso de [JUnit 5](https://junit.org/junit5/) que nos servirá para realizar todo el testeo necesario para la aplicación de escritorio del agente.

Luego, para verificar los demás, simplemente bastará con la visualización de los acontecimientos usado el sistema en vivo. Para ello, designamos dos personas que opten por todas las opciones disponibles para ver si se produce algo fuera de lo escrito en este documento.


## 6. Apendices

### Apéndice A: Ejemplos de este documento relleno

[Ejemplo relleno en inglés](http://www.cse.chalmers.se/~feldt/courses/reqeng/examples/srs_example_2010_group2.pdf)
[Ejemplo relleno en español](https://sites.google.com/site/ingesoftuao/definicion-proyecto)

### Apéndice B: Generar PDF usando un fichero MD

[Dillinger](https://dillinger.io/)

### Apéndice C: Crear una tabla para un fichero MD

[Tables Generato](https://www.tablesgenerator.com/markdown_tables#)

### Apéndice D: Crear interfaces simples

[Balsamiq](https://balsamiq.com/wireframes/)