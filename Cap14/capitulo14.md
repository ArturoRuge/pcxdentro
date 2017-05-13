1-114
------------------------------------------------------------------------------------------------------------------
1.14|#PARA ENTENDER LOS 
    |#PENTIUMr I, II, III, 4, XEONr 
    |#Y LOS PROCESADORES RISC

###�Qu� es el "modelo de Von Neumann", y en qu� medida los
###procesadores actuales lo cumplen?
 -----------------------------------------------------------------------------------------------------------------
	si bien con importante mejoras en la velocidad de procesamiento, _la mayor�a de los procesadores actuales
	procesan en base al esquema de la figura_ 1.7, denominado "__modelo de Von Neumann"__[^nota1], que supone:

	~~~
	+ Existe una sola UCP, que procesa en secuencia una instrucci�n tran otra.
	  Ejecuta una sola intrucci�n por vez mediante una serie de paso

	+ Las instrucciones a ejecutar y los datos a procesar, codificados en binario, deben almacenarse en una 
	  rapida memoria interna (memoria principal) antes de realizar el procesamiento de los mismos.

	+ Existen instrucciones de "salto", (figura 1.35) que ordenen a la UC discontinuar o no (seg�n se
	  alcance o no un resultado interno) la secuencia de intrucciones que viene ejecutando, para 
	  pasar a ejecutar otra secuencia, cuya primer intrucci�n se debe poder localizar. 
	~~~

	En la figura 1.27 se endicaban cinco pasos o etapas b�sicas para ejecutar una instrucci�n.
	Una de las primeras mejoras en velocidad para el modelo, fue ejecutar el paso 5 mientras se espera el
	dato a operar (paso 3), quedando asi 4 subprocesas t�picos por lo que pasa la ejecuci�n de cada intruc
	ci�n: los cuales progresan con cada pulso reloj, seg�n se ha visto (figura 1.30, que se repite en la 1.84).

					INSERTAR FIGURA 1.84
	
	La figura 1.85 (izquierda) es similar a la 1.84, salvo la direcci�n (diagonal) en que avanza el proceso, 
	para poder comparar el procesamiento seg�n el modelo original de Von Neumann con otro m�s eficaz. 
	La ejecuci�n de una instrucci�n progresa de un rengl�n al siguiente con cada pulso reloj, por lo
	cual los pulsos se han dibujado en sentido vertical. 
	Primero se termina de ejecutar totalmente una intrucci�n (__I1__), y luego la siguiente (__I2__), insumiendo 
	ejecuci�n de ambas intrucciones 8 pulsos reloj.

###�Qu� mejora en la velocidad presentan los procesadores actuales con "pipe line"?
-----------------------------------------------------------------------------------------------------------------------
	Hoy d�a, para aumentar la velocidad de procesamiento se ha mejorado el modelo original, dando 
	lugar a otro que podemos denominar modelo de Von Neumann con "solapamiento de procesos", o
	con "__pipe line__" o "__segmentado__" -como quiera llamarse- que se pasa a exponer conceptualmente.
	Intel en 1978 ya adopt� el "pipe line"�� en el procesador 8086.

	-------------------------------------
	[^nota1]  > En el presente tamb�n se denomina "escalar o "secuencial", generalizable a cualquier computador que opera en forma secuencial
	> sobre los datos. 
	[^nota2]  > Tracucible "como un tubo"), t�rmino originado en el proceso de fabricaci�n en serie de autos, adoptado por Ford en 1919.														1-115
---------------------------------------------------------------------------------------------------------------------
	Esta mejora sustancial en la cantidad de intrucciones que se procesan por segundo se basa en las l�neas de
	producci�n en serie de las f�bricas dde autos.. En ellas se divide el proceso de fabricaci�n en una serie de
	subprocesos que se pueden realizar en forma independiente. En una cadena de este tipo, cuando se termina
	un subproceso de fabricaci�n de una unidad (como ser el de pintura), la misma es desplazada al lugar donde
	se realiza siguienta subproceso de la cadena, a la par que otra unidad -tambi�n en proceso de fabricaci�n- 
	ocupa el lugar de la primera, para ser sometida al mismo subproceso realizado sobra la unidad anterior.
	De esta forma _se realizan simult�neamente todos los subprocesos_ independientes que requiere el  
	armado de un auto, *pero aplicados a distintos autos* en curso de fabricaci�n. Cuando se termina de 
	producir un autom�vil, los que fueron entrando a la cadena estar�n parcialmente contruidos.
	Para plantear did�cticamente la mejora habida apelaremos a un proceso conocido: el lavado de autos.
	Un lavadero simple tiene una persona a cargo de todas las estapas del lavado. Entra un auto por
	vez, y despu�s de un tiempo, en el cual se sucedieron dichas etapas, el auto sale limpio. Luego 
	entra el auto siguiente a lavar, y as� de seguido.
	Esto es semejante al procesamiento de cada instrucci�n en el modelo original de Von Neumann
	(figura 1.85 izquierda), siendo que la siguiente instrucci�n reci�n se peude comenzar a ejecutar 
	luego de transcurrido el n�mero de pulsos que requiere la ejecuci�n de la anterior. 

	En un lavadero semiautom�tico en el cual el proceso se hace en 4 etapas de 5 minutos (entrada y pago
	del ticket --> cepillado autom�tico --> limpieza de ruedas e interior --> limpieza de vidrios y secado final[^nota1])
	se pueden ir procesando 4 autos simult�neamente. Cada auto tardar�a 20 minutos en salir, pero puede
 	salir __un__ auto terminado cada 5 minutos. Esto es, aumenta la cantidad de autos lavados por hora, lo cual
	redunda en un menor precio de lavado, pero _cada cliente debe esperar_ las 4 etapas (20 minutos).

	Si al modelo de Von Neumann se le agrega "piperlining", la UCP mantiene su esquema b�sico, pero se le 
	debe agregar circuiter�a adicional, del mismo modo que un lavadero autom�tico requiere m�s personal, 
	marquinaria y espacio interno para espera, en comparaci�n con un lavadero manual unipersonal.
	As�, se necesita un buffer para almacenar por orden de llegada los c�digos de varias instrucciones (como
	ser __4__ � 5) pedidas a la memoria (o al cach�), y los otros buffers intermedios entre etapas. Estos sirven para que 
	no se pierda el c�digo de una instrucci�n en curso de ejecuci�n, o datos y resultados relacionados con ella.[^nota2]

	La figura 1.85 (derecha) ilustra c�mo un "pipe line" permite procesar simult�neamente diversas etapas 
	de distintas instrucciones, complet�ndose en cada etapa una parte de la ejecuci�n de cada instrucci�n.
	Se ha supuesto a los fines comparativos que el "pipe line" se realiza con las 4 etapas y tiempos 
	(dados por pulsos reloj, designados __t1__, __t2__,. ...) de la figura 1.84 � 1.30, y que todas las intrucciones 
	requieren para su ejecuci�n 4 pulsos). Entonces la UC ordenar�:
	
	En __t1__, la primera de estas instrucciones que corresponde ejecutar (__I1__), pasa del butter al registro RI.
	En __t2__ el c�digo de __Isub1__ es decodificado, y al registro RI pasa a contener el c�digo de __I2__.
	En __t3__ se trae[^nota3] el dato a operar para __Isub1__, se decodifica __I2__, y a RI llega desde el buffer el c�digo de __I3__. 
	En __t4__ termina de ejecutarse __I1__, se trae el dato a operar para __I2__, se decodifica __I3__ y llega RI el c�digo de __L4__

	As� de seguido se llevan a cabo en paralelo los procesos indicados en diagonal en la figura citada, cada uno
	independiente del otro. De esta forma, al cabo de 8 pulsos se habr�n terminado de ejecutar 4 instrucciones, o
	sea, 4 veces m�s que con el modelo sin "pipe line" que aparece a la izquierda de la misma figura.
	En general, si se tiene un "pipe line" de __n__ etapas, te�ricamente[^nota4] se puede procesar hasta __n__ veces m�s
	instrucciones por segundo que sin "pipe line", suponiendo que todas las intrucciones requieran __n__ etapas.
	Esto implica tambi�n una situaci�n ideal, con todas las instrucciones de igual complejidad, ejecut�ndose
	en 4 pulsos reloj. As�, _con cada pulso entra una instrucci�n al "pipe line", y se termina de ejecutar otra_.
	Resulta, que si bien _no se reduce el tiempo de ejecuci�n de una instruccion_ (cada una requiere __4__ pulsos reloj), 
	en cada pulso __reloj__ se est� ejecutando una etapa de 4 instrucciones distintas, lo cual permite ejecutar varias
	veces m�s rapido (4 en este caso) las instrucciones de un programa que en un modelo sin "pipe line".

	-------------------------------------
	[^nota]  > Suponiendo que esta �ltima etapa sea la que dura 5 minutos y otras mucho menos, ella determina el ritmo de lavado.
	[^nota]  > Del mismo modo, en el lavadero citado puede requerirse un lugar entre dos subprocesos, donde un autom�vil que sale de un sub-proceso
	> permanezca en �l demorado, antes de pasar al siguiente, so pena de llevarse por delante el auto que a�n est� en este subproceso.
	[^nota]  > Desde la memoria cach�, si est� en ella (sino habr� que pedirlo a la memoria principal) o desde un registro de la UCP.
	[^nota]  > Un "pipe line" sin circuitos para "predicci�n de saltos condicionados" puede cortarse, si por ejemplo __I1__ es una instrucci�n de salto
	> condicionado (figura 1.35), que obligue que la siguiente que corresponda ejecutar no sea __I2__; o si tiene lugar de interrupci�n por
	> hardware. O demorarse un pulso reloj por que el dato a operar no est� el cach� y hay que pedirlo a memoria. Asimismo, la circuiter�a
	> extra para el "pipe line" hace que cada instrucci�n se ejecute con pulsos de mayor duraci�n en relaci�n con un modelo sin "pipe line"1-116
---------------------------------------------------------------------------------------------------------------


	INSERTAR FIGURA 1.85

###�Qu� es el multiprocesamiento o procesamiento en paralelo?
---------------------------------------------------------------------------------------------------------------
	Los requerimientos actuales de velocidad de procesamiento hicieron necesario el desarrollo de 
	m�quinas designadas "__no Von Neumann__", en el sentido de que existen __varios procesadores__ operando 
	juntos, __en paralelo__. As� se puden ejecutar ejecutar, en forma independiente, varias instrucciones de un
	mismo programa, o varios programas independientes, u operar con diversos datos a un mismo tiempo.
	Esto se conoce como "__multiprocesamiento__", contrapuesto al "uniprocesamiento" de Von Neumann.
	De existir varios lavaderos que trabajen "en paralelo" ser�a factible que varios autos salgan
	terminados simult�neamente y que adem�s se ayuden mutuamente. En las arquitecturas "no Von
	Neumann", varias UCP pueden terminar de ejecutar juntas varias instrucciones por pulso reloj.

	~~~
	No debe confudirse _multiprocesamiento_ con "__multiprogramacion__" ("_multitasking_", tambi�n traduci-
	ble como "_multitarea_"), consistente en la ejecuci�n alternada por un UCP de varios programas que
	est�n en memoria principal. Dada la velocidad de procesamiento, _puede parecerle al usuario como 
	simult�nea la ejecuci�n de dos o m�s programas cuya ejecuci�n en realidad se alterna muy r�pidamente_.
	~~~


###�C�mo funciona b�sicamente un micropocesador 486?
----------------------------------------------------------------------------------------------------------------
	A continuaci�n describiremos los principales bloques que est�n en el interior de un procesador 486 (figura
	1.86), y las funciones que cumplen. Luego se concretar� de que modo los mismos parcipan, paso a paso,
	en la ejecuci�n de la conocida secuencia de instrucciones __I1, I2, I3, I4__ desarrollada en las figuras 1.23 a 1.26.
	Este procesamiento, que fue realizado en dichas figuras conforme al modelo "original" de Von Neumannm 
	fue acelerado ya en procesadores de Intel anteriores al 486, como se desarroll� en una respuesta anterior.
	En la figura 1.86 aparecen los siguientes sub-bloques y bloques:

	+ Los registros de direcciones (RDI) y de datos (RDA), pertenecientes a la "_Unidad de Interconexi�n con
	  el Bus_" (__BIU__ en ingl�s), encargada de la comunicaci�n con el exterior a trav�s de las 32 l�neas de datos y
	  32 l�neas de direcciones del bus, conectadas a las correspondientes patas del procesador ("local bus"). En
	  Relaci�n con �ste, los registros RDI y RDA cumplen las mismas funciones que en la figura 1.23, siendo 
	  que ahora intrucciones y datos le�dos en memoria pasan al cach� interno de 8 KB del procesador 
														1-117
-------------------------------------------------------------------------------------------------------------
	. La _Unidad de cach�_ de 8 KB guarda las instrucciones y datos que seguramente ser�n requeridos pr�x-
	  mamente. Por una parte, a trav�s de un bus de 128 l�neas,se pueden leer del cach� 128/8 = 16 bytes que
	  pasan a un buffer de la Unidad de pre-carga de instrucciones. Corresponden en promedio a unas 5
	  instrucciones a ejecutar, que as� llegan juntas para entrar al "pipe line".Por otra, el cach� puede ser le�do
	  para que se env�en 32 biys de datos a la UAL, o un registro de la UCP � 64 bits de datos a la Unidad de 
	  Punto Flotante(FPU en ingl�s). En una escritura van hacia el cach� 32 � 64 bits, respectivamente 

	. La _Unidad de Pre-Carga_ proporciona las direcciones de las pr�ximas instrucciones a ejecturar, y
	  guarda las mismas en orden en dos buffers de 16 bytes, para que luego cada una sea decodificada

	. La _Unidad de Decodificaci�n_ realiza dos decodificaciones de cada instrucci�n, seg�n se ver�.

	. La _Unidad de Control_ (UC) mediante l�neas que salen de ella(dibujadas en figuras 1.87 a 1.89), activa las
	  operaciones que con cada pulso reloj deben realizar los distintos bloques de la UCP (U. de pre-carga,
	 U.Decodificadora, UAL UPF y UC), Conforme lo establecen microc�digoa de la ROM de Control.

	. La _Unidad de segmentaci�n, paginaci�n y protecci�n de memoria_, conocida como "Unidad de 
	  manejo de memoria" (__MMU__ en ingl�s) se encarga de proporcionar las direcciones f�sicas de
	  memoria que utiliza un programa Para tal fin esta unidad convierte la referencia a la direcci�n del
	  dato -que viene con la instrucci�n- en la correspondiente direcci�n f�sica. Puesto que la memoria
	  de una PC se divide en segmentos, y �stos -de ser necesario- pueden subdividirse en p�ginas
	  (por ejemplo si se usa el sistema operativo Unix). Esta unidad se encarga de ello, as� como de la 
	  protecci�n contra escrituras no permitidas en zonas reservadas de memoria. Conviene aclarar que 
	  el nombre de esta unidad no tiene mucho que ver con la traducci�n castellana de "pipe line" como
	  "segmentaci�n", raz�n por la cual se prefiri� usar dicha palabra inglesa.

					INSERTAR FIGURA 1.86
	
	Todas estas unidades participan en el "pipe line" de instrucciones, que en el 486 consta de 5 etapas, 
	que progresan con cada pulso reloj, al comp�s de sus millones de ciclos por segundo:1-118
-------------------------------------------------------------------------------------------------------------------
	1. __Pre-carga__ ("pre-fetch") consiste en la llegada de los c�digos de las pr�ximas instrucciones que entrar�n
	   al "pipe line" a dos buffers(de 16 bytes cada uno) de la Unidad de Pre-carga, ,para formar una "cola".
	   En la figura 1.86 se ha supuesto que a uno de estos buffers han llegado desde el cach� 5 instrucciones
	   (promedio de instrucciones que entran en los 16 bytes de este buffer) en forma simult�nea. Los c�digos
	   de ellas son los mismos que hemos usado en la figura 1.15 para __I1, I2, I3, I4,__ que en hexa son A10050,
	   30600500, B0600650, y A31050, respectivamente. La instrucci�n __I5__, aparece con un c�digo XXXX. De no 
	   haber estado estas intrucciones en el cach�, primero se hubiera pedido __I1__ a la memoria principal[nota1], y 
	   llegar�a una copia de su c�digo al buffer de pre-carga para que entre al "pipe line", y otra copia del mis
	   mo al chach�. Inmediatamente legar�n luego al cach� desde memoria, uno tras otro, los c�digos de __I2, 
	   I3, I4__[^nota2], que pasar�n a la cola del buffer. De esta forma, s�lo se pierde tiempo en obtener del exterior a __I1__
	
	2. __Primera Decodificaci�n:__ a la Unidad de Decodificaci�n llegan los primeros 3 bytes de cada 
	   instrucci�n, para separar -entre todos los bytes que forman su c�digo de m�quina- su c�digo
	   de operaci�n, del n�mero que hace referencia a la direcci�n del dato (Los c�digos de operaci�n
	   pueden tener de 1 a 3 bytes). As�, en la figura 1.86, al primer decodificador llegan los bytes
	   A10050H, que en este caso son todos los bytes de la instrucci�n __I1__, identific�ndose __A1__ como el
	   c�digo de operaci�n, y __0050__ como la referencia a la direcci�n del operando, n�mero que pasar�
	   a la Unidad de segmentaci�n y paginaci�n, que formar� la direcci�n del dato a operar, de modo
	   que pueda ser le�do del cach� (si est� en �ste).

	3. __Segunda Decodificaci�n:__ en la figura 1.87, el c�digo de operaci�n __A1__ identificado en el paso
	   anterior es ahora decodificado. Esto permite determinar la secuencia de microc�digo contenida en la 
	   ROM de Control. Merced a esta secuencia la UC generar� las se�ales de control, que enviar� por las 
	   l�neas (insinuadas con flechas) que salen de ella, para que cada unidad que controla, ejecute una
	   parte de la instrucci�n con cada pulsos reloj (como en la figuras 1.31 y 1.32), Si la instrucci�n es
	   simple se ejecuta en un solo pulso. Al mismo tiempo que __I1__ pasa por esta etapa del "pipe line", tres
	   bytes (030600H) del c�digo de __I2__ (03060050H) entran a la etapa de primera codificaci�n, siendo que 
	   0050 -direcci�n traspuesta del dato- pasar� a la U.de segmentaci�n, para leer luego el dato del cach�.

	4. __Ejecuci�n:__ en la figura 1.88 el dato que debe transferirse al registro AX -como ordena __I1__- hay que
	   leerlo en la direcci�n (500H) que la U. de Segmentaci�n dej� en el registro RDI, la cual permite leer el
	   dato a operar en el cach�. Suponiendo que el dato est� en la U de cach�, el mismo llegar� al registro
	   RDA[^nota3]. Paralelamente con la acci�n reci�n descripta para __I1__, el c�digo 0306 de __I2__ pasa a la segunda
	   decodificaci�n, a la par que los bytes 2B0606 del c�digo 2B060650 de __I3__ van a la primera decodificaci�n.

	5. __Almacenamiento de resultados:__ a esta etapa final del "pipe line" llega __I1__, complet�ndose su 
	   ejecuci�n, para lo cual el dato (1020H) pasar� al registro AX (paso incluido en la figura 1.88).
	   Al mismo tiempo se tiene que: __I2__ entra en la etapa de ejecuci�n obteni�ndose del cach� el dato
	   1020H, que pasa al RDA. Este dato se suma en la UAL con el contenido (1020H) de AX (figura
	   1.88), conforme ordena el c�digo de dicha instrucci�n.
	   El c�digo 2B06 de la instrucci�n __I3__ entra a la segunda decodificaci�n, y los bytes A31050, o sea
	   todos los que conforman el c�digo A31050 de __Isub4__ son sometidos a la primer decodificaci�n.
	
	En la figura 1.89 se ha incluido c�mo progresa el "pipe line" con otro pulso reloj, a fin de terminar 
	de ejecutar __I2__, que pasa a la quinta etapa. En �sta, el resultado de la UAL (2040H) debe guardarse
	en AX, as� como los "flags" SZVC que ella tambi�n genera, resultantes de la operaci�n, en el regis-
	tro de estado (no dibujado). Paralelamente, __I3, I4__ e __I5__, pasan por las etapas 4, 3 y 2 del "pipe line".







	----------------------------------
	[^nota3]  > Si como es corriente, existe un segundo nivel de cach� exterior (por ejemplo de 256 __KB__), se buscar�a __Isub1__ primero en este cach�
	> r�pido, y de no encontrarse en el mismo, se obtendr�a __I1__ de memoria principal.
	[^nota3]  > Cuando no hay un contenido en un cach�, su controlador solicita a la memoria el mismo y los que est�n en las direcciones siguientes
	[^nota3]  > Por razones did�cticas se ha buscado continuidad con el modelo de Von Neumann (figuras 1.23 a 1.26), aunque la ejecuci�n de __I1__
	> pueda realizarse en un paso menos en el 486. Esta simplicaci�n puede traer alguna inconsistencias en el paso 5.   1-131
	Las *�ops-R generadas por instrucciones complejas son aportadas por la ROM* vinculada al TC (fig.194),por
	ser las mismas infrecuentes de aparecer en un programa.
	Tambi�n debe suponerse que cuando se direcciona al __TC__ para localizar en una l�nea del mismo una pr�xima
	secuencia de 3 �ops-R a ejecutar, �stas deben aparecer en las salidas del __TC__. Dichas �ops-R (de igual 
	longitud) ir�n a la etapa de Renombramiento de Registros ( __RR__ ) de donde pasan seg�n el orden originario a
	la "Cola de �ops-R", junto con la direcci�n de la instrucci�n que los origin�. Lo mismo ocurre con las �ops-R
	generadas por la ROM. Esta cola oficia de buffer intermediario entre los subsistemas que operan en orden y desorden.
	Para la "HT" este buffer se comparte mitad para cada "thread", pudi�ndose identificar en esta cola las �ops-R
	de cada "thread". Si para la "HT" se debe acceder simult�neamente al __TC__ para obtener l�neas con �ops-R de 
	ambos "threads", durante un ciclo pedir� una l�nea cada uno de ellos, y en el siguiente una l�nea del otro.
	Mientras uno de ellos esta detenido se podr� acceder durante ciclos sucesivos al __TC__ para obtener l�neas 
	del otro.Por lo tanto el __TC__ es un recurso compartido en "HT", puediendo un "thread" tener m�s l�neas que otro.
	Tambi�n es compartida la ROM de �ops-R. Cuando el cach� L2 llega una instrucci�n compleja, el __TC__ le env�a a la ROM
	el n�mero que genera la __UPD__ el cual es como la direcci�n de la ROM donde est� la primera de una secuencia de
	�ops-R, en que se traduce una instrucci�n compleja que lleg� a la __UPD__. Para "HT" el hardware permite identificar
	a que "thread" corresponde dicha sencuencia.
	Si al direccionar el __TC__ *hay un fallo* ("miss") se debe acceder a la jerarqu�a de memorias (en primer lugar al cach�
	L2) para obtener dos l�neas de instrucciones (64 bytes), las cuales ser�n traducidas por la __UPD__ (de a una por
	vez) y enviadas como �ops-R a la __UT__ y tambi�n a la "Cola de �ops-R".
	>Obs�rvese que en esta arquitectura s�lo se pierde tiempo en las traducciones cuando hay un fallo en el __TC__ 

Antes de ir a la __UPD__ los 64 bytes citados  provenientes del cach� L2, temporariamente se guardan en el Buffer L2
	( __BL2__ ) hasta que puedan ser decodificadas las instrucciones. Para "HT" existen dos __BL2__, uno para cada "thread".
	Tambi�n existen dos __CRS__ y dos buffers para instrucciones de retorno (de subrutina, por ejemplo).
	>En definitiva el __TC__ mayormente provee las �ops-R que se van ejecutar pr�ximamente, y cada vez que en el __TC__
	hay un fallo, la __UPD__ traducir� en �ops-R las instrucciones __BL2__ ( *a raz�n de una por vez* ) que ir�n al __TC__
	y tambi�n a la cola de �ops-R, salvo que aparezca alguna instrucci�n compleja. Esto es como en una UCP con cach�: si
	hay fallo, las instrucciones a ejecutar van al cach� y la UCP (en este caso dicha cola).
	
Si en "HT" hace falta decodificar instrucciones de los dos "threads", se sacan alternadamente secuencias de cada __BL2__
	
En Proceso de ejecuci�n de �ops-R se inicia con una asignaci�n ("allocation") en la etapa __RR__ que renombra los
	registro de 80x86 indicados en la �ops-R, que est�n en la "Cola de �ops-R" en otros registros "alias". Para tal fin
	existen 128 registros para enteros y 128 para punto flotante, m�s buffers para reordenamiento y para operaciones
	load/store., que para "HT" son particionados en mitades, una para cada "thread", siempre identificables por el 
	hardware del procesador, como en todos los casos.
	En "HT" en la "Cola de �ops-R" Hay �ops-R de los dos "threads",y con cada pulso reloj se alterna la asignaci�n de 
	recursos de la __RR__ . Si en un "thread" usa todos los recursos que tiene reservados, la asignaci�n sigue para el otro.	
	Junto con la asignaci�n se realiza el renombramiento de registros. Para ello existen dos "Tabalas de Registros Alias",	
	que indican para cada nueva �ops-R que se va a ejecutar de cada "thread" en que registro "alias" estar�n sus operandos
	(que pueden ser resultados de �ops-R ejecutadas antes),y en que registro "alias" ir� el resultado.
	Las secuencias de �ops-R con sus registros nombrados pasan a dos colas": una para provenientes de instrucciones 
	load/store (que deben acceder a memoria), y otra para las que se tradujeron de las instrucciones que no ordenan acceder 
	a memoria. Estas dos colas tambi�n pueden ser particionadas con la mitad de entradas para cada "thread". De estas colas
	salen �ops-R hacia la __UPRE__ , en forma alternada -una por "thread" y con cada pulso reloj.
	
En la __UPRE__ existen 5 "L�gicas planificadoras" (__LP__) que determinan c�ando �ops-R se puede ejecutar. Cada __LP__
	tiene su propia cola de 8 a 12 �ops-R que debe seleccionar para enviar a las __UE__. *Las __LP__ no distiguen entre �ops-R
	de dos "threads"*. Las �ops-R se seleccionan en funci�n de la dependencia de datos y disponibilidad de __UE__. Para evitar
	problemas est� limitado el n�mero de entradas en uso que puede tener en cada cola un "thread".	
	
>Puesto que para cada �ops-R se efect�a en una __UE__ la operaci�n que ordena con los datos apropiados y se deja el
	resultado en el destino indicado por ella: y dado que dichos datos est�n fisicamente en registros que est�n definidos
	desde la etapa __RR__, al igual que el destino del resultado, y que para "HT" dichos recursos est�n separados para cada 
	"thread", no hay problemas en encontrar los resultados que usar�n las �ops-R que se ejecutar�n luego.
	Asimismo las �ops-R se pueden identificar, pues tienen asociado (incluso en la __UT__) un n�mero que es la direcci�n
	en memoria de la instrucci�n originaria de la cual fueron traducidas.
	
Si bien cada ciclo reloj de las __LP__ pueden hacer que las __UE__ efect�en las operaciones de hasta 6 �ops-R, como el 
	m�ximo de �ops-R que genera la __UT__ es 3, *queda limitado a este n�mero la cantidad de �ops-R ejecutables por ciclo*.
	
	
	
Figura 1.94

Existe 4 **UE**, siendo que las dos que contienen una **UAL** operan al doble de la frecuencia del procesador, o sea
que en medio ciclo completa una operacion, siendo por ello posibles hasta 6 operaciones por ciclo. Ellas son:
**UE0** dedicaca a �ops-R "store", y **UE1** para �ops-R "load", a raz�n de una �op-R por ciclo.
**UE2**: en la primer mitad de un ciclo puede operar enteros en una **UAL**, o una instrucci�n de transferencia en
punto flotatnte; y en la segunda mitad de un ciclo puede operar nuevamente enteros en la **UAL** de dicha **UE**.

Para �ops-R load/store existe un Bufer Conversor compartido en "HT" por los dos "threads", que es una memoria
totalmente asociada (definida al tratar cach�s), que convierte direcciones a direcciones fisicas de memoria.
Despu�s de haberse realizado la operaci�n ordenada por cada �op-R en la **UE** correspondiente, las �ops-R
pasan a un buffer de reordenamiento, que hace de intermediario entre la **UPRE** y la **UR**. este buffer se parte en
mitades si hay dos "threads".

La **UR** retira las �ops-R en orden en forma alternada para cuando "thread".
Luego que las �ops-R ejecutadas se retiran, los resultados pasan desde registros hacia el caach� de datos **L1**.
Este es un cach� asociativo de 4 vias con l�neas de 64 bytes, que siempre escribe "write-through" en el cach�
asociativo **L2** de 8 v�as con l�neas de 64 bytes, con 128 bytes por l�nea. Este Xeon tiene un cach� similar al *L3*
Los cach�s **L2** y **L3** operan con direcciones f�sicas y el **L1** con virtuales, pero con tags f�sicos.

De la descripci�n anterior reslta, que dos "threads" que se est�n ejecutando en paralelo comparten (en principio
por partes iguales) la mayor�a de los recursos f�sicos de un �nico procesador, ya sea por partici�n de los mismos o 
por alternancia (en un ciclo reloj uno y en el siguiente el otro) y no se trata simplemente que se ejecuta un "thread" 
y cuando �ste se detiene por alg�n motivo se pasa a ejecutar el otro.           
1-133
# REPRESENTACI�N DE N�MEROS BINARIOS NATURALES Y OPERACIONES CON ELLOS

A1.1|  ##SISTEMAS N�MERICOS POSICIONALES
	
####�Qu� es un sistema num�rico posicional?
La necesidad de representar conjuntos de objetos ah llevado a las distintas culturas a adoptar diversas formas de 
	simbolizar su valor num�rico.
Una manera primera de representar el n�mero de elementos que constituyen un cierto conjunto, es establecer una 
	correspondencia con un n�mero igual de s�mbolos.
	Esto lo hacemos cuando contamos con los dedos,o si para representar, como ser, los d�as de la semana,
	dibujamos igual n�meros o trazos:           | | | | | | |
	Tal sistema de representaci�n ser�a *"unario"*, pues se usa un solo tipo de s�mbolo. Su desventaja es que no permite
	simbolizar c�moda y r�pidamente conjuntos de muchos elementos.
	
Cuando fue necesario designar la existencia de muchos elementos, se trat� siempre de *utilizar menos cantidad de simbolos*	
	,para lo cual se establecieron *impl�citas* ente los mismos.
	Los romanos utilizaron un sistema de signos de valor creciente: __I__,__V__,__X__,__L__,__C__,__D__,__M__, etc,
	que se agrupan de derecha a izquierda, sum�ndose o rest�ndose entre s�, seg�n sugieran o no el orden creciente.
	
__CXVII__ = cien + diez + cinco + uno + uno
						__MCMV__  = mil + (mil - cien) + cinco

Esta codificaci�n requer�a nuevos s�mbolos cuando seagotaban los de mayor valor, a la par que los c�lculos por su
	complejidad conven�a realizarlos con �bacos.
	Fueron los pueblos orientales y americanos (mayas) los que desarrollaron los sistemas *posicionales*, basados en un conjunto
	limitado y constante de s�mbolos, entre los cuales se encontraba el "cero", para indicar la ausencia de elementos. Miles 
	de a�os antes, el �baco, construido en la tierra  o con madera fue el antecesor natural de estos sistemas, siendo que la ausencia
	de objetose en una posici�n o varilla implicaba de hecho el cero.
	
>En estos sistemas, __cada s�mbolo__, adem�s del n�mero que elementos de un tipo que representa considerado aisladamente,
	__tiene un significado o peso distinto, seg�n la posici�n que ocupa en el grupo__ de caracteres del que forma parte.

De esta manera es posible representar sistem�ticamente *cualquier* n�mero, empleado en forma combinada un conjunto *limitado* de
	caracteres simb�licos.
	Los caracteres se denominan *"d�gitos"*, y constituyen piezas de informaci�n digital (secci�n 1.10)
	
>Relacionado con los diez dedos, el __sistema posicional decimal__ , tambi�n denominado de *"base o ra�z diez"* por utilizar
	diez s�mbolos (que forma la sucesi�n mon�tona creciente __0,1,2,3,4,5,6,7,8,9__) permite representar cualquier n�mero de elementos
	combinando dichos s�mbolos.

Este sistema servir� para comprender conceptualmente en qu� consiste y cu�l es la estructura de cualquier sistema num�rico posicional.134

Si bien en la pr�ctica apreciamos mec�nica e intuitivamente, sin pensar, la magnitud de un n�mero decimal con solo
visualizarlo, en realidad la cantidad de elemntos que un n�mero simboliza se determina sumando los productos
que se obtienen de multiplicar el valor de las unidades que representa cada d�gito por el ***peso*** (valor) de la
posici�n que ocupa (unidades, decenas, etc).

9323 = 9x1000 + 3x100 + 2x10 + 3x1   siendo: 10 = 1 x 10[^nota1]; 100 = 10 x 10 = 10[^nota2; 1000 = 100 x 10 = 10[^nota3]

>Resulta que __el peso de cada posici�n es el de la anterior multiplicada por la base__ (diez, o sea el n�mero de s�mbolos de
sistema), *resultando as� los pesos potencias crecientes de la base*. Esto es com�n a todos los sistemas posicionales. En caso
de necesitarse representar n�meros m�s grandes se usan siempre los mismos diez s�mbolos,y s�lo es necesario agregar nuevas posicionse 
a la izquierda.
Un sistema num�rico es una forma de fraccionar una totalidad de porciones, cuyos tama�os, a partir del valor uno, se van escalonando
-a medida que se requieren nuevos tama�os- de forma tal que cada tama�o que se necesite es el anterior multiplicado por la cantidad de 
s�mbolos de la base.
El n�mero m�ximo de porciones de cada tama�oo lo determina el s�mbolo de mayor valor de la base en cuesti�n.

Cuadno leemos 109 personas (109 = 1x100 + 0x10 + 9x1) en relaci�n a la totalidad de dichas personas, las mismas de hecho han sido 
divididas en forma *virtual*, de modo de conformar de manera �nica:
- un solo grupo de 100, (pueden existir hasta 9 grupos posibles de 100),
- con las restantes (109-100=9) no se puede formar ning�n grupo de 10, y s� 9 grupos de personas.
Tambi�n puede pensarse en relaci�n a un n�mero 109,que en una balanza (figura A1.1) se debe pesar un objeto 
*de peso supuestamente desconocido*, pero que a los fines did�cticos de simular su pesada debemos partir de que dicho peso es conocido
(109 grs)

	INSERTAR FIGURA A1.1

Los juegos de pesas a utilizar en base diez ser�n subconjuntos de 9 pesas de m�ltiplos de diez:
- 9 pesas de 1 gramo.
- 9 pesas de 10 gramos.
- 9 pesas de 100 gramos.
- 9 pesas de 1000 gramos... y as� de seguido; o sea que podemos tener m�s subconjuntos de 9 pesas que sean m�ltiplos de diez 
(te�ricamente infinitos), seg�n sea la magnitud del peso de los objetos que se quiere pesar.

Para pesar dicho objeto se usar�a primero una pesa de 100grs. (la de mayor peso posible para empezar a equilibrar, siendo que con
dos pesas de ese tipo se extender�a los 109 grs. a pesar: 100 + 100 = 200 > 109).
Luego si se prueba con una pesa de 10grs, tambi�n se exeder� el peso a ponderar: 100 + 10 = 110 > 109).
Finalmente agregando 9 pesas de 1gr, se equilibra la balanza. En definitiva se usaron: __1__ pesa de 100grs, __0__ pesas de 10grs
 y __9__ pesas de 1gr con lo cual el n�mero 109 indica el peso del objeto en base diez. O sea: 1 0 9 = 1x100 + 0x10 + 1x9

Es importante observar qeu tanto con las personas como con la balanza, se empieza siempre respectivamente por los grupos o pesas mas
grandes (de valor ...1000, 100.....) que se puedan formar  o emplear. De este modo se aseguran qeu la representaci�n simb�lica es �nica.


##�Cu�les son las caracter�sticas de los sistemas num�ricos posicionales?

Podemos sistemizar como sigue las caracter�sticas del sistema decimal, que tambi�n, como se tratar�, *son comunes a todos los sistemas 
num�ricos  posicionales*, cualquiera sea su base (definida por el n�mero de s�mbolos empleados para formar n�meros)

> -Consta de un n�mero finito de s�mbolos individuales que constituyen la  *"base o ra�z"* del sistema (diez en sistema decimal, dos en 
el binario, etc).
- Cada s�mbolo aislado representa un n�mero espec�fico de *unidades*.
- Existe un s�mbolo (*cero*) para indicar la ausencia de elementos a representar.
- Los s�mbolos pueden ordenarse en forma mon�tona creciente.
- Formando parte de un n�mero compuesto por varios s�mbolos, *un mismo s�mbolo tiene un significado o "peso"  distinto seg�n su posici�n
relativa en el conjunto*.
-La posici�n extrema derecha corresponde a  unidad (peso uno): a partir de ella, cada posici�n tiene el peso de la que est� a su derecha 
multiplicada por la base, resultando siempre que *el peso de cada posici�n es una potencia de lab ase. Esta en todas las bases se simboliza*
__10__ ("uno cero").135

A1.2 # SISTEMAS NUMERICOS OCTAL BINARIO Y HEXADECIMAL

## �Qu� s�mbolos se emplean en otras bases num�ricas y c�mo se representan n�meros en ellas?

A los fines de que resulte f�cil simbolozar en otros sistemas num�ricos, los s�mbolos 0 y 1 existen en todos los sistemas con 
igual significado que en el decimal.
Si otros sistemas usan algunos o todos los s�mbolos decimales restantes del 2 al 9, se ha acordado que su significado es el mismo
que en decimal. As� 7 representa siete unidades, ya sea en decimal, octal o hexadecimal.

El __sistema hexadecimal__ tendr� __diecis�is__ s�mbolos distintos que constituyen la base.
Del 0 al 9 coinciden en significado con los correspondientes decimales; para los seis restantes se crearon los simbolos de la
__A__ hasta la __F__, como aparecen en la figura A1.1 en correspondencia a sus equivalentes decimales y con los n�meros de otros sistemas

INSERTAR FIGURA A1.2

###Sistemas en base ocho u octal

En base ocho los s�mbolos van de 0 al 7 (fig A1.2), con los cuales se puede formar cualquier n�mero.
Con los mismos supuestos que planteamos para la pesada realizada en relacion con la fig A1.1, pesaremos (fig A1.3) el mismo objeto cuyo
peso en octal supondremos desconocido, siendo que en base diez pesa 109 grs.Veamos c�ales son las pesas en base ocho. Si en base diez cada
pesa en relaci�n con la del tama�o anterior era diez veces m�s pesadas, en octal lo ser� __ocho veces__. Juntando ocho pesas de un valor 
se construye una pesa del tama�o siguiente. Si para fines did�cticos simbolizamos en base diez el peso de cada tipo de pesa octal, por lo
que se tendrpia la serie de valores: __1__ gr; 1gr x 8d = ___8__d grs x 8 d = __64__d grs; 64d grs x 8d = __512__d grs., etc...
El s�mbolo "d" indica que se trata de base diez. El s�mbolo para representar 1 es el mismo en ambas bases.
*De cada uno de dichos tama�os existen un total de 7 pesas octales* (en base diez eran 9), siendo 7 el s�mbolo octal de mayor valor:
- 7 pesas de 1gr.
- 7 pesas de ocho veces mayor que la de 1gr (8d grs)
- 7 pesas diecis�is veces mayor que la de 1gr (16d gramos) y ocho veces mayor al tama�o anterior.
- 7 pesas sesenta y cuatro veces mayores que la de 1gr (64d grs) y ocho veecs mayor que el tama�o anterior.
y asi de seguido, o sea que podemos tener m�s subconjuntos de 7 pesas que sean m�ltiplos de ocho (te�ricamente infinitos), seg�n
sea la magnitud del peso de los objetos que se quiere pesar.

INSERTAR FIGURA A1.3

Volvemos a pesar el objeto que en base diez pesaba 109grs.Cuando se pesa un objeto en general se desconoce su peso, el cual hay que determinar
Para ello se requiere ir probando poniendo y sacando pesas (octales en este caso), hasta que con las pesasdas adecuadas a la balanza alcance 
el equilibrio. La selecci�n de las pesas adecuadas la simualremos haciendo c�lculos simples en base diez, como se hizo en relaci�n con la 
figura A1.1.
Suponiendo (fig A1.3) que se empeiza adecuadamente a equilibrar la balanza con __una__ pesa setenta y cuatro veces mayor que la de 1gr
en el platillo derecho. Pensando en base diez se habr�a equilibrado 64d grs, por lo que faltar� quilibrar 109 - 64 = 45d grs.
Si se coloca otra pesa del mismo tama�o que el anterior se tendr�a: 64d + 64d = 128d > 109d, y el peso del platinillo derecho superar�a 
al del izquierdo, por lo qeu no puede colocarse m�s que una pesa de dicho tama�o.﻿m.ginzburg
-F pesas de 1gr
-F pesas dieciséis veces mayor que la de 1gr. (16d grs)
-F pesas docientoscincuenta y seis veces mayor que la de 1gr. (256d grs) y dieciseis veces el tamaño anterior 
-F pesas mil veinticuatro veces mayor que la de 1gr. (1024d grs) y dieciséis veces el  tamaño anterior.
y asi de seguido, o sea que podemos tener mas subconjuntos de F pesas que sean múltiplos de dieciséis
(teóricamente infinitos), según sea la magnitud del peso de los objetos que se quiere pesar.

figura A1.7
Otra vez pesaremos el objeto que en base diez pesa 109 grs. la selección de pas pesas adecuadas la simula-
remos haciendo cálculos simples en base diez, como se hizo en relacion con las figuras A1.1 y A1.3.
suponiendo (fig A1.7) que se empieza adecuadamente a equilibrar la balanza con las pesas dieciséis veces mas 
pesadas que 1 gr., se podrán colocar hasta 6 pesas de ese peso, con lo cual, calculando en base diez, 
habremos equilibrado 6x16=96d grs., faltando equilibrar 109-96=13dgrs. El equilibrio de los platillos se logra
agragando 13d=Dh pesas del tamaño menor siguiente, que es de 1gr. por consiguiente,
el peso del objeto en hexa es *6D*. O sea: 109d=155 base(0)=1101101b=6Dh

asimismo, si pensamos en el conjunto de personas que en base diez fue dividido conforme indican los simbolos 109, 
dicha totalidad en base dieciseis fue dividida (pensando el tamaño de los grupos en base diez), en 6 grupos
de 16, y 13 grupos de una persona, siendo que pueden existir hasta F=15 grupos de cada tipo.

**¿Como se sombolizan los pesos en hexadecimal sin necesidad de estimarlos en bases diez?**
AL igual que cualquier otro sistema, el hexadecimales no surge del sistma decimal, sino que es independiente como
asi lo sufiere la posibilidad de pesar el objeto en cuestion usando pesas hexadecimales, pudiendose simbolizar en 
hexa el valor de las pesas o pesos de este sistema simplemente (fig a 1.8) si ponemos en el plato izquierdo de la 
balanza un peso de dieciseis veces mayot que 1gr.(16 grs. en base diez) para equilibrarlo hace falta una sola presa 
dieciseis veces mayor que 1 gr, y ninguna (cero) pesa de 1gr., osea que esta pesa o pseo en hexa se simboliza 10
(lease uno-cero y no "diez").
conforme con esto, en el fig. A1,2 luego del simbolo mayor F sigue el **10** (1^16 0h^1 = 16d), asi como en base diez
despues del 9 sigue el 10, en octal despues del 7 sigue el 10, y en binario despues del 1 sigue el 10.
Del mismo modo si en el plato izquierdo se colocaria un peso docientos cincuenta y seis veces mayor que 1gr
se equilibra con una sola de peso de ese tamaño y ninguna de los tamaños menores, por lo que en hexa este peso 
se simboliza 100h (lease uno-cero, y no "cien").
por lo tanto, tambien en hexa las pesas se simbolizan 1, 10, 100, 1000...(estos mismos simbolos representan los
valores de las pesas que se usan en base diez, aunque en hexa representan 1, 16, 256, y 4096, respectivamente).
osea 100% en hexa:  


.                        6^10  D^1 h^jh  =6x10+Dx1jh

esta cuenta (que indica 6 pesas de 100,mas D pesas de 1) realizada en hexadecimal daria, obviamente, 6Dh.

con los pesos de 6Dh en base diez es: 6^16 D^1 h=[6x16+13x1]d=109d;
esto es, pesos de 6Dh en base de diez se usaron una pesa de 64 mas 5 de 8, mas 5 
de 1, suma que da 109d.

Figura A1.8
como ya se dijo, al valorar los pesos de una base en diez en esencia se esta pasando dicha base a base diez.

**ejercicio:**
con la balanza con peso hexadecimales pesar un objeto que en base diez pesa 112d.        Respuesta:70h
idem otro que pesa 100d                                                                  Respuesta 64h

##**¿cono se halla facilmente el siguiente de cada numero en base ?**
Elcuenta vueltas que indica los kms. recorridos por un auto consta de ruedas con los simbolos del 0 al 9.
Cada rueda al cambiar de 9 a 0 obliga a la que esta a su izquierda a avanzar una posicion. La rueda de las unidades
progresa una unidad merced a una accion exterior para que las otras puedan cambiar, si asi debe ocurrir.
suponiendo que el numero que esta en frente al vidor es 4588, si la rueda de las unidades avanza un simbolo, oasara de 8 a 9sin
adectar la rueda de las decenas, por lo que el numero siguiente es 4589. Cuando las unidades vuelvan a aumentar uno, ahora 
pasaran de 9 a 0, lo que hara que las decenas tambien progresen uno. De 8 a 9, sin afectar la centenas. Por lo tanto.el
numero que sigue sera 44590. Con las mismas consideraciones si las unidades siguen aumentando uno. Sucesivamente se
tendra: 4591,4592....4599. Luego de éste  las unidades pasan de 9 a 0, lo que hace que las decenas  tambien pasen de 9 a 0,
lo cual a su vez obliga que las centenas cambien de 5 a 6. asi se forma 4600, y asi seguido   ﻿*cuentas vueltas hexadecimal y binario* nos permintiran hallar facilmente el numero que sigue a otro dado.
en hexadecimal cada rueda tiene desiseis simbolos (0,1,2,3,4,5,6,7,8,9,a,b,c,d,e,f), y cuando cambia de f a 9 hace cambiar la
rueda qye esta a su izquierda salco que hay 16 simbolos en cada rueda en vez de diez, todo es igual al cuenta vueltas anterioro.
asumiendo que el cuenta vuelta hexadecimal indica 3899. si la rueda de las unidades avanza un simbolo pasara de 9 a A, sin
hacer cambio en la rueda la  que esta a su izquierda, por lo que el numero hexadecimal siguiente es 389A. Luego cada vez que las 
unidades aumentan en uno, sucesivamente se iran formando 389B, 289C, 289E, 389F. con el siguiente cambio de la
rueda de las unidades, esta pasara de F a 0, con lo siguiente avance en uno de la rueda delas unidades esta pasara de F a
0, forzando que la rueda que esta a su izquierda rambien cambie de f a 0, lo que a su vez tambien hace que su rueda vecina izquierda
pase de f a 0, lo que a su vez hara que la rueda que esta a su izquierda cambe de 3 a 4, en  fefinitiva 3FFF se paso a 4000.

Podemos imaginar un **cuenta vueltas binario** constituido por ruedas que solo tienen dos simbolos **0** y **1**, cada uno ocupando una
mitad de cada rueda. cuando una rueda pasa de 1 a 0 obliga a la que esta a su izquierda que gire media vuelta para que pase a 1
si estaba en 0, o que pase a 0 si estaba en 1.
suponiendo que este cuenta vueltas indique 1010, si la rueda extrema derecha de las unidades avanza uno pasara de 0 a 1, sin afectar
a la rueda que esta a su izquierda, por lo que el numero binario que sigue sera 1011. cuando la rueda de las unidades vuelva a
cambiar, esta vez de 1 a 0, hara que la rueda vecina izquierda que estaba en 1 pase a 0, esto a su vez obliga a que la rueda vecina 
izquierda que estaba en 0 cambie a uno, lo cual no afectara a la rueda vecina izquierda de la misma. entonces 1011 sigue 1100, etc,
en la figura 1.4 puede verificarse con este metodo la generacion de la sucesion de binarios del 0000 a 1111.

##**¿Cuantos bits se necesita por cada digito decimal a representar?**
El numero decimal 109 de 3 digitos, resultan aproximadamente 7/2=2,5 bits por cada digito decimal.
512d=1000000000b o sea 10bits para representar 3 digitos decimales :10/3=3,3 bits por cada digito decimal.
con 2 bits se forma 4=2^2 combinaciones binarios (00 11 10 11). con 3 bits se forman 8=2^ combinando binarios (000 001
010 011 100 101 110 111). en la figura 1.4 de la seccion 1.2 aparecen las 16=2^4 combinaciones binarios que se forman con 4 bits.
O sea, que el exponente de dos indica la cantidad de bits que se necesita en uno, el numero de combinaciones se duplica.

es importante recordar siempre que 2^10=1024, numero cercano a 1000 = 10^3 (1K)
EL exponente diez de dos indica que con 10 bits puede formarse 1024 numeros o combinaciones binarias distintas
(de 0000000000 a 1111111111b=1023d), numero cercano a 1000d que es el numero o combinaciones
que en base diez pue en el platillo derecho den formarse con 3 digitos decimales (de 000 a 999), siendo 3 el
exponente de diez.

por lo tanto, un numero aproximadamente igual de combinaciones distintas se forma con 10  bits en binario, y con 3
digitos decimal. osea unos 10 bits por cada 3 digitos decimales, lo que da 10/3 =3,33 bits por cada digito decimal.
ejercicio: cuantos bits se necesita para fotmar 10^6(1mega)numeros distintos.     respuesta 6x3,3 3=19,98 - 20bits
otra forma de hacerlo: dado que 2^10 , se tiene 10^3x10^3 ~ 2^10x2^10=2^20   Eo exponente indica que hacen falta 20bits

#**1.3 CONVERSION ENTRE BASES**
##**Conversion de una base cualquiera a base diez** 
se trata de una metodologia que de hevho hemos realizado anteriormente cuando evaluamos en base diez
los valores de las pesas con las cuales formamos numeros en otras bases. Asi, hemos realizado

64  8  1
1   5  5=[1x64 + 5x8 + 5x1]d=109d


64 32 16 8 4 2 1 d
1   1  0 1 1 0 1 b=[1x64 + 1x32 + 0x16 + 1x8+ 1x4 + 0x2 + 1x1]d=109d

16 1
6  Dh=[6x16 + 13x1]d =109d 












**regla:**
1. escribir sobre cada posicion su peso en decimal
2. sumar los prductos del peso decimal de cada posicion por el simbolo que aparece en ella (en hexa se debe
pasar los simbolos A, B, D, E, F a base diez). El resultado de essta suma sera el numero decimal buscado.

ejercicio: convertir a decimal el numero binario 10000   respuesta 16d
           convertir a decmial los numeros hexadecimales 109 y 100A
           convertir a decmial el numero octal 137

##**conversion de base diez a otra bese cualquiera por el "metodo pesas"**
como mse puso de relieve anteriormente, el hecho pesar con pesas de otras bases objetos cuyo peso es
conocido en base diez (figuras A1.3, A1.5, A1.7)permite determinar en octal, binario etc. Los simbolos
que representan en estas bases el peso de dichos objetos.
O sea que el metodo de simular que se pasa un bojeto, cuyo peso se conoce en base, diez con pesas de una
cierta base cuya magnitud se estima en base diez permite convertir un numero en base diez a otra cualquiera.

##**Regla para pasar un numero decimal a binario:**(no se requiere realizar dibujo alguno)
a. dado el numero a convertir, se parte de la pesa binaria que en base diez tiene un valor igual a dicho numero.o que
presenta el valor menor mas proximo al mismo; t apartir de este valor se escriben en base diez los sucesivos valores
decrecientes de las pesas binarias hasta el valor uno, siendo cada valor la mitad del anterior.
B. se coloca un uno debajo del primer balor determinado en el paso anterior. A este valor decimal se le sumara el valor
pesa que sigue a la ultima que se analizo el resultado alcanzado igual o es menor que el numero decimal a convertir,
se coloca un uno debajo del valor de esa pesa; y si ese resultado supera dicho numer se coloca un cero, para indicar
que esa pesa no se usa para balancear.
c. Los unos y cero asi determinado de izquierda a derecha son los bits del numero binario buscado

**Ejemplo**: convertir el numero 284d binario
a.=> 256 128 64 32 16 8 4 2 1 d 
b.=>   1   0  0  0  1 1 1 0 0 b    c.284 = 100011100d
en el paso a. se comenzo con la pesa del valor 256, que es la menor en relacion con 284. siendo que la de 512 lo supera.
el paso b. comienza escribiendo un uno debajo de 256. sumando el valor 128 que le sigue daira 256+128=384>284.
por lo que se coloc 0 debajo de 128. Lo mismo ocurre si intentamos sumar al 256 ya sea 64 o 32, por lo que tambien
escribimos un cero debajo del 64 y del 32, para indicar que no se han usado estas pesas. Con el paso 16. Con el peso 8
=272<284 (siendo que aun faltan equilibrar 284-272=12), por lo que escribimos un uno debajo del 16resulta 256+16 
resulta  272+8=280<284 por lo que tambien se escribe un uno debajo del 8. resultan equilibrar 284-280=4, lo cual se
consigue con la pesa de ese valor, escribiendose un uno debajo del 4. Dado que se ha equilibrado el 284 con las pesas
indicadas con un uno, no se usaran la pesas de 2 y 1,colocandose un cero debajo de cada uno de esos valores.
**Verificancion: siempre** es factible determinar si el resultado de una conversion esta bien, realizando el pasaje inverso a
base diez del numero binario hallado, segun la regla antes indicada:

256 128 64 32 16 8 4 2 1 d
1     0  0  0  1 1 1 0 0 b=(1x256+1x16+1x8+1x4)d=284d se verifica que la conversion fue bien hecha

**ejercicio**  convertir 100d a binario     respuesta:1100100b
con el presente metodo formar los numero binarios del 0 al 15, y verificar su concordancia concordancia con la fig 1.4.
 ##**Metodo para pasar de base diez a hexadecimal:**
a. Dado el numero a convertir, se parte de la pesa hexadecimal que en base diez tiene un valo igual a dicho numero, o que 
presenta el valor menor mas proximo al mismo; y a partir de  este valor se escriben en base diez los sucesivos valores
decreciente de las pesas hexadecimales a traves de siguiente ejemplo representativo.
b. Repitiendo la metodologia de las pesas desarrollada en relacion con la figura A1.7,sistematizaremos la forma 
de hallar os digitos hecadecimales atraves del siguiente ejemplo representativo.

**EJEMPLO:** convertir el numero 2574d a hexadecimales
a=> 256 16 1d
b.   A   0 Eh

en el paso a, no se pudo usar ninguna pesa de valor 4096d, por lo que se comenzo con las de valor 256d que es la menor
en relacion con 2574d. para el paso b, si usamos 10d= a pesas de 256d habremos equilibrado 10x256=260<2574(de
haber puesto 11=b pesas de 256. faltan equilibrar 2574
-2560=14 si se probara equilibrar con pesos hexadecimales que valen 16, bi seria posible colocar ninguna 
(cero), pues si se pusiera una, se tendria 2560+16=2576 excediendose el numero 2574, por lo que debe escribirse 0 pag 142

debajo del 16. Los 14 que falta equilibrar se consiguen con 14d = Eh pesas de valor uno, debi�ndose escribir **E** debajo del 1

En definitiva resulta 2574d = A0Eh.

**Verificaci�n**:

**256**  **16**  **1**
     
..A.. 0...Eh =(10x256 + 0x16 + 14x1)d = 2574d         Se verifica que la conversi�n fue bien hecha.

**Ejercicio**:   convertir 45056d a hexadecimal >>>>>>>>>  Respuesta: B000h 

#Otros m�todos para convertir de base 10 a otra base cualquiera

##*M�todo de las divisiones sucesivas por la base a la que se quiere pasar:*

**1.** Dividir por el valor decimal de la base el n�mero decimal a convertir.

Idem el cociente asi obtenido.

Idem hasta obtener un cociente menor que divisor


**2.** Este �ltimo cociente y los restos de las divisiones efectuadas, constituyen�, en ese orden, el n�mero buscado.


##Ejemplos                 
(la justificaci�n de este m�todo se da en la Unidad 4 de la presente obra)

**a.** Convertir a binario los n�meros decimales 13 y 12 

      13 | 2__                            
          
        1   6 |2__ 
             
             0   3|2__
                 
                 1  1     =  1101(base 2) = 13(base 10)



      12| 2__
       
        0   6 |2__
             
             0   3|2__
                 
                 1  1     =  1100(base 2) = 12(base 10)



**b.** Convertir a hexadecimal el n�mero decimal 16140



      16140 |16__
         
       0140   1008  |16__
                     
        12=C   48      63  |16__
                           
                0=0    15=F  3=3      = 3F0C(base 16)= 16140(base 10)


**EJERCICIO** : Usando el presente m�todo pasar el n�mero 109d a binario y hexadecimal


#*�C�mo se pasa directamente de binario a hexa, y viceversa?*
Como se anticip� al tratar el sistema hexadecimal, �ste se usa para pasar de una forma sencilla de binario a hexa y viceversa **usando en pantalla o en el papel la cuarta parte de los s�mbolos de los que se utilizan en binario**, siendo que en el interior de un computador s�lo se puede representar el sistema binario.

###*Regla para pasar de binario a hexadecimal:*

1. A partir del bit extremo derecho del n�mero binario, dividirlo en cuartetos, agregando ceros a la izquierda si se necesita.

2. Asignar a cada cuarteto los pesos 8-4-2-1 en forma escrita o mentalmente.

3. Sumar en base diez los pesos de cada cuarteto correspondientes a los bits de valor 1, o sea hallar su valor en base diez.

4. El n�mero resultante de cada suma as� efectuada en cada cuarteto seg�n el paso anterior, ser� el digito hexadecimal correspondiente a ese cuarteto, siendo que si dicho n�mero es del 0 al 9 ser� el mismo en hexa; y si el mismo es 10 el digito hexadecimal ser� A, si es 11 ser� B. si es 12 ser� C, si es 13 ser� D, si es 14 ser� E, si es 15 ser� F.


##Ejemplo: 

convertir a hexadecimal el n�mero binario 110011100

Pasos 1. y 2.    ........   **8421** .... **8421**...... **8421**

   ................................0001.......1001........1100

............................... ----- .... ----- ... ------ =  19Ch

pasos 3. y 4. ............. **1**.......8+1=9.....8+4=12=C


**Ejercicio**: 

Convertir a hexa 1010000011110111   y    1100011101     ( respuesta: A0F7h y 31Dh)

Con un m�todo semejante y formando tr�os, pasar 1101101b a octal (Respuesta: 155o)

___
�      En caso que los restos decimales superen el valor 9, (como puede ocurrir cuando se pasa de decimal a hexa) se debe convertir dichos restos al s�mbolo equivalente de la base en cuesti�n( por ejemplo 10=A; 11=B; etc.)



pag 143


**REGLA PARA PASAR DE HEXADECIMAL A BINARIO:**

1. Separarlos d�gitos hexadecimales de modo de poder formar debajo de uno de ellos un cuarteto binario a determinar de pesos 8-4-2-1. Estos n�meros pueden escribirse o ser imaginados mentalmente. 
2. Convertir cada d�gito hexadecimal de 0 a F a decimal (ser�n iguales del 0 al 9), y �ste n�mero a su vez en un cuarteto de pesos 8-4-2-1 por el m�todo de las pesas ya visto.
3. El conjunto de cuartetos as� formados constituir�n el n�mero binario buscado.


**EJEMPLO:** Convertir a binario el n�mero hexadecimal A07

paso 1   ..............A...............0................7h

 ............... ......**8421**...........**8421**..........**8421**d

paso 2 ...........1010..........0000...........0111b        ............O sea A07h = 101000000111b

.....................A=10=8+2................7=4+2+1

**Ejercicio:**  Convertir a binario 10h .........................................................Respuesta: 00010000b


#A1.4|| OPERACIONES ARITM�TICAS CON N�MEROS BINARIOS NATURALES


##*De qu� forma la UAL suma dos n�meros?*

>En cualquier base num�rica pueden definirse las distintas clases de n�meros (naturales, negativos, imaginarios, reales, etc.), y todas las operaciones que empleamos en base diez. Estas presentan las mismas propiedades conocidas en base diez, pueden aplicarse los mismos algoritmos que conocemos para realizarlas con n�meros de varios d�gitos.

>Comenzaremos con la suma de binarios

>Si bien pueden sumarse manualmente varios n�meros binarios ordenados uno debajo del otro, interesa especialmente operar dos n�meros binarios por vez, como lo hacen las unidades aritm�ticas de los microprocesadores y las calculadoras de bolsillo.

>Para sumar en binario se debe tener presente que en la sucesi�n de los n�meros naturales: 0, 1, 10, 11, ....; si se suma cero a un numero debe resultar el mismo, y si se suma uno debe obtenerse el siguiente.

>Esto se verifica en las siguientes sumas elementales, que son las variantes que tienen lugar en la suma de dos n�meros binarios:

0+0=0  

1+0=1   

0+1=1  

1+1=10 

10+1=11


Efectuar    110110100 + 11010110

...................................................................1 1 1 1....1

...................................................................1 1 0 1 1 0 1 0 0

................................................................+... 1 1 0 1 0 1 1 0


........................................................... -----------------------------


................................................................ 1 0 1 0 0 0 1 0 1 0

.....................................................................i h g f e d c b a


La suma se ha realizado, posici�n por posici�n, como se detalla:

**a.**.. 0 + 0 = 0

**b.**.. 0 + 1 = 1

**c.**.. 1 + 1 = 10 --------------> se escribe el 0 y "me llevo 1" de acarreo ("carry") a la posici�n siguiente   

**d.**.. 1 + 0 + 0 = 1 + 0 = 1

**e.**.. 1 + 1 = 10 --------------> (�dem c.)

**f.**.. 1 + 1 + 0 = 10 + 0 = 10 ----(�dem c.)

**g.**.. 1 + 0 +1  = 10 -------------(�dem c.)

**h.**.. 1 + 1 + 1 = 10 + 1 = 11 ----se escribe 1 y "me llevo 1" a la posici�n siguiente. 

**i.**.. 1 + 1 = 10

p�gina 144

En la resta indicada�, toda vez que se "pide 1" si la siguiente posici�n del minuendo vale 1,
�ste pasar� a ser 0, dado que (1-1=0) como indica el regl�n superior.Si la siguiente es 0 pasar� 
a ser 1(10-1=1), debi�ndose nuevamente "pedir 1" a la subsiguiente, que tambi�n pasar� a ser 1 si es 0, 
y as� sucesivamente. Si hay ceros en el minuendo se transformar�n en unos, hasta llegar a un 1 que pasar� a ser 0.

El procedimiento de "pedir prestado" no se emplea en los circuitos de un computador, por la complejidad y lentitud que ocasionar�a.
En su reemplazo se usa el m�todo de **sumar al minuendo el complemento al m�dulo del sustraendo,** cuyos pasos se indica a continuaci�n,
y cuya justificaci�n se trata en detalle en el **Complemento para Enteros y Punto Flotante"** que est� al final de esta Unidad.


##*�De qu� forma se realiza manualmente una resta de binarios?*

La tabla de restar binaria es sencilla:

0 - 0 = 0

1 - 0 = 1

1 - 1 = 0

0 - 1 = 1  -----> y se "pide 1" a la siguiente; o sea se hace 10 - 1 = 1


..............001 ..01..0

..........10~~1~~~~1~~~~0~~0~~1~~~~0~~010

-- ............11100101

.. -----------------

 ...........10010101101

##*�C�mo efect�a la UAL una resta sin pedir prestado, mediante una suma?*

Realizaremos la misma resta anterior sin pedir prestado, mediante **una sola suma** que hace la UAL




..........10110010010

-- ......00011100101

.. -----------------

........111......1....1

..........10110010010

. + ....11100011010

.. -----------------

 .......1 **10010101101**
 
 (El primer 1 se descarta)

 (El resultado est� en negrita recuadrado)
 
 **Regla**

 1. El minuendo se sumar� sin modificaci�n.

 2. Se invierten cada uno de los bits del sustraendo, y el n�mero as� formado es el segundo operando.

 3. Se escribe un uno para ser sumado en la posici�n de las unidades.

 4. Sumar los tres n�meros indicados en 1, 2 y 3 , y descartar el 1 que est� fuera del formato de los n bits que se restan.
 
 Los bits restantes a la derecha del bit descartado constituyen el resultado de la resta.
 
 ##*�C�como se multiplican y dividen manualmente n�meros binarios naturales?*
 
 La tabla de multiplicar es muy sencilla, al igual que la operatoria manual (que no se usa en c�lculos autom�ticos): se repite el multiplicando desplazado a la izquierda, conforme a la posici�n que ocupen los unos del multiplicador. Luego se realiza la suma de los sumandos as� ordenados.
 
 0x0=0

 0x1=0

 1x0=0

 1x1=1
 
 
..........11011

X ...........101

.. ----------

..........11011

.....11011

.. -----------

...1 0000111


 
     111011 | 110_____                           
    -110         1001
	 ____
     0010
    - 000
	 _____
       0101
	-    110
	     _____
		  101
		  
La divisi�n se ha realizado con el m�todo de las diferencias sucesivas, siendo que cada sustraendo se obtiene: multiplicando por 1 al divisor si este �ltimo es menor o igual que el resto parcial en cuesti�n, o por 0 si el mismo es mayor que dicho resto.


Es imporatente se�alar que cada vez que se multiplica o divide un n�mero entero binario  **por la base 10b = 2d al igual que en base diez se agrega o se quita un cero**, respectivamente:


(1011x10)b = 10110b           ...........................................................(10x10)b = 100b

(10110 x 10 x 10 = 10110 x 100)b = 1011000b(1110 : 10)b = 111b

(101011000 0 : 1000)b = 1010110b




---------------
� Es conveniente comparar las similitudes de la resta efectuada con restas en base diez, como : 880010010 - 5349809)D 




1-132
----------------------------------------------------------------------------------------
				
				INSERTAR FIGURA 1.94
	
	Existen 4 __UE__, siendo que las dos que contienen una UAL operan al doble de la frecuencia del procesador, o sea
	que en medio ciclo completan la operac�on, siendo por ello posibles hasta 6 operaciones por ciclo. Ellas son:
	__UE0__ dedicada a uops-R "store", y __UE__1 para uops-R "load", a raz�n de una uop-R por ciclo.
	__UE2__: en la primer mitad de un ciclo puede operar enteros en una UAL, o una instrucci�n de transferencia en 
	punto flotante; y en la segunda mitad de dicho ciclo puede operar otra vez enteros en la UAL de dicha __UE__.
	__UE3__: en la primer mitad de un ciclo puede operar enteros en una UAL, u operar (en el coprocesador) todas las
	operaciones aritm�ticas en un punto flotante, pero no las de transferencia, o cualquier operaci�n SIMD, o llevar a cabo
	una uop-R de salto; y en la segunda mitad de un ciclo puede operar nuevamente enteros en la UAL de dicha __UE__.

	Para uops-R load/store existe un Buffer Conversor compartido en "HT" por los dos "threads", que es una memoria
	totalmente asociativa (definida al trata cach�s), que convierte direcciones a direcciones f�sicas de memoria.
	Despu�s de haberse realizado la operaci�n ordenada por cada uop-R en la __UE__ correspondiente, las uops-R
	pasan a un buffer de reordenamiento, que hace de intermediario entre la __UPRE__ y la __UR__. Este buffer se parte en 
	mitades si hay dos "threads".
	La __UR__ retira las uops-R en orden en forma alternada para cada "thread".
	Luego que las uops-R ejecutadas se retiran, los resultados pasan desde registros hacia el cach� de datos L1. 
	Este es un cach� asociativo de 4 v�as con l�neas de 64 bytes, que siempre escribe "write-through" en el cach�
	asociativo L2 de 8 v�as con l�neas de 64 bytes, con 128 bytes por l�nea. Este Xeon tiene un cach� similar L3.
	Los cach�s L2 y L3 operan con direcciones f�sicas y el L1 con virtuales , pero con tags f�sicos.

	~~~
	De la descripci�n anterior resulta, que dos "thread" que se est�n ejecutando en paralelo comparten (en principio
	por partes iguales) la mayor�a de los recursos f�sicos de un �nico procesador, ya sea por partici�n de los mismos o
	por alternancia (en un ciclo reloj uno y en el siguiente el otro)'y no se trata simplemente que se ejecuta un "thread"
	y cuando �ste se detiene por alg�n motivo se pasa a ejecutar el otro.
	~~~