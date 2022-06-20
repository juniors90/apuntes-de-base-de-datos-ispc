Introducción a los sistema de administración de bases de datos.
===============================================================

Introducción
------------

Durante las últimas cuatro décadas del siglo veinte, el uso de las bases de datos creció en todas las empresas. En los primeros días, muy pocas personas interactuaban directamente con los sistemas de bases de datos, aunque sin darse cuenta interactuaban indirectamente con bases de datos (con informes impresos como los extractos de las tarjetas de crédito, o mediante agentes como los cajeros de los bancos y los agentes de reservas de las líneas aéreas). Después llegaron los cajeros automáticos y permitieron a los usuarios interactuar directamente con las bases de datos. Pero a partir de la revolución de Internet a finales de los años noventa aumentó significativamente el acceso directo del usuario a las bases de datos.

Una base de datos (DB, en inglés Data Base) es una colección de datos relacionados. Con la palabra datos nos referimos a los hechos conocidos que se pueden grabar y que tienen un significado implícito. Por ejemplo, los nombres, números de teléfono y direcciones de las personas que conoce. Puede tener todos estos datos grabados en un libro de direcciones indexado o los puede tener almacenados en el disco duro de un computador. Esta colección de datos con un significado implícito es una base de datos.

Una base de datos tiene las siguientes propiedades implícitas:

- Una base de datos representa algún aspecto del mundo real, lo que en ocasiones se denomina mini-mundo o universo de discurso. Los cambios introducidos en el mini-mundo se reflejan en la base de datos.

- Una base de datos es una colección de datos lógicamente coherente con algún tipo de significado inherente. No es correcto denominar base de datos a un surtido aleatorio de datos.

- Una base de datos se diseña, construye y rellena con datos para un propósito específico. Dispone de un grupo pretendido de usuarios y algunas aplicaciones preconcebidas en las que esos usuarios están interesados.

En otras palabras, una base de datos tiene algún origen del que se derivan los datos, algún grado de interacción con eventos del mundo real y un público que está activamente interesado en su contenido.

Con el objetivo de que una base de datos sea en todo momento precisa y fiable, debe ser un reflejo exacto del mini-mundo que representa; por consiguiente, en la base de datos deben reflejarse los cambios tan pronto como sea posible.

Una base de datos puede ser de cualquier tamaño y complejidad.

Una base de datos se puede generar y mantener manualmente o estar automatizada.


Sistemas de Gestión de Bases de Datos (DBMS)
Concepto
Una base de datos, por sí misma, no es más que una forma de almacenamiento de datos; por lo tanto, para poder acceder a dichos datos existe un conjunto de programas que facilitan la interacción con dichos datos.

El objetivo principal de este conjunto de programas denominado: Sistema de Administración de Base de Datos (DBMS, en inglés DataBase Management System) es proporcionar una forma de almacenar y recuperar la información de una base de datos de manera que sea práctica y eficiente.

Estos sistemas de administración de DB están diseñados para gestionar grandes cantidades de información. La gestión de los datos implica tanto la definición de estructuras para almacenar la información como la provisión de mecanismos para la manipulación de la información. Además, los sistemas de administración de bases de datos deben garantizar la fiabilidad de la información almacenada, a pesar de las caídas del sistema o de los intentos de acceso no autorizados. Si los datos van a ser compartidos entre diferentes usuarios, el sistema debe evitar posibles resultados anómalos.

Podemos definir un sistema de administración de datos como una colección de programas que permite a los usuarios crear y mantener una base de datos. El DBMS es un sistema de software de propósito general que facilita los procesos de definición, construcción, manipulación y compartición de bases de datos entre varios usuarios y aplicaciones. Definir una base de datos implica especificar los tipos de datos, estructuras y restricciones de los datos que se almacenarán en la misma.

Propósito de los DBMS
Las bases de datos y los sistemas de administración de bases de datos surgieron en respuesta a los primeros métodos de gestión informatizada de los datos comerciales. A modo de ejemplo de dichos métodos, típicos de los años sesenta, considérese parte de una entidad bancaria que, entre otros datos, guarda información sobre todos los clientes y todas las cuentas de ahorro. Una manera de guardar la información en la computadora es almacenarla en archivos del sistema operativo. Para permitir que los usuarios manipulen la información, el sistema tiene varios programas de aplicación que gestionan los archivos, incluyendo programas para:

- Efectuar cargos o abonos en las cuentas.

- Añadir cuentas nuevas.

- Calcular el saldo de las cuentas.

- Generar los extractos mensuales.

Estos programas de aplicación los han escrito programadores de sistemas en respuesta a las necesidades del banco.

Se añaden nuevos módulos al sistema según surgen las necesidades. Por ejemplo, supóngase que un banco decide ofrecer además de caja de ahorro, cuentas corrientes. En consecuencia, se crean nuevos archivos permanentes que contienen información acerca de todas las cuentas corrientes abiertas en el banco y puede que haya que escribir nuevos programas de aplicación para afrontar situaciones que no se dan en las cajas de ahorro, como los descubiertos. Así, con el paso del tiempo, se añaden más archivos y programas de aplicación al sistema.

Los sistemas operativos convencionales soportan este sistema de procesamiento de archivos típico. El sistema almacena los registros permanentes en varios archivos y necesita diferentes programas de aplicación para extraer y añadir a los archivos correspondientes. Antes de la aparición de las bases de datos, las organizaciones normalmente almacenaban la información en sistemas de este tipo.

Guardar la información de la organización en un sistema de procesamiento de archivos tiene una serie de inconvenientes importantes:

#. Redundancia e inconsistencia de los datos. Debido a que los archivos y programas de aplicación los crean diferentes programadores en el transcurso de un período de tiempo, es probable que los diversos archivos tengan estructuras diferentes y que los programas estén escritos en varios lenguajes de programación diferentes. Además, puede ser que la información esté duplicada en varios lugares (archivos). Por ejemplo, la dirección y el número de teléfono de un cliente dado pueden aparecer en un archivo que contenga registros de cuentas de ahorros y en un archivo que contenga registros de cuentas corrientes. Esta redundancia conduce a costos de almacenamiento y de acceso más elevados. Además, puede dar lugar a la inconsistencia de los datos; es decir, puede ser que las diferentes copias de los mismos datos no coincidan. Por ejemplo, es posible que el cambio en la dirección de un cliente esté reflejado en los registros de las cuentas de ahorro, pero no en el resto del sistema.

#. Dificultad en el acceso a los datos. Supóngase que uno de los empleados del banco necesita averiguar los nombres de todos los clientes que viven en domicilio con un mismo código postal. El empleado pide al departamento de procesamiento de datos que genere esa lista. Debido a que esta petición no fue prevista por los diseñadores del sistema original, no hay un programa de aplicación a mano para satisfacerla. Hay, sin embargo, un programa de aplicación que genera la lista de todos los clientes. El empleado del banco tiene ahora dos opciones: obtener la lista de todos los clientes y extraer manualmente la información que necesita, o bien pedir a un programador de sistemas que escriba el programa de aplicación necesario. Ambas alternativas son obviamente insatisfactorias. Supóngase que se escribe el programa y que, varios días más tarde, el mismo empleado necesita reducir esa lista para que incluya únicamente a aquellos clientes que tengan una cuenta con saldo igual o superior a $10.000. Como se puede esperar, no existe ningún programa que genere tal lista. De nuevo, el empleado tiene que elegir entre dos opciones, ninguna de las cuales es satisfactoria. La cuestión aquí es que los entornos de procesamiento de archivos convencionales no permiten recuperar los datos necesarios de una forma práctica y eficiente. Hacen falta sistemas de recuperación de datos más adecuados para el uso general.

#. Aislamiento de datos. Como los datos están dispersos en varios archivos, y los archivos pueden estar en diferentes formatos, es difícil escribir nuevos programas de aplicación para recuperar los datos correspondientes.

#. Problemas de integridad. Los valores de los datos almacenados en la base de datos deben satisfacer ciertos tipos de restricciones de consistencia. Por ejemplo, el saldo de ciertos tipos de cuentas bancarias no puede nunca ser inferior a una cantidad predeterminada (por ejemplo, $25). Los desarrolladores hacen cumplir esas restricciones en el sistema añadiendo el código correspondiente en los diversos programas de aplicación. Sin embargo, cuando se añaden nuevas restricciones, es difícil cambiar los programas para hacer que se cumplan. El problema se complica cuando las restricciones implican diferentes elementos de datos de diferentes archivos.

#. Problemas de atomicidad. Los sistemas informáticos, como cualquier otro dispositivo mecánico o eléctrico, está sujeto a fallos. En muchas aplicaciones es crucial asegurar que, si se produce algún fallo, los datos se restauren al estado consistente que existía antes del fallo. Considérese un programa para transferir $10.000 desde una cuenta A a una Cuenta B. Si se produce un fallo del sistema durante la ejecución del programa, es posible que los $10.000 fueran retirados de la cuenta A, pero no acreditados en la cuenta B, dando lugar a un estado inconsistente de la base de datos. Evidentemente, resulta esencial para la consistencia de la base de datos que tengan lugar tanto el débito (descuento del saldo de la cuenta A) como el crédito (cargo en la Cuenta B), o que no tenga lugar ninguno. Es decir, la transferencia de fondos debe ser atómica—debe ocurrir en su totalidad o no ocurrir en absoluto. Resulta difícil asegurar la atomicidad en los sistemas convencionales de procesamiento de archivos.

#. Anomalías en el acceso concurrente. Para aumentar el rendimiento global del sistema y obtener una respuesta más rápida, muchos sistemas permiten que varios usuarios actualicen los datos simultáneamente. En realidad, hoy en día, los principales sitios de comercio electrónico de Internet pueden tener millones de accesos diarios de compradores a sus datos. En tales entornos es posible la interacción de actualizaciones concurrentes y puede dar lugar a datos inconsistentes. Considérese una cuenta bancaria A, que contenga $5000. Si dos clientes retiran fondos (por ejemplo, $500 y $1000, respectivamente) de la cuenta A aproximadamente al mismo tiempo, el resultado de las ejecuciones concurrentes puede dejar la cuenta en un estado incorrecto (o inconsistente). Supóngase que los programas que se ejecutan para cada retiro de dinero leen el saldo anterior, reducen su valor en el importe que se retira y luego escriben el resultado. Si los dos programas se ejecutan concurrentemente, pueden leer el valor $500, y escribir después $4500 y $4000, respectivamente. Dependiendo de cuál escriba el valor en último lugar, la cuenta puede contener $4500 o $4000, en lugar del valor correcto, $3500. Para protegerse contra esta posibilidad, el sistema debe mantener alguna forma de supervisión. Pero es difícil ofrecer supervisión, ya que muchos programas de aplicación diferentes que no se han coordinado con anterioridad pueden tener acceso a los datos.

#. Problemas de seguridad. No todos los usuarios de un sistema de bases de datos deben poder acceder a todos los datos. Por ejemplo, en un sistema bancario, el personal de nóminas (Empleados de la empresa), sólo necesita ver la parte de la base de datos que contiene información acerca de los diferentes empleados del banco. No necesitan tener acceso a la información acerca de las cuentas de clientes. Pero, como los programas de aplicación se añaden al sistema de procesamiento de datos a medida que se requieren, es difícil hacer cumplir tales restricciones de seguridad.

Estas dificultades, entre otras, motivaron el desarrollo de las bases de datos y los sistemas de administración de las mismas.

Funciones de los DBMS
- Metadatos: es la definición o información descriptiva de una base de datos, relacionada con su estructura y los datos que contiene, también se almacena, en forma de catálogo o diccionario de la base de datos.

- Construcción de la base de datos: es el proceso consistente en almacenar los datos en algún medio de almacenamiento controlado por el DBMS.

- Manipulación de una base de datos: son aquellas funciones como la consulta de la base de datos para recuperar datos específicos, actualizar la base de datos para reflejar los cambios introducidos en el mini-mundo y generar informes a partir de los datos.

- Compartir una base de datos: permite que varios usuarios y programas accedan a la base de datos de forma simultánea.

- Consultas: una aplicación accede a la base de datos enviando consultas o solicitudes de datos al DBMS. Una consulta normalmente provoca la recuperación de algunos datos.

- Transacciones: una transacción puede provocar la lectura o la escritura de algunos datos en la base de datos.

- Protección: incluye la protección del sistema contra el funcionamiento defectuoso del hardware o el software y la protección de la seguridad contra el acceso no autorizado o malintencionado.

- Mantenimiento: una gran base de datos típica puede tener un ciclo de vida de muchos años, por lo que el DBMS debe ser capaz de mantener el sistema de bases de datos permitiendo que el sistema evolucione según cambian los requisitos con el tiempo.

Tecnología de Base de Datos vs. Tecnología Tradicional
Unas cuantas características distinguen la tecnología de bases de datos de la tecnología tradicional de programación con archivos.

Procesamiento tradicional de archivos
Base de Datos
- Cada usuario define e implementa los archivos necesarios para una aplicación concreta como parte de la programación de esa aplicación.

- Cada aplicación tiene libertad para asignar un nombre independientemente a los elementos de datos.

- Se mantiene un único almacén de datos, que se define una sola vez, y al que acceden varios usuarios.

- Los nombres o etiquetas de los datos se definen una vez, y son utilizados para consultas, transacciones y aplicaciones.

 

Las principales características de las bases son las siguientes:

Naturaleza auto descriptiva de un sistema de bases de datos.
Una característica fundamental de la tecnología de bases de datos es que el sistema de bases de datos no sólo contiene la propia base de datos, sino también una completa definición o descripción de la estructura de la base de datos y sus restricciones. Esta definición se almacena en el catálogo DBMS, que contiene información como la estructura de cada archivo, el tipo y el formato de almacenamiento de cada elemento de datos, y distintas restricciones de los datos. La información almacenada en el catálogo se denomina, como vimos anteriormente: metadatos y describe la estructura de la base de datos principal. El software DBMS y los usuarios de la base de datos utilizan el catálogo cuando necesitan información sobre la estructura de la base de datos. Un paquete de software DBMS de propósito general no se escribe para una aplicación de base de datos específica. Por consiguiente, debe referirse al catálogo para conocer la estructura de los archivos de una base de datos específica, como el tipo y el formato de los datos a los que accederá. El software DBMS debe funcionar igual de bien con cualquier cantidad de aplicaciones de bases de datos (por ejemplo, la base de datos de una universidad, la base de datos de un banco o la base de datos de una empresa), siempre y cuando la definición de la base de datos esté almacenada en el catálogo.

Aislamiento entre programas y datos, y abstracción de datos.
En el procesamiento de archivos tradicional, la estructura de los archivos de datos está incrustada en las aplicaciones, por lo que los cambios que se introducen en la estructura de un archivo pueden obligar a realizar cambios en todos los programas que acceden a ese archivo. Por el contrario, los programas que acceden a un DBMS no necesitan esos cambios en la mayoría de los casos. La estructura de los archivos de datos se almacena en el catálogo DBMS, independientemente de los programas de acceso. Llamaremos a esta propiedad independencia programa-datos.

Soporte de varias vistas de los datos.
Normalmente una base de datos tiene muchos usuarios, cada uno de los cuales puede necesitar una perspectiva o vista diferente de la base de datos. Una vista puede ser un subconjunto de la base de datos o puede contener datos virtuales derivados de los archivos de la base de datos pero que no están explícitamente almacenados.

Algunos usuarios no tienen la necesidad de preocuparse por si los datos a los que se refieren están almacenados o son derivados. Un DBMS multiusuario cuyos usuarios tienen variedad de diferentes aplicaciones debe ofrecer facilidades para definir varias vistas.

Compartición de datos y procesamiento de transacciones multiusuario.
Un DBMS multiusuario, como su nombre indica, debe permitir que varios usuarios puedan acceder a la base de datos al mismo tiempo. Esto es esencial, si los datos destinados a varias aplicaciones serán integrados y mantenidos en una sola base de datos. El DBMS debe incluir software de control de la concurrencia para que esos varios usuarios que intentan actualizar los mismos datos, en el mismo momento, lo hagan de un modo controlado para que el resultado de la actualización sea correcto. Por ejemplo, si varios agentes de viajes intentan reservar un asiento en un vuelo, el DBMS debe garantizar que en cada momento sólo un agente tiene acceso a la asignación de ese asiento para un pasajero. Estos tipos de aplicaciones se denominan, por lo general, aplicaciones de procesamiento de transacciones en línea (OLTP, online transaction processing). Un papel fundamental del software DBMS multiusuario es garantizar que las transacciones concurrentes operan correcta y eficazmente.

El concepto de transacción es cada vez más importante para las aplicaciones de bases de datos. Una transacción es un programa en ejecución o proceso que incluye uno o más accesos a la base de datos, como la lectura o la actualización de los registros de la misma. Se supone que una transacción ejecuta un acceso lógicamente correcto a la base de datos si lo ejecutó íntegramente sin interferencia de otras transacciones. El DBMS debe implementar varias propiedades de transacción. La propiedad aislamiento garantiza que parezca que cada transacción se ejecuta de forma aislada de otras transacciones, aunque puedan estar ejecutándose cientos de transacciones al mismo tiempo. La propiedad de atomicidad garantiza que se ejecuten o todas o ninguna de las operaciones de bases de datos de una transacción.

