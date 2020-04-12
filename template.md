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
Describa las características de cada interfaz entre el producto de software y los componentes de hardware del sistema. Esto puede incluir los tipos de dispositivos que deben ser compatibles, la naturaleza de los datos y las interacciones de control entre el software y el hardware, y los protocolos de comunicación que se utilizarán.

#### 3.3 Interfaces con el Software
Describa las conexiones entre este producto y otros componentes de software específicos (nombre y versión), incluidas bases de datos, sistemas operativos, herramientas, bibliotecas y componentes comerciales integrados. Identifique los elementos de datos o mensajes que entran y salen del sistema y describa el propósito de cada uno. Describa los servicios necesarios y la naturaleza de las comunicaciones. Consulte los documentos que describen los protocolos detallados de la interfaz de programación de aplicaciones. Identifique los datos que se compartirán entre los componentes de software. Si el mecanismo de intercambio de datos debe implementarse de una manera específica (por ejemplo, memoria compartida, ficheros, en la nube, etc), especifique esto como una restricción de implementación.


## 4. Requisitos
Esta sección especifica los requisitos del producto a nivel de sistema y desglosa estos en diferentes categorías. El conjunto de requisitos se debe validar y estos deben ser:
* Vigentes: Los requisitos reflejan las necesidades actuales de los usuarios del sistema, estos han podido cambiar con el tiempo, por tanto se debe revisar que sigen estando vigentes.
* Consistentes: Los requisitos no deben tener conflicto entre ellos. De tenerlo se puede establecer prioridades (obligatorio, deseable o opcional sería una opción).
* Completos: El conjunto de los requisitos define todas las funciones y restricciones deseadas por los stakeholders.
* Viables: Los requisitos pueden ser implementados dentro del presupuesto y tiempo planeado.
* Verificables: Los requisitos pueden ser comprobables (verificables) mediante tests.

Para cada requisito se debería especificar, su ID, nombre del requisito, descripción del requisito, dependencias, prioridad y justificación de su espeficación (stakeholder, derivado de un caso de uso, una interfaz necesaria, etc). Un estilo formateado facilitará la lectura. Podéis usar el siguiente formato(dependiendo de la sección se añadiran más o menos almohadillas para ponerlo en su subsección correspondiente):

### ID - Nombre del requisito
Descripción
#### Dependencias 
#### Priodidad
#### Justificación

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
