# 1.3 Hardware del computador

**�Qu� es el hardware?**

 **Hardware** son los medios f�sicos (equipamiento material) que permiten llevar a cabo un proceso de datos, conforme lo ordenan las instrucciones de un cierto programa, previamente memorizado en un computador. 


En ingl�s duro; es hard, y hardware: significa ferreter�a.

El hardware de un computador es la totalidad f�sica, conformada por todos los componentes de su equipamiento: circuitos electr�nicos (hoy microcircuitos contenidos en chips cuadrados con patas para conexi�n), plaquetas que los soportan, cables o caminos conductores (buses) que los interconectan, mecanismos, discos, motores, gabinetes, tornillos, pantallas, teclas, etc.

Con estos elementos se construyen los distintos bloques funcionales del hardware: procesador, memoria, perif�ricos, interfaces, etc.

En la figura 1.5 se indican  elementos constituyentes  del hardware correspondientes a la plaqueta principal de una PC, conocida como **motherboard** cuyos bloques principales se ir�n tratando.

 Salvo detalles de la motherboard y otros menores, los **conceptos y definiciones que siguen son v�lidos para el funcionamiento de**  **cualquier**  **computador**. Como se indica en el prefacio, **todos los computadores con un solo procesador funcionan b�sicamente de la misma forma que una PC actual**. Cualquier procesador actual (Pentium, Motorola, Risc, etc) o anterior, funciona sobre la base del llamado  **modelo de Von Neumann** planteado en 1946, cuyos enunciados se dan en la secci�n 1.14.

**�Cu�les son los bloques constituyentes b�sicos del hardware de un computador y qu� funciones cumplen?**

En lo que sigue, si bien se parte de la fig. 1.2 es esencial tener presente lo dicho en relaci�n con la fig,1.3   

La comprensi�n de las funciones que cumple cada una de las partes que conforman el proceso de datos de la figura 1.2, permite entender c�mo funciona en esencia cualquier computador,  dado que cada trabajo que realiza un computador siempre es un proceso de datos, que tiene la particularidad  de ser autom�tico.

En un proceso autom�tico (figura 1.6) tambi�n est�n presentes los cuatro subprocesos constituyentes:

**Entrada - Memorizaci�n - Procesamiento - Salida** que llevan a cabo los bloques a definir (perif�rico de entrada  - memoria  principal - unidad de  procesamiento - perif�rico de  salida), siendo que en un computador existen diversas posibilidades para la entrada o salida de datos. Las flechas indican movimientos semejantes en ambas figuras.

Los bloques se comunican el�ctricamente entre s� a trav�s de caminos formados por un conjunto de cables o l�neas conductoras que constituyen un  **bus**. **Un mapa de buses actual est� en la fig 1.80**.

A los fines did�cticos de mantener los cuatro bloques citados en el orden dibujado en las figuras 1.2 y 1.3, aparecen repetidos dispositivos que pueden actuar tanto para la entrada como para la salida de datos (las unidades de disquete y disco, y el m�dem). El bloque **I** se refiere a una **Interfaz** intermediaria, necesaria para conectar su perif�rico, la cual contiene los registros **ports** ( **Ver secci�n 1.10** ).

En l�neas muy generales, en las figuras 1.6 y 1.7 se supone lo que sigue. Un disco de la unidad de disco r�gido provee un  programa, cuyas instrucciones pasar�n a trav�s de buses hacia la memoria. Los datos llegar�n tambi�n a trav�s de buses a la memoria, provenientes del teclado.

Luego, dichas instrucciones son ejecutadas, una por vez. A tal fin primero cada una por un bus llega a un  registro de  instrucci�n (Rl) de la Unidad Central de Procesamiento (Procesador), donde permanece mientras se ejecuta, para  que la Unidad de Control interprete qu� operaci�n ordena ella.

A continuaci�n, a trav�s del mismo bus, el dato a operar por dicha instrucci�n llega desde memoria a un registro acumulador AX del procesador, antes de ser operado (conforme a la operaci�n ordenada) en la Unidad Aritm�tica, a fin de obtener un resultado. Este puede sustituir en el registro AX al dato ya operado, y luego pasar a memoria -nuevamente a trav�s del bus citado si una instrucci�n as� lo ordena.

Si por ejemplo se quiere enviar dicho resultado al exterior para ser visto en pantalla, � para ser guardado en el disco r�gido o en un disquete, ello se consigue mediante la ejecuci�n de instrucciones que as� lo ordenen.

En la figura 1.6 se ha reemplazado al id�neo de la figura 1.2 encargado de obtener de la memoria en el orden establecido cada instrucci�n y ejecutarla por un  circuito denominado  **Unidad de Control**,**(UC)**, capaz de realizar sus mismas acciones b�sicas, pero millones de veces m�s veloz. Dichas acciones formaban parte de una secuencia siempre repetitiva:

�  obtener de la memoria la pr�xirila instrucci�n que corresponde ejecutar,

�  localizar los datos a operar (en la memoria principal, o en un registro como AX u otro, seg�n se ordene)

�  ordenarle al circuito de la Unidad Aritm�tica  que realice con dichos datos la operaci�n indicada,

�  guardar el resultado en un registro acumulador o en memoria principal

Por lo tanto:

 La UC tiene a su cargo el secuenciamiento de las acciones necesarias que deben realizar los circuitos involucrados en la ejecuci�n de cada instrucci�n, seg�n el c�digo de la misma; y tambi�n tiene a su cuidado el orden de ejecuci�n de las instrucciones de un programa, conforme como �ste fue establecido 


La calculadora de la figura 1.2 se ha dividido en dos porciones: una que contiene los circuitos de c�lculo, que denominaremos **Unidad Aritm�tica L�gica** ( **UAL** o ALU en ingl�s), y otra constituida por el **registro acumulador** designado **AX** , para datos y resultados (que en la calculadora es su registro visualizable). La UC  ordenar�  mediante se�ales el�ctricas transmitidas  por  cables, las operaciones (suma, resta, multiplicaci�n, etc.) que debe realizar la UAL. Esta forma de control electr�nico directo reemplaza a las lentas teclas de una  calculadora de la figura 1.2. Asimismo, el hecho de tener un registro separado, permite a la UC entrar al mismo datos a operar en forma electr�nica directa, mediante cables que  llegan a �l, sin que  tampoco se requiere teclas para ello.

 La **UAL** sirve para realizar las operaciones aritm�ticas o l�gicas que le ordena la UC, siendo auxiliada por registros acumuladores para guardar transitoriamente resultados datos y resultados. 


Mientras que la UC es la encargada de ordenar operaciones de lectura-escritura de registros y de memoria, as� como de las operaciones que debe realizar la UAL, �sta es pasiva: no puede emitir orden alguna.

Por lo tanto, la UAL **no** ejecuta instrucciones. O sea, no puede ordenar las operaciones correspondientes a los pasos que requiere la ejecuci�n una instrucci�n. S�lo realiza uno de ellos: la operaci�n aritm�tica o l�gica que la instrucci�n ordena, cuando as� lo requiere la UC. Mediante una operaci�n de la UAL, a partir de uno o dos n�meros (materia prima) se puede obtener un n�mero (resultado) que antes no exist�a.

Conforme al  proceso de  la  figura 1.2, no debe perderse nunca de vista  que el  conjunto UAL Acumulador forman de hecho una calculadora con funciones semejantes a una de bolsillo, siendo la UC la encargada de manejarla, seg�n la operaci�n ordenada.

La palabra &quot;L�gica&quot; de las siglas UAL puede llevar a equ�vocos, en el sentido de suponer inteligencia. Como se ejemplifica en 1.8, las operaciones &quot;l�gicas&quot; de la UAL son las operaciones AND, OR, negaci�n, etc.

Se denomina **Unidad Central de Proceso** ( **UCP** o **CPU** en ingl�s) al conjunto formado por:�  la Unidad de Control�  la Unidad Aritm�tico-L�gica�  los registros (como el AX, RI y otros) usados durante la ejecuci�n de cada instrucci�n. 

La UCP es el bloque donde se lleva a cabo la ejecuci�n de las instrucciones. Hacia ella se dirigen las instrucciones que ser�n ejecutadas (una vez que la UC decodifique su c�digo), y los datos para ser operados por la UAL a la par que de la misma salen resultados generados por la UAL.

Como se ver�, adem�s del registro acumulador definido, en la UCP existen otros registros necesarios para la ejecuci�n de las instrucciones, que se ir�n definiendo.

 La UCP de una microcomputadora -como lo es una PC- est� contenida en el chip **microprocesador** central (por ejemplo, el 80286/386/486, Pentium, 68000, Alfa, Power PC, etc.). 


Los t�rminos UCP, microprocesador y procesador suelen ser sin�nimos.

Al igual que el dep�sito fabril de la figura  1.3, la memoria principal o central o interna almacena materia prima (datos), instrucciones, y los resultados del proceso realizado en circuitos electr�nicos. O sea:

 La **memoria principal** ( **MP** ) almacena instrucciones de programas, que pr�ximamente ser�n ejecutadas en la UCP, y los datos que ellas ordenan procesar (operar); as� como resultados intermedios y finales de operaciones sobre datos recientemente llevadas a cabo en la UCP. 


Vale decir, los datos que se procesan  y el programa que se ejecuta para ese proceso deben estar en MP. Cada programa comparte la MP con sus datos,  pero las instrucciones est�n en una zona y los datos en otra.

Esta inform�ci�n queda almacenada temporariamente mientras se opera con ella, pudiendo ser luego reemplazada por otras instrucciones a ejecutar, y datos que �stas procesan. Tambi�n existen programas que residen en MP en forma permanente, como los del sistema operativo, que facilitan el uso de un computador, cuya ejecuci�n se alterna con la de programas de los usuarios.

Las instrucciones y datos a procesar que pasan a la UCP llegan a la MP desde el exterior del computador (figura 1.6); y los resultados que llegan a MP provenientes de la UCP deben luego pasar al exterior:

En una **operaci�n de entrada** , la MP es el destino de instrucciones y datos provenientes del exterior (que ingresan a trav�s de unidades de discos o disquetes, teclado, mouse, m�dem, u otros).

Asimismo, en una **operaci�n de salida** , la MP es el origen de resultados que deben salir al exter�or (a trav�s del monitor, impresora, unidades de discos o disquetes, m�dem, u otros).

T�picamente los programas llegan a MP para ser ejecutados provenientes de archivos en discos o disquetes. los datos a procesar pueden llegar a MP provenientes del exterior desde cualquier perif�rico.

 Los dispositivos que se encargan de entrar desde el exterior datos o instrucciones hacia el computador, o dar salida de resultados del computador al exterior, se denominan **perif�ricos** o **unidades de entrada/salida**. 

Para tal fin su funci�n principal es **convertir** datos externos en internos en las operaciones de entrada, o a la inversa en las operaciones de salida. Un perif�rico oficia de frontera entre el exterior y el interior de un computador para la conversi�n de se�ales. Del mismo modo (figura 1.1), nuestros ojos, o�dos, piel, etc., sensan se�ales externas y las transforman en se�ales el�ctricas que van hacia nuestro cerebro o m�dula. Nuestras  cuerdas vocales y cavidades asociadas permiten un proceso opuesto para la comunicaci�n con el exterior.

Hay que diferenciar el perif�rico de lo que es su exterior. As�, para los perif�ricos unidades de discos (o disquetes), el exterior  est� constituido por el disco para la impresora el exterior es el papel, para el m�dem es la l�nea telef�nica, etc.

Usualmente, en  un  sistema  de  computaci�n personal existe un  conjnnto  de  perif�ricos (teclado,mouse, y otros) construidos s�lo para entrar del exterior datos o instrucciones, que se escriben en MP. Perif�ricos como el monitor con pantalla y la impresora s�lo pueden dar salida a datos o resultados. En cambio, las unidades  de discos o disquetes y el m�dem son perif�ricos que operan ya sea para entrada  o salida,  pudiendo llevar  a cabo una de estas operaciones por vez. Por tal motivo, en el esquema de la figura 1.6 aparecen  repetidos en la entrada y salida, aunque en realidad se trata siempre de la misma unidad actuando de una forma u otra, como ya se expres�.

La denominaci�n perif�ricos proviene de su posici�n, vinculada al mundo exterior en relaci�n con la **porci�n central** o **interna** , constituida por el microprocesador (UCP) y la memoria principal.

Por las razones que se exponen en la secci�n 1.10, un perif�rico no se conecta directamente a la porci�n central, sino por intermedio de una interfaz circuital (indicada con la letra **I** en la figura 1.6), que en una PC en general est� contenida en una plaqueta que se inserta en un z�calo apropiado (figuras 1.60 a 1.65).

Debe consignarse que la UC **no** gobierna directamente a los perif�ricos mediante l�neas que llegan a ellos, sino que la UCP ejecuta un subprograma preparado para cada perif�rico, merced al cual desde la UCP llega a la interfaz del perif�rico cada comando que ordena a la electr�nica de �ste qu� debe h�cer

Los perif�ricos como el teclado, el monitor, la impresora, el graficador (plotter) y cualquier otro que permita la comunicaci�n directa mediante s�mbolos usados por los hombres, se denominan terminales. Las unidades de disco (magn�tico u �ptico), de disquete, de cinta son perif�ricos conocidos como **unidades de almacenamiento masivo** ,tambi�n denominadas **memorias auxiliares** o **externas** o **secundarias**.

Distintos circuitos de un computador se comunican entre s� mediante un conjunto de conductores (cables o l�neas) que interconectan el�ctricamente las patas  de los chips que contienen dichos circuitos.

As�, las l�neas conductoras de electricidad que salen de las  patas del chip de un microprocesador para transmitir direcciones, instrucciones, datos y resultados, constituyen el denominado **bus local**.

| Un bus de un computador es una estructura de interconexi�n para la comunicaci�n selectiva entre dos o m�s m�dulos de un computador, a fin de poder transmitir informaci�n entre dos m�dulos por vez. |
| --- |

En general, en un bus encontramos l�neas para direcciones, datos, y se�ales  de  control (a veces denominadas bus de direcciones, bus de datos, y bus de control, respectivamente Ver figura 1.8).

Las **l�neas de  direcci�n** , conducen de UCP a MP cada combinaci�n de unos y ceros que indica d�nde localizar instrucciones o datos en MP. Es unidireccional.

Las **l�neas de datos** , en cada lectura de MP conducen de �sta hacia la UCP tanto datos a operar como instrucciones; y en una escritura conducen desde la UCP hacia MP datos resultantes. Son pues, l�neas bidireccionales. Las l�neas  de control, son unidireccionales individuales para que la UCP d� �rdenes c�mo leer o escribir MP y para que ella reciba se�ales como la que origina la MP para inicar lectura efectivizada-

Un bus presente en las PC es el bus **PCI** (Peripheral Component Interconnect) creado por Intel, al cual a trav�s de z�calos (figura 1.5)se conectan plaquetas para conexi�n de perif�ricos, y de otros buses. Este bus tambi�n emplea las tres clases de l�neas citadas. No est� vinculado directamente al procesador central.

En la secci�n 1.13 se detalla este bus, el **USB** y el **SCSI** , y en la figura 1.80 se da un mapa de c�mo se comunican entre s� (como sugieren las figs 1.6 y 1.7) a trav�s de chips que hacen de &quot;puente&quot; entre distintos buses. **Las se�ales el�ctricas digitales se transmi en por las l�neas de un bus  como se indica en la fig 1.48**

Las figuras 1.7 y 1.6 son en esencia similares, salvo la ubicaci�n relativa de la UCP (m�s acorde  a la figura1.3), y que  los perif�ricos de entrada o salida (seg�n indica el sentido de las flechas) aparecen espacialmente en  un  mismo nivel  de proceso,  aunque  como se aclar�, por ejemplo una unidad de disco cuando act�a como perif�rico de entrada no puede  simult�neamente operar para salida, y viceversa.

En  ambas figuras se  han  respetado los  or�genes y destinos de los movimientos.

Otra  diferencia  menor,  pero importante, es que por la forma en que se comunican los buses de la figura 1.7, es factible que datos o instrucciones que entraron  por un perif�rico, en lugar de pasar directamente a memoria principal, primero pasen a un registro de la UCP, y de �ste a memoria, resultando una triangulaci�n.

Esto es lo que sucede en  una  PC cuando se entran datos desde el teclado, el mouse, o el disco r�gido. Asimismo, en una operaci�n de salida, un resultado en memoria puede pasar a un registro de la UCP, y desde �ste ir a un  perif�rico. As� se realiza  una impresi�n  o un almacenamiento en el r�gido en una PC.

En cambio, la unidad de disquete env�a o recibe informaci�n directamente a memoria, sin triangulaci�n. Estas  alternativas  de triangulaci�n para entradas y salidas no se han dibujado, para no complicar la figura. En la 39 mother de una PC existen chips que integran distintas funciones, constituyendo el chipset

**�C�mo puede resumirse el funcionamiento b�sico de un computador?**

|
- Los datos y las instrucciones del programa que los procesar�, deben llegar a MP desde perif�ricos. Cada instrucci�n est� codificada mediante una combinaci�n de unos y ceros, que constituye su c�digo.
- La UC localiza en MP la instrucci�n que debe ser ejecutada (como se explica en la siguiente pregunta), para que su c�digo llegue a la UCP, donde la UC determinar� qu� ordena ese c�digo.
- Dicho c�digo permite: localizar los datos que operar� la UAL, la operaci�n que debe realizar la UAL, d�nde guardar el resultado, y d�nde localizar la pr�xima instrucci�n en MP.
- Se vuelve al paso 1.
 |
| --- |

Si una instrucci�n ordena una transferencia de un dato desde la UCP hasta la plaqueta donde est� conectado un perif�rico, tendr� lugar una operaci�n de salida, encarg�ndose el perif�rico de llevar los datos al exterior (representado por la pantalla del monitor, un disco, etc.). Igualmente existen instrucciones para llevar un dato que entr� desde un cierto perif�rico hasta la UCP, mientras se desarrolla una operaci�n de entrada.

| Se debe tener siempre presente que las instrucciones son interpretadas (decodificadas) por la UC; luego de lo cual la UC ordena encaminar los datos hacia la UAL, y la operaci�n que �sta debe realizar con los datos. 

**�Qu� registros de la UCP falta definir para realizar las primeras pr�cticas con el programa Debug a fin de operar en el interior de un computador?**

En la figura 1.2 el id�neo ; recuerda, en una zona de su cerebro, cu�l instrucci�n ejecut�, para luego leer la instrucci�n siguiente en la planilla. Esta sirve para escribir qu� ordena realizar cada instrucci�n.

Si por razones de velocidad el id�neo ; s�lo pudiera leer una sola vez cada instrucci�n de la planilla -como ocurre con la UC- deber�a registrar en su mente o en alg�n papel dicha informaci�n.

Para tal fin, como antes se trat�, el c�digo de cada instrucci�n le�do en memoria principal (MP) queda registrado en el registro de instrucci�n (RI), para  que la UC determine qu� ordena el mismo y llevar una cuenta para poder ubicar en MP la instrucci�n a ejecutar.

Para localizar en MP la siguiente instrucci�n que sigue en orden de ejecuci�n, en la UCP existe registro muy  necesario para la UC, conocido como **contador de programa **(CP) o **registro de pr�xima instrucci�n**, que en el modelo de PC que operaremos con el Debug ser� el denominado registro puntero de instrucci�n ( **IP** - Instruction Pointer). El IP indica un n�mero, el cual permite localizar en una zona de memoria d�nde est� la instrucci�n a ejecutar. 

 Adem�s de los registros AX, RI e IP, definiremos un cuarto registro denominado registro de estado (RE), que contiene un conjunto de bits llamados indicadores (flags), los cuales pueden cambiar de valor luego de cada operaci�n que hace la UAL. Los flags  se usan en instrucciones de salto, esenciales para el proceso autom�tico de datos, pues permiten repetir muchas veces un mismo subprograma, o saltar de un subprograma a otro que ordena acciones diferentes. 

Tambi�n una calculadora com�n muestra, junto con el resultado de una operaci�n, otras indicaciones de inter�s,  que  pueden asimilarse a dichos  flags. As�, un  signo menos  que  aparezca  en  el visor adelante del resultado de una  resta, nos indica que el minuendo es menor que el sustraendo. La no aparici�n de este indicador de signo, implica que el minuendo es mayor. Asimismo, si el resultado de una resta es cero, significa que ambos n�meros son iguales. Otro indicador es el de resultado excedido.

Igualmente, la UAL luego de cada operaci�n aritm�tica  o l�gica que realiza, genera & 39 de estado del resultado:  si fue positivo o negativo, si fue cero o no, si como n�mero entero sobrepas� o no el m�ximo representable. Cada uno de estos si o no ; es un bit que se guarda en el registro de estado citado, actualizado por la UAL.