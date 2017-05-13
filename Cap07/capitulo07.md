# **1.7 PAPEL DE LA UC Y DE LOS MHz DEL RELOJ EN LA EJECUCION DE LAS INSTRUCCIONES**
### **�C�mo se ejecutan las instrucciones I^1 a I^4 mediante movimientos simples entre memoria y registros de la UCP ordenados por la UC ?**

---

*Con el fin de comprender mejor como opera la UC, veremos m�s en detalle la forma en que se ejecutan las instrucciones*, a partir del esquema de la figura 1.8, con el agregado de los registros de direcciones (RDI) y de datos (RDA), definidos en la secci�n 1.4 al tratar el acceso al azar.
Como se vio en relaci�n con la figura 1.15 cada **sentencia** (orden) de un programa de alto nivel (como R=P+P-T) es traducida por un programa compilador en una secuencia de **instrucciones** (�rdenes mas simples, en nuestro ejemplo **I^1,I^2,I^3 e I^4**) que una UC puede ejecutar.

**A su vez**, la ejecuci�n de cada instrucci�n se divide en pasos a�n m�s simples (4 en nuestro caso, figs 1.23 a 1.25). Las acciones que debe ordenar controlar la UC en cada uno de estos 4 pasos est�n determinadas por 4 combinaciones binarias llamadas **"microc�digos"** que van apareciendo una tras otra en las **l�neas de control** con cada uno de los pulsos que constituyen los Mhz (figuras l.29 y 1.30). 
Estas l�neas salen de la UC hacia la UAL, los registros y la memoria (fig. 1.31). La ejecuci�n de una instrucci�n implica una secuencia de movimientos de transferencia de bytes entre memoria principal y registros de la UCP (o entre estos �ltimos), establecidos por la UC en un orden determinado, seg�n el c�digo de dicha instrucci�n. Tambi�n puede ordenarse una operaci�n en la UAL.|
:-|


*Cada segundo* puede ejecutarse algunos millones de instrucciones, para lo cual deben sucederse muchos *millones* de estos movimientos de pasaje de direcciones, c�digos, datos y resultados, *al ritmo de millones de impulsos el�ctricos por segundo* (**"megahertz"**, abreviados **MHz**) que le llegan a la UC, generados regularmente por un cristal piezo-el�ctrico de cuarzo o **"reloj"** ("*clock*"). 
As� se habla de microprocesadores (con reloj) de 100 MHz, 1 GHz, etc. En principio, a mayor n�mero de MHz podr�n suceder m�s de estos movimientos por segundo, con lo cual se podr�n ejecutar mas instrucciones por segundo. Un Pentium actual de 1 GHz puede ejecutar m�s de mil millones de instrucciones por segundo (1000 MIPS), y en ciertos casos hasta 3000 MIPS.
Describiremos *en un modelo simplificado*, el orden, origen y destino de estos movimientos, que deben llevarse a cabo durante la ejecuci�n de una instrucci�n, para I^1,I^2,I^3 e I^4, y los agruparemos por etapas Dichos movimientos el Debug no los puede mostrar, como tampoco muestra los registros RI, RDI y RDA.


Asi se comprender� que la UC tiene como funci�n primera dar �rdenes de operaciones de lectura o escritura a la memoria y registros de la UCP, y ordenar qu� operaci�n debe hacer la UAL, o sea **controlar**, *en el sentido de dar �rdenes*, a esos dispositivos. De ah� su nombre de "unidad de control".|
:-|


A fin de hacer m�s simple la explicaci�n, supondremos que cuando la UC ordena leer la zona de instrucciones de memoria �a la cual apunta el valor de IP�*pide 4 bytes Consecutivos de c�digo de instrucci�n[^2]*. Para ello, si por ejemplo es IP = 0200, asumiremos que primero pide leer 0200 y 0201, y luego 0202 y 0203[^3]. Los contenidos de estas posiciones llegan al **registro de instrucci�n RI** (figura 1.23).
Para leer dos (o m�s) direcciones consecutivas basta dar el n�mero correspondiente a la primera de ellas. 
Durante la obtenci�n y ejecuci�n de una instrucci�n, ocurren en definitiva las siguientes acciones y movimientos principales (figuras 1.23 a 1.26), con los objetivos que se indican, *que como se ver� son comunes en general a todas las instrucciones*. Para las operaciones de lectura de la memoria principal (MP), dene tener presente el esquema de la figura 1.10. Comenzaremos con *I^1* (figura 1.23).

---
[^1] En Electricidad, si un fen�meno sucede X veces por segundo se dice que tiene una frecuencia de repetici�n de X Hertz (hercios),en honor a Hertz, descubridor de las ondas electromagn�ticas. Un Hertz (Hz) es un ciclo por segundo; 1000 Hz son un kilohertz(Khz), 1000000 I-Iz son un megahertz(Mhz).
[^2] En los microprocesadores actuales, para ganar tiempo, mientras se est�n ejecutando instrucciones pedidas anteriormente, se van leyendo de MP c�digos de instrucciones a ser ejecutados localizados en posiciones consecutivas. Las Instrucciones pedidas con anticipaci�n se guardan en una memoria interna del microprocesador. Esto se describe en la secci�n 1.14.
[^3] O sea estarnos suponiendo un microprocesador como el 80286 que opera con un word de 16 bits.


**1. Movimientos para direccionar y obtener el c�digo de la instrucci�n en el registro RI (Igualmente para cualquier instruccion)**

 *a.> La UC pne en **1** la l�nea L/E (lectura), y ordena enviar al registro RDI una copia de la direcci�n 0200 H= 0000 0010 0000 0000 que indica el IP. De este modo dicho n�mero, de 16 bits, llegar� a trav�s de 16 l�neas de direccion del bus (una l�nea para cada bit).
 *b.> La MP env�a juntos los contenidos de la posici�n direccionada y de la siguiente (0200 y 0201), o sea en caso el n�mero Al 00, que en binario ser�a 10100001 00000000. Estos 16 bits van por las 16 lineas de datos del bus, hacia el registro RDA[^1], y de �ste al RI, Luego siguen la misma ruta los contenidos 50 y 03 de las direcciones 0202 y 0203, como se plante� m�s arriba. . En consecuencia, al cabo de estos movimientos, en RI existir� en binario la combinacion que en hexa A100503, que corresponde al c�digo de m�quina a la instrucci�n pedida (**I^1**,en este caso).

![imagen1](/Figura 1.23.jpg) ![imagen2](/Figura 1.24.jpg)

---
[^1] Es importante notar * **que en una lectura de MP,los datos de las posiciones le�das permanecen intactos, y una copia de los mismos reemplaza alos que exist�an en el registro de destino, los cuales se pierden.** *
**O sea que una lectura de MP implica una escritura en un registro de la UCP.**
Esto es semejante en un calculador se pulsa la tecla RM, y una copia de lo que est� memorizado pasa al visor, perdi�ndose el n�mero que �ste conten�a anteriormente.


**2. Decodificaci�n** (Determina los pr�ximos movimientos a realizar por la UC para ejecutar la instrucci�n que est� en RI y *ocurre para todas las instrucciones*).
: Cuando un c�digo de m�quina (en este caso A1005003) llega al registro RI, el c�dgio de operaci�n (en este caso **A1**) es **"decodificado"**[^1] por la UC. Esto es, el c�digo es detectado por circuitos de la UC, y *su combinaci�n particular de unos y ceros desencadena una secuencia de acciones que ya han sido separadas para esa combinaci�n cuando se dise�o el precesador, a saber:*

**3. Movimientos para direccionar y leer un operando** (dato a operar), **cuyo destino es el registro RDA** (fig 1.24) 
: **a.** La UC pone **1** la l�nea L/E (lectura), y ordena enviar al registro RDI una copia de la direcci�n formada por los dos bytes del c�digo de m�quina que siguen al c�digo de operaci�n (en este caso 0050),pero traspuestos (o sea 5000), con lo cual dicho n�mero llega a MP a trav�s de las l�neas de direcci�n del bus.
: **b.** La MP env�a juntos los contenidos de la posici�n direccionada y de la siguiente (5000 y 5001), o sea en este caso el dato 1020H. Los 16 bits del mismo llegan por las l�neas de datos del registro RDA.

**4. Movimientos y acciones para cumplimentar la operaci�n que ordena la instrucci�n: I1** ordena transferir desde MP hacia AX un dato. Puesto que �ste ya se encuentra en RDA, solo resta el movimiento de pasar dicho dato del RDA al registro AX (figura 1.24), donde queda almacenado. De esta forma se ha ejecutado lo ordenado por **I^1**.

**5. Movimientos y acciones para que IP contenga la direcci�n de la pr�xima instrucci�n a ejecutar:** 
: En la UAL se debe sumar al contenido del registro IP, la cantidad de bytes que ocupa la instrucci�n ejecutada (en este caso 3), y reemplazar el valor anterior (0200) por el resultado de la suma (0203)[^1].

La ejecuci�n de **I^2** (que ordena sumar al registro AX el dato que est� en 5000H) empieza con los pasos **1a.** y **1b.** de la figura 1.23 (iguales para *todas* las instrucciones). En **1a.** ser� 0203 la direcci�n que apunta IP; y en **1b.** al registro RI llegara 0306 0050 que es el c�digo de **I^2**. Adem�s, **I^2** tiene en com�n con **I^1** el movimiento **3a.** y la direcci�n en este caso es tambi�n 5000H. En el movimiento **3b.** (figura1.25) el dato (en este ejemplo otra vez 1020H) obtenido de la lecutra de la direcci�n 5000H llega al registro RDA.
La operaci�n ordenada en el paso **4** ahora es sumar el operando (1020H) -que est� en RDA- al dato contenido en AX (1020H). El resultado de la suma (2040H) debe guardarse en AX reemplazando el valor anterior 1020H, que se pierde (igual que una calculadora cuando se suma). 
El paso **5** consistir� en cambiar el valor de IP, de modo que apunte a la direcci�n **I^3**, para lo cual la UC debe sumar 4 (pues **I^2** ocupa 4 posiciones de memoria) al valor 0203, de forma que IP indique 0207H.

**I^3** se ejecuta con los mismos movimientos que **I^2** con la �nica diferencia que la UC ordena la resta a la UAL[^2].
Puede verificarse que mediante ellos se llega a los resultados hallados con el Debug (figura 1.21). 
Para la instrucci�n **I^4** (que ordena guardar en 5010H el contenido de AX), luego del movimiento **1b.** (figura 1.23) se tendr� en RI su c�digo A31050.
En el movimiento **3a.** -como en **I^1**- se ordena enviar al registro RDI una copia de la direcci�n formada por los dos bytes del c�digo de m�quina que siguen al c�digo de operaci�n (en este caso 1050), pero traspuestos (o sea 5010H), con lo cual dicho n�mero llega a MP a trav�s de las 16 l�neas de direcci�n del bus. (fig 1.26).
En el paso **3b.** el dato (0000H) que se debe enviar a MP para cumplimentar la operaci�n, pasar� al RDA. 
Puesto que la operaci�n ordenada en esencia es una escritura de memoria, el paso **4.** consiste simplemente en que la UC pone 0 la l�nea L/E (escritura). con lo cual enviar� hacia MP, por las l�neas de datos, una copia del contenido de RDA (en este caso 0000H). Este se escribir� en las posiciones 5010 y 5011[^3]. En el paso **5** el IP se actualiza en 020E (no dibujado).
---
[^1]Esta acci�n circuital no es visualizable en la figura 1.23. Supondremos que cuando la UC lee el primer byte del c�digo (**A1**) de una instrucci�n detecta cuantos bytes la componen y qu� representa cada uno. Por lo tanto la UC as� "sabe" que 03 no forma parte del c�digo de la instrucci�n. Recordar que �sta ordenaba enviar hacia AX una copia del n�mero contenido en la direcci�n 5000 (y en la 5001)
[^2] En los pasos 3b de las instrucciones **I^2** e **I^3** tiene lugar una lectura de memoria seguida de una operaci�n aritm�tica.
[^3]En general, *en una operaci�n de escritura en MP (o en cualquier registro), se destruye el contenido que ten�a antes la posici�n escrita, la cual pasa a almacenar el nuevo valor escrito. Los datos le�dos en el registro de origen, cuya copia fue escrita en MP (destino), permanecen intactos.* Asimismo, *una escritura de MP supone una lectura de un registro de la UCP.*|
:-|

![imagen1](/Figura 1.25.png) ![imagen2](/Figura 1.26.png)


## **�Qu� secuencia de pasos ordena la UC para ejecutar cada instrucci�n?**
---
Si recapitulamos (figuras 1.23 a 1.26) c�mo se ejecutaron las instrucciones en el esquema de UC	supuesto, resulta que la estructura de la UCP est� pensada para que repita *permanentemente* la siguiente secuencia de pasos, con las intruciciones del programa a ejecutar que est� en memoria principal (MP):

**1. Obtener** (direccionar) **la instrucci�n a ejecutar de la memoria principal[^1]:**
>El IP indica la direci�n de MP donde comienza el c�digo de m�quina[^2] de la instrucci�n a ejecutar, el caul luego de ser le�do de MP llega al registro RI.

**2. Decodificar:** 
>El c�digo de operaci�n indica: la operacion a realizar, c�mo encontrar un dato a operar, y la cantidad de bytes que tiene la instrucci�n, para que la UC lleven a cabo la secuencia de movimientos preparada para ejecutar dicho co�digo.
---
1 En ingl�s **"fetch"**
2 Por ejemplo en la instrccion **I^1** el *c�digo de m�quina* era **A10050** (3 bytes), siendo su *c�digo de operaci�n* **A1**, y los 2 bytes restantes **0050** permiten formar la direcci�n 5000 donde est� el dato a operar. **I^2** es una instrucci�n cuyo c�digo de m�quina es de 4 butes, y su c�digo de operaci�n es de 2 bytes. En general los bytes que siguen al c�digo de operaci�n permiten determinar la direcci�n de MP o el registro d�nde est� el dato a operar, o d�nde escribir un resultado.


**3. Obtener un dato a operar:**
>3a	Si el dato est� en MP, con una direcci�n que resulta del c�digo de m�quina de 
La instrucci�n, se direcciona la MP para obtener un dato a operar (�operando�).
>3b	Dicho dato llega al registro RDA (lo mismo en una escritura en MP)
**4. Realizar la operaci�n ordenada y almacenar el resultado:**
Seg�n lo ordenado, puede tener lugar una operaci�n en la UAL y almacenar el resultado en un registro, o consistir la operaci�n en un simple movimiento de un registro a otro, donde queda guardado un dato.
**5. Cambiar el contenido del registro IP, para que tome la direcci�n de la pr�xima instrucci�n a ejecutar, y vuelta al paso 1.** (El cambio del contenido de IP puede hacerse junto con el paso 3.)
Las etapas o pasos citados �sintetizados en la figura 1.27� describen, al igual que las figuras 1.23 y 1,24, el **ciclo de una instrucci�n**,  que puede dividirse temporalmente en una fase de *obtenci�n de la instrucci�n* seguida de otra fase de ejecuci�n. (Figura 1.27)


![imagen1](/Figura 1.27.jpg)


##**�C�mo hace la UC para no equivocarse con tantos n�meros contenidos en memoria que pueden ser instrucciones, datos o direcciones?**
 
En memoria principal existen almacenadas combinaciones de unos y ceros, n�meros binarios que pueden representar c�digos de instrucciones, datos o direcciones. El procesador "no sabe" con cu�l de estos tipos de informaci�n est� tratando, pero el orden, la secuencia repetitiva que realiza �descripta en la respuesta anterior� ha sido perfectamente planeada para que no existan problemas de interpretaci�n al respecto.
Este orden empieza cuando se enciende un computador, pues lo primero que pide la UCP de la MP es un c�digo de m�quina, el que corresponde a la primera instrucci�n del primer programa a ejecutar'. La direcci�n de dicha instrucci�n est� preestablecida, y pertenece a la porci�n ROM de MP, por lo que al encenderse el equipo el n�mero de dicha direcci�n siempre debe formarse en el IP (y en el registro CS2). Luego se suceden en orden los 4 pasos descriptos en la respuesta de la pregunta anterior. De esta forma, lo primero que recibe la UCP de MP es el c�digo de m�quina de Una instrucci�n, que ir� al RI.
*Por lo tanto, un computador est� pensando que la UCP comience a operar leyendo de MP un n�mero que debe ir al registro de instrucci�n (RI), por lo que dicho n�mero ser� interpretado como un c�digo de una instrucci�n.*|
:-|

Conforme se estableci� antes, luego de decodificar el c�digo de una instrucci�n (paso 2), la UCP est� pen�sada para que forme la direcci�n de MP donde est� un dato a operar. Entonces (paso 3a), lo *siguiente que la UCP lee de MP* (o de un registro de la UCP si el c�digo lo ordena) es *un n�mero que es un dato*
Este dato si bien llega al RDA, no va al RI, como el c�digo de operaci�n, sino hacia .un registro de la UCP (como el AX ejemplificado, o es conducido a la UAL' para ser operado). Tambi�n puede ocurrir que un n�mero se escriba en esa direcci�n de MP (como en la ejecuci�n de **I^4**).
Despu�s de sumar al IP la cantidad de bytes que ten�a la instrucci�n ejecutada, IP contendr� la direcci�n de la pr�xima instrucci�n a ser ejecutada, con lo cual vuelve a empezar otro cielo, leyendo de MP un n�mero que es el c�digo de dicha instrucci�n, y como tal es interpretado dado que va en RI en reemplazo del c�digo anterior, y as� de seguido.
El orden, establecido supone que *las instrucciones, deben estar escritas en posiciones sucesivas de memoria*, y que  datos a operar por dichas instrucciones est�n en otra zona de memoria.
Acorde con estas "reglas de juego", si las instrucciones han sido escritas en posiciones sucesivas de memoria y su c�digo es el correcto, no habr� problemas en lo concerniente a c�mo la m�quina "interpreta" cada combinaci�n binaria que pide de memoria. Esto es as� por que el orden establece que lo primero que llega un c�digo, el cual permite localizar otro n�mero que ser� un dato, y luego nuevamente lo pr�ximo que llega ser� un c�digo, etc.
En caso que la UC decodifique en el R1 un c�digo que no reconoce, est� previsto que la UC pase a ejecutar subrutina, que de ser necesario, por ejemplo haga aparecer en pantalla un aviso de error insalvable.

---
[^1]Como ya se describi�, este programa en la porci�n ROM de MP, dado que el primer programa a ejecutar debe estar siempre en memoria, aunque se apague el equipo, para poder traer del disco los programas del sistema operativo que se pierden en la porci�n RAM de  memoria al apagar el computador. Al ser ejecutado comienza una secuencia de pasos que permiten traer trae del disco a MP otro programa, que cuando es ejecutado a su vez trae del **disco** a MP programas del sistema  operativo.

[^2] En un 80X86, el contenido del registro de segmento CS multiplicado por 16 siempre se suma a IP para formar cualquier direcci�n.

##**�Qu� analog�a did�ctica puede establecerse para visualizar la actividad b�sica de organizar movimientos y operaciones que realiza la UC ?**
---
Si observamos  los movimientos indicados en las figuras 1.23 a 1.26 podernos establecer ciertas similitudes con los que *un sistema de control autom�tico de v�as de trenes* (figura 1.28) realizar�a entre un galp�n con trenes estacionados (simil de memoria), y los andenes de una estaci�n de tren (s�miles de registros de la UCP vinculados por *una* �nica v�a bidireccional (similar al bus de datos), para que cada tren vaya al destino que corresponda, seg�n una cierta planificaci�n establecida.
Desde el centro de control se comandar�a, por ejemplo, que un tren que est� estacionado en un lugar del galp�n, se dirija un and�n, y que luego otro tren estacionado en otro lugar  se dirija a otra and�n. Estos  movimientos tendr�an  correlato en el movimiento **1b** y **3b** de las figuras. 1.23 y 1.24. Tambi�n es factible imaginar un lugar de transformaci�n enganche y desenganche de vagones) para formar nuevos convoyes (s�mil de la UAL), Por ejemplo, un tren que estaba en un and�n ser�a conducido a ese lugar para ser acoplado, total o parcialmente, con otro que viene del galp�n form�ndose un nuevo tren que luego ir�a al and�n de donde parti� el primero de los trenes citados. Algo semejante,  cuando durante la ejecuci�n de un programa procesador de texto se unen los caracteres de dos p�rrafos para formar uno nuevo.

![imagen1](/Figura 1.28.jpg)

La funci�n de la UC de encaminar datos hacia un registro de destino, puede apreciarse en este modelo "ferroviario", en el. cambio de v�a que debe realizarse, para que un tren que viene desde el galp�n de estacionamiento �por la �nica v�a de comunicaci�n con la estaci�n- vaya hacia el and�n de destino.

Dentro del microprocesador de la UC permanentemente- mendiante llaves electr�nicas (transistores) quecomanda � est� abriendo y cerrando caminos electr�nicos (buses) internos', para habilitar en cada movimiento previsto el camino que permita *encaminar* datos del registro de origen   al registro de destino, deshabilitando los restantes caminos. Como se describir�, el control de estos movimientos lo realiza la UC mediante l�neas que salen de ella hacia los buses internos, registros y memoria (cable de lectura/escritura), al ritmo de los pulsos que genera el "clock�.|
:-|

Esta analog�a tambi�n permite visualizar que el bus que comunica, memoria con el microprocesador s�lo permite un env�o por vez, en un sentido u otro. Tambi�n la v�a principal de la figura 1.28. s�lo permite que circule por ella un solo tren por vez, sea de un  and�n a un lugar de la playa o en sentido inverso. 
Este modelo que pone de relieve la funci�n de la UC de abrir y cerrar caminos el�ctricos mediante l�neas de control que salen de ella, puede tambi�n servir para aclarar ciertas asociaciones err�neas en torno a la palabra "control" que caracteriza a la UC�.	

--------------
[^1]      En Ingl�s *�data parths�*
[^2]      Si bien la semejanza realizada vale en cuanto a las movimientos ordenados, es importante notar una diferencia sustancial en
relaci�n con los procesos de datos, Seg�n se vio, por ejemplo si se lee la memoria, una *copia* del dato direccionado es la que llega al registro de destino. A diferencia, un tren "desaparece" del lugar donde estaba estacionado cuando va hacia alg�n destino.
                    

---

En primer lugar, en las figuras citadas resulta que **ni datos ni instrucciones entran a la UC,** sino que van a registros, encarg�ndose la UC de que ello ocurra habilitando en cada caso los caminos correspondientes. 
La UC no encarga de controlar si un dato lleg� correctamente, sin bits cerrados, a la UCP, o si un resultado de la UAL es correcto' o no, dado que los datos no Van a la UC. 
Sino directamente a registros asociados a la UAL. Lo  mismo pasa con la materia prima en la figura 1.3. 
As� mismo, cuando un c�digo de instrucci�n llega al registro RI, la UC determina qu� ordena ella, para poner en marcha los movimientos preparados para ejecutarla.
S�lo si el c�digo no corresponde a ninguna instrucci�n, se interrumpe la ejecuci�n del programa en curso y se pasa a ejecutar una subrutina preparada para tal eventualidad. 
Del mismo modo,en el modelo "ferroviario", la oficina de control de v�as no tiene por objetivo controlar cuantos vagones tiene cada tren que pasa,o la carga que lleva.|
:-|

**�Qu� relaci�n existe entre los movimientos que ocurren durante la ejecuci�n de una instrucci�n y el reloj de sincronismo del procesador?**

---

Anteriormente afirmamos que los movimientos que componen la ejecuci�n de cada instrucci�n se realizan en *sincronismo* con impulsos el�ctricos que se suceden *regularmente* a raz�n de millones de ellos por segundo,generados por un cristal pieza-el�ctrico de cuarzo, denominado *"clock"* ("reloj") Profundizaremos m�s este tema, suponiendo que se generan 50 millones de impulsos por segundo.

![Imagen1](/Figura 1.29.jpg)

**50 millones de pulsos por segundo (50 MHz)

**
Si dichos impulsos se visualizan con un instrumento apropiado, como un osciloscopio electr�nico, tienen una forma de onda como indica la figura 1.29. 
Se trata de una se�al el�ctrica que pasa c�clicamente por dos niveles denominados *"bajo"* y *"alto"*, cada uno de una duraci�n fija.
Esto implica que si midi�semos la se�al que sale de dicho cristal oscilador, por ejemplo, durante diez nanosegundos (1/100 de millon�sima de segundo) se tendr�a O volts (nivel bajo), y en los siguientes diez nanosegundos, 5 volts (nivel alto).
Por definici�n, un ciclo tiene lugar cada vez que se repite un mismo fen�meno. En la figura se ha indicado un ciclo del reloj, considerado desde que comienza un nivel bajo, hasta que dicho nivel se inicia de nuevo,con un nivel alto (pulso) en el ciclo. 
O sea que en un ciclo tiene lugar un pulso.

En el ejemplo, un ciclo o pulso se repite 50 millones de veces por segundo, por lo cual se tiene una frecuen-cia de repetici�n de 50 millones de Hertz - 50 Megahertz = 50 **MHz**, siendo 1 Hertz = 1 ciclo por segundo.


**Entonces, *hablar de megahertz es lo mismo o megahercios que  hablar de millones de pulsos por segundos y es lo mismo que de un millones de ciclos por segundos.*

**
Son comunes los microprocesadores con reloj de 100 MHz a m�s de 1 Ghz. El reloj est� incorporado al micro-procesador.
En general, un procesador ser� m�s r�pido si funciona a m�s MHz.


Como se plante�, *estos pulsos marcan, sincronizan, los instantes en que comienzan los movimientos que tienen lugar durante la ejecuci�n de cada instrucci�n*. Vale decir, que un movimiento empieza al comienzo de un pulso y tiene tiempo de consumarse hasta que el inicio del pulso siguiente, cuando comienza otro movimiento.|

:-|


Con un reloj de 50 MHz de reloj, un movimiento debe concretarse durante un ciclo reloj, siendo que �ste dura 1/50 millon�sima de segundo, para el caso que ocurran 50 millones de ciclos por segundo. 
En la fig 1.30 se han  indicado los movimientos que empiezan en consonancia con cada pulso, para las instruc-ciones **I^1 e I^2** antes ejecutadas (ver figs 1.23 y 1.24), suponiendo que con cada pulso tenga lugar un paso de la ejecuci�n de una instrucci�n, y que se requiere 4 pulsos (pasos) para ejecutar cada una de dichas instrucciones.


**Resulta asi que, en general,* una instruci�n requiere para su ejecucion unos pulsos reloj*.**

---

[^1]Al encender un computador la ejecuci�n de un programa de diagn�stico que est� en RDM lleva a cabo una serie de verificaciones en
 el Hardware, en relaci�n con el correcto funcionamiento de la UAL, y la memoria, entre otros, y la configuraci�n  del sistema entre otros.

[^2]La frecuencia de los pulsos reloj no sirve para comparar la performance de
procesadores *distintos*.


###**�De qu� forma la UC pasa de un movimiento a otro abriendo y cerrando caminos?**

En la figura 1.23 se tiene que para leer en memoria el codigo de maquina de una instruccion a ejecutar,en movimiento **la.** una copia del contenido de IP pasaba a RDI. Esto lo ordena la UC mediante una linea control que sale de ella *(figura 1.31) que habilita �por estar en **1**� el camino ("bus") que une IP con RDI.
Los contenidos de memoria llegan al registro RDA pasando por el bus de datos que comunica ambas.
Este movimiento de lectura es ordenado por la UC *mediante su lima de control* L/E (de lectura/ escritura *que va de la UC a memoria*, para lo cual dicha linea de control debia estar en **1** (5 volts).
Una vez que dichos contenidos leidos llegaron al RDA, tendran como destino el registro RI, dado que se trata de un codigo de instruccion. Para ello, la UC *habilitar� mediante otra linea de control* de valor **1**el camino que une RDA con RI. Observese en el esquema propuesto, que las restantes lineas de control que salen de UC por estar en 0 (0 volts), no permiten la transferencia de datos entre otros registros de la UCP, por cortar la comunicaci�n entre los caminos (buses) que los unen.

De manera andloga (figura 1.32), en la lectura del dato a operar, las lineas de control que estan en **1** permiten los movimientos **3a., 3b** y **4**, que aparecen en Ia figura 1.24. Estos movimientos son ordenados por las lineas de control que en la figura 1.32 estan en **1** (que en la figura 1.31 estaban en **0**), las cuales habilitan los correspondientes caminos entre registros.
Tambien salen lineas de control de la UC hacia la UAL, para ordenar sumar, restar u otra operaci�n.
Si el codigo de una instruccion (como el de **I^4**), ordena un movimiento de escritura en memoria, cuando tenga lugar el mismo, un cable de control de la UC habilitara el camino que va de un registro acumulador hacia el registro RDA, y el cable L/E que va a memoria debera estar en 0 volts, para que se escrita la posicion de memoria previamente direccionada, en correspondencia con los movimientos de la figura 1.26.


Por lo tanto, de la UC sale un conjunto de "limas de control" que van 
1. hacia la UAL
2. hacia los caminos entre registros de la UCP
3. hacia la memoria (linea de lectura/escritura -L/E) y hacia los ports de las interfaces (figuras 1.61 y 1.62).
Segun el valor (1 6 0) de estas lineas la UC ordena la operaciOn que hace la UAL, de quo registro a cual otro
se pasara la informaciOn, y si Ia memoria sera leida o escrita.|
:-|

![imagen](/Figura 131.jpg)     

---
*De esta forma se realiza la accion de control de la UC mediante las lineas que salen de ellas, a fin de lograr los movimientos y operaciones necesarios para ejecutar cada paso de una instruccion. Es como un "director de orquesta" que ordena en cada momento que instrumentos deben ponerse en juego.* |
:-|

En la UCP dichos momentos son iniciados, sincronizados, por cada pulso reloj.
Puesto que �como se trat� cada movimiento se lleva a cabo en un pulso reloj, cada uno de las l�neas que salen de la UC pueden cambiar de **0 a 1** � viceversa en cada pulso reloj.
Por ejemplo, si durante un pulso reloj la l�nea que en el movimiento **1b** habilita la escritura de RI desde RDA (figura 1.31), en el pulso siguiente debe inhabilitarla (cambiando de **1 a 0**), para que el dato no vaya a RI, sino a AX, como aparece en la figura 1.32.

> Por consiguiente, * **con cada pulso reloj avanza un movimiento o paso la ejecuci�n de una instrucci�n, y cambia la combinaci�n de unos y ceros presente en las l�neas que salen de la UC**, a fin de que puedan llevarse a cabo dicho movimiento.*|
:-|
---

Cada vez que se repite un determinado movimiento �como el **1a** � el **1b**� se repite tambi�n en las salidas de la UC la combinaci�n de unos y ceros que determina (controla) dichos movimientos


###_**�D�nde reside la "inteligencia" de la UC, para "saber" los movimientos y
operaciones en la UAL a realizar; y c�mo localizarcada microc�digo?**_

Esta pregunta equivale a plantear *de d�nde sale cada combinaci�n de unos y ceros que aparecen con cada pulso reloj en las l�neas de salida de la UC.*

Seg�n se describi� (fig. 1.27) la ejecuci�n de cada instrucci�n se divide en **pasos** a�n m�s simples (4 en nuestro caso, pero que son m�s en instrucciones complejas). Las acciones que debe ordenar/controlar la UC en cada uno de estos 4 pasos est�n determinadas por 4 combinaciones binarias llamadas **"microc�digos" (�cod)** que van apareciendo una tras otra con cada .pulso reloj (Clock =**Ck**) en las **l�neas de control (LC)**. Estas salen de la UC con destino a la UAL, los registros de la UCP, y laa me'Moria (fig. 1.31). Tambi�n van hacia los ports.
Con cada **Ck** el valor (1 � 0) de cada **LC** que sale de la UC determina los movimientos (como ser de **IP** a **RDI**) que deben tener lugar, y si interviene la UAL, qu� operaci�n debe hacer. El valor de cada **LC** puede cambiar con cada **Ck**. As�, para 500 Mhz (500 millones pulsos/seg) las **LC** cambian 500 millones de veces por segundo, o sea que se generan en ellas 500 millones de **�cod/**seg.)
* **Este funcionamiento es com�n a todos los procesadores** *, sean CISC o RISC (secci�n 1.14).|
:-|

> En un CISC las salidas de la UC, o sea las **LC**, son salidas de una ROM denominada ROM de Control[^1](**RC**), que contiene escritas en su interior todas las combinaciones binarias que pueden aparecer en las **LC** para determinar qu� debe hacer la UC en cada paso de la ejecuci�n de una instrucci�n. Ello implica que en la **RC** reside la "inteligencia" de la UC, que obviamente fue originada por quienes crearon la UCP.
En general de la UC salen *n* **LC** (como ser *n*= 100), por lo que cada **�cod** ser� de *n* bits (un bit por cada **LC**), y est� guardado (grabado) en una sola celda de *n* bits de la **RC**. O sea que en la **RC** las celdas no son de 8 bits, sino de *n* bits (figura 1.34).
En la figura 1.31 se supone que durante un cierto Ck los valores de las 7 LC supuestas que salen de la UC son 1000101, y en la fig. 1.32 se asume que con el Ck siguiente dichos valores son 0001011. Ambos valores en la figura 1.33 aparecen guardados en 2 celdas sucesivas de 7 bits de una **RC**. Como en cualquier ROM, cuando se accede a una celda una copia de su contenido (**�cod**) pasa a sus l�neas de salida, que son las **LC** de la UC. Esto sucede con cada **Ck**. 
Con xxxx se indican otros **�cod** en la **RC**, que como todos los **�cod** constan de unos y ceros. 
Cuando el **�cod** 1000101 est� en las **LC** permite realizar los movimientos de la figura 1.31.

![imagen](/Figura 1.33.jpg)

**El esquema siguiente generaliza la fig. 1.33 e intenta acercarse conceptualmente a c�mo se localizan los �cod en una ROM de Control**. Sobre la base de la fig 1.33, y suponiendo que cada una de las instrucciones de la fig 1.15 se ejecute en 4 pasos indicados en la figura 1.30 en concordancia con 4 pulsos, hacen falta **4 �cod** (**�codl, �cod2, �cod3** y **�cod4**) que deber�n aparecer en las **LC** con cada pulso, para indicarle a la UC qu� hacer en cada uno de los 4 pasos de una instrucci�n. Con **Ck1, Ck2, Ck3, Ck4**, designamos a cada uno de los 4 pulsos necesarios para que avance un paso la ejecuci�n de cada instrucci�n, ya sea **I^1, � I^2 , � I^3 � I^4** (fig. 1.15). 
En las celdas de la **RC** de una UCP CISC se guardan los **�cod** para pedir y ejecutar cada instrucci�n de su repertorio.


---
[^1] Tambien llamado **ROM de microcodigo** o **de microinstrucciones**, inmodificable y forma parte del chip del procesador. **Esta ROM no tiene nada que ver con la ROM de la memoria principal**, que contiene los programas de arranque y el BIOS (Basic Input Output System)en una PC, ** ni tampoco tiene que ver con el sistema operativo elegido para un computador**. Esta concepcion circuital se emple� en procesadores y microprocesadores CISC de distintos fabricantes, inclusive hasta el Pentium 1, prevaleciendo luego la concepci�n RISC. 



Puesto que una **RC** es una memoria random -cuyas celdas guardan tantos bits como **LC** existan- *cada celda de* **RC** *se localiza por su direcci�n*.**Cada ucod proveer� la direcci�n del siguiente, salvo la direcci�n del tercer (ucod3)**,que se determina **en la decodificaci�n ** a partir del cod-op del a isntrucci�n que lleg� al **RI**.
Como se tratar�,* dado que en la **RC** existen miles de **ucod** para ejecutar todo el repertorio de instrucciones de una UCP, la localizaci�n de los sucesivos **ucodigos** para ejecutar la instrucci�n que lleg� al RI y luego pedir la siguiente, se realiza sempre a partir de la loccalizaci�n del **ucod3**, merced al cod-op de dicha instrucci�n.* |

:-|

![imagen1](/Figura 1.34.png) 

Supondremos que despu�s de los pulsos **Ck1** y **Ck2**, en las **LC** han aparecido **ucod**1 y luego **ucod**2, con lo cual llega a **RI** (fig. 1.34) en la 2B06; y que en la decodificaci�n decho cod-op 2B06 que esta en RI permite localizar la  direcci�n del 
"**ucod**3 de 2B06" en la **RC**. Osea que cuando llegue Ck los **0s y 1s ** del **ucod**3 del 2B06 al aparecer sobre las **LC** abrir�n y cerrar�n los caminosque corresponda mediante las llaves que los gobiernan, para que  se lleve a cabo el paso 3 de 2B06: direccionar el dato y llavarlo a RDA.

Asimismo, un subconjunto de bits del **ucod**3 de 2B06 no van a las **LC** sino que proveen  la direcci�n del **ucod**4, supuesto en la direcci�n que sigue al a del **ucod**3.

Cuando se genere el pulso **Ck**4, el **ucod**4 de 2B06 aparecer� en las **LC** determinando que se lleve a cabo el paso 4:realizar la resta ordenada por dicho cod-op 2B06.
Asu vez un conjunto de bits del **ucod**4 de 2B06 no van a las **LC**, sino que proveen la direcci�n (Dir ucod1) del **ucod**1 para pedir  de memoria la siguiente instrucci�n (de cod-op supuesto A3). Sial pulso que sigue a **Ck**4 lo volvemos a llamar **Ck**1, al ocurrir este pulso el **ucod**1 aparecer� en las **LC** para que se lleve a cabo el paso 1 del pedido. Del mismo modo, bits del **ucod**1. el **ucod**2 permitir� qye el cod-op A3 dela instrucci�n supuesta ahora en **RI** sea decodificado, para localizar el **ucod**3 de A3, como sucedi� antes con 2B06 dado que el **ucod**2 no indica la direcci�n del **ucod**3 de cada nueva instrucci�n a ejecutar.
De esta forma, luego de ejecutar cada instrucci�n (con **ucod**3 y **ucod**4),se pide lo siguiente  \(con **ucod**1 y **ucod**2)\, para seguir con los **ucod**3 y con **ucod**4 que determinan la ejecuci�n de esta siguiente instrucci�n, **y asi sucesivamente**. En cada secuencia **ucod**3 \=>\ **ucod**4 \=>\ **ucod**1 \=>\ **ucod**2 la direcci�n de cada **ucod** la provee el **ucod** anterior, siendoque la direcci�n de **ucod**3 la provee el cod-op de
instrucci�n que lleg� a RI, como los se�alan las dos simbollizaciones del registro RI en grisado en la figura 1.34
Los dosprimeros pasos (obtener instrucci�n en RI y decodifcarla -fig1.31) como se trat�, **son comunes a todas las instrucciones**,por lo que los**ucod**1 y **ucod**2 ser�n compartidos por todas las instrucciones.
Tanto **ucod**3 de XX como **ucod**4 de XX hacen referencia a **ucod** de otra instrucci�n que puede ejecutar la UCP.

[imagen2](/Figura pag58.png)

Cada sentencia (por ej. R = P + P -Q) de un programa de alto nivel se traduce en una secuencia de instrucciones (I1, I2, I3, I4 en este caso) y cada instrucci�n se ejecuta mediante una secuencia de **uc�digos** que en uns CISC et�n en una ROM de Control, y que aparecen en las lineas de control al ritmo de los pulsos reloj. Ellos determinan las acciones que deben realizar la UC en cada paso de la ejecuci�n de una instrucci�n.|

:-|

Cuando el c�digo de operaci�n de una instrucci�n llega al registro de RI, el mismo permite ubicar (en este ejemplo) la tercera de dichas combinaciones que debe aparecer en las lineas de la UC para que comience la ejecuci�n de dicha instrucci�n.

>Este conjunto de combinaciones constituyen la \"inteligencia"\ de un >computador, habiendo sido preparadas pro el hombre, para que la UC >pueda ejecutar cada una de las instrucciones de m�quina que forman >parte de cualquier programa contenido en memoria principal, sea de >usuario o del sistema operativo.
Los procesadores qu tienen dichas combinaciones almacenadas en una ROM de Control se dice que son \"maquinas microprogramadas"\.

Todo sucede como si la UC fuera como un robot preprogramado, para que con cada orden distinta que se le imparta (instrucci�n) responda mediante una serie de acciones espec�ficas (ordenadas por las combinaciones que se generan en sus�neas de salida), programadas en su interior por sus creadores.



 