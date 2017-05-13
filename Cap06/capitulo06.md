# 1.6 USO DEL PROGRAMA DEBUG DEL DOS PARA VISUALIZAR EL INTERIOR DEL COMPUTADOR

## �C�mo se usa el Debug para escribir datos e instrucciones en memoria?
---

A continuaci�n se indican los pasos a dar para llamar al programa Debug desde el DOS (que tambien est� en Windows 98 y NT), y luego poder leer y escribir los datos e instrucciones como se plantea en la figura 1.15. El procedimiento sirve en general para leer o escribir la memoria principal de una PC.
En negrita aparece aquello que escribe el DOSQ (y que interesa a los fines did�cticos), y en cursiva may�scula lo que debe escribir el usuario (con la tipograf�a que sea). El s�mbolo (figura1.jpg "figura1.6") indica la tecla �Enter�.
Los n�meros que se tipean y los que aparecen en pantalla son hexadecimales, aunque como sabemos en el interior de un computador solo puede haber unos y ceros.

> C:\> DEBUG (figura1.jpg "figura1.6")
_

Un gui�n que aparece titilante debajo de la C, indica que el Debug est� listo para que a continuaci�n del gui�n se escriba un comando. Para leer o escribir la memoria se tipea la letra E (examinar) seguida de la primer direcci�n que se quiere leer o escribir. Por ejemplo, si se quiere conocer el contenido de posiciones de memoria a partir de la  5000 H, primero se tipea el comando E 5000 seguido de un Enter ((figura1.jpg "figura1.6")), con lo cual en la pantalla se ver�, por ejemplo, lo siguiente:

- E 5000 (figura1.jpg "figura1.6")	(tipeado por el usuario para examinar memoria)
> 309D:5000 1F.					(mostrado por el Debug)


Esto nos dice que la direccion 5000H(0101 0000 0000 0000) de memoria [^1] tiene por contenido la combinaci�n 1F H = 00011111. Esta combinaci�n es la que estaba almacenadaenla direcci�n 5000H en la PC que hemos utilizado, pero que otro dia, o en otra PC ser� distinta [^2]. Lo mismo vale para 309D si luego de leer la 5000H se quiere leer el contenido de la posici�n siguiente 5001H, no hace falta repetir el comando E. Basta con pulsar la barra de espaciado luego del ultimo valor leido -en este caso 1F- para que en pantalla aparezca el n�mero que guarda la posici�n 5001 (06 en est caso como aparece a continuaci�n).

-E 5000 (figura1.jpg "figura1.6") (Examinar memoria)
(figura2.jpg "figura2.6")

Del m�smo modo si se vuelve a pulsar la barra se conocer� el contenido de la posici�n 5002H, y asi de seguido para determinar contenidos de posiciones consecutivas de memoria. Por razones de claridad, aparecen hasta 8 lecturas de posiciones por rengl�n, y para no llenar la pantalla con numero, solo se muestra

---
[^1] Aunque esto por el momento no es relevante conviene aclarar que realidad se trata de una zona (segmento) de memoria con m�s de 6400 posiciones (Bytes), numerados con direcciones que van de 0000H hasta FFFFH. La direcci�n 0000G es la primer posici�n de este segmento de memoria, y no el cero de la memoria. La direcci�n de memoria donde comienza este segmento est� en relaci�n con el valor 309D que aparece en la izquierda de 5000. Dicho 0000 corresponde a la direcci�n de memoria 309D0 H (309D con el agregado de un cero,
conforme a la convenci�n para los 80x86 de Intel). Si a 309D0 le sumamos 5000H se tendria 359D0H = 0011 0101 1001 1101 0000 en binario (20 bits), que seria una direcci�n de memoria que esta 5000H posiciones despu�s de 309D. Puesto que las direcciones de memoria ejemplificadas son de 20 bits, significa que se trata de una memoria de 1 megabyte, como se deduce en la figura 1.14 (2^20 = 1 MB)
Este es el tama�o de memoria que "ve" el DOS. desde la direcci�n 00000000000000000000 = 00000 H hasta la 1111111111111111111 = = FFFFF H. Este tema se ver� en detalle al tratar este sistema operativo en la Unidad 3.
[^2] Conforme al modelo de 8 llaves "si-no� por celda de memoria. las mismas siempre est�n formando una combinacion de unos y ceros determinada. No es factible que no haya "nada" en una posici�n. Cuando se enciende un computador. en cada posmi�n se forma un n�mero al azar. que no tiene por que ser el 1F ejemplificado en esta obra.
---

una direcci�n a la izquierda de cada rengl�n. As�, luego de la 5000 no aparecer�n en pantalla 5001 a 5007 (que debe determirarse visualmente, como se�alan las flechas dibujadas con los valores), y luego aparece 5008
Entonces, si a partir de la indicaci�n anterior pulsamos repetidamente la barra de espaciado, se obtendr�a un vuelco de memoria del tipo siguiente (distinto para cada oportunidad y computador):
Cuando se quiere dejar de leer se pulsa Enter (figura1.jpg "figura1.6") como se indica en el �ltimo rengl�n, con lo cual vuelve a aparecer el gui�n titilante del Debug, esperando un nuevo comando. En general se debe pulsar Enter luego de escribir un comando o cuando se quiere que aparezca el gui�n titilante, para indicarle un nuevo comando al Debug. Los valores que aparecen var�an de un computador a otro, y en un mismo computador. Con el Debug es factible leer cualquier zona de memoria, sea RAM o ROM.

> Escritura de los datos en memoria mediante el Debug:

El ejemplo anterior mostr� la lectura de posiciones consecutivas de memoria. Tambi�n es posible luego de leer una posici�n cambiar su contenido, o sea escribirle un n�mero de dos d�gitos en hexa (equivalente a un byte binario). Este n�mero se debe escribir a continuaci�n del punto que acompa�a a cada valor le�do, en el espacio que para tal fin se ha reservado. Luego de escribir el nuevo contenido que tendr� una posici�n, se puede leer la siguiente pulsando la barra de la forma vista. Si tambi�n se desea cambiar el contenido de esta posici�n, debe escribirse el nuevo valor despu�s del punto del contenido anterior, y as� de seguido.
Volviendo al proceso de datos de la figura 1.15 escribiremos en 5000 y 5001 los contenidos 20 y 10 (que corresponden al dato P =1020 H, y en 5006 y 5007, los contenidos 40 y 20, correspondientes a Q = 2040 H

-E 5000 (figura1.jpg "figura1.6")	(Examinar memoria y escribir en ella)
> 309D:5000		1F.20		06.10		50.		8D.		46.		B0.		A0.40		6A.20 (figura1.jpg "figura1.6")
_

   Figura 1.16[^1]

Si se quiere corroborar que los valores reci�n escritos son los nuevos contenidos de las posiciones modificadas, nuevamente se ordena examinar, debiendo resultar:

-E 5000 (figura1.jpg "figura1.6") (Examinar memoria)
> 309D:5000 20. 10.   50.   8D.   46.   BO.   40.   20. (figura1.jpg "figura1.6")
_

De esta manera se han escrito en las posiciones 5000, 5001, 5006 y 5007 los datos que en la figura 1.15 aparecen escritos en la "escalera" (que representa las posiciones de memoria). En las posiciones 5010 y 5011 deber� ir el resultado de la operaci�n a realizar, en reemplazo de los contenidos que existan (en este caso FD y 11, como surge de la primer lectura realizada), por lo que no interesa estos valores (FD y 11)
> Con el mismo procedimiento se escriben en memoria los c�digos de m�quina de las instrucciones, a partir de la direcci�n elegida 0200H

-E 200 (figura1.jpg "figura1.6") (Examinar memoria y escribir en ella)
> 309D:0200 25.A1 F3.00 AA.S0 DD.03 09.06 56.00 00.50 AB.2B
> 309D:0208 49.06 FF.06 00.50 12.A3 FF.10 FA.50 (figura1.jpg "figura1.6")
_


Verificando luego si la escritura anterior es correcta, resulta:

-E 200 (figura1.jpg "figura1.6") (Examinar memoria)
> 309D:0200 Al. 00.   50.   03.   06.   OO.   50.   2B.
> 309D:0208 06. 06.   50.   A3    10    50 -/
_


De esta forma hemos realizado la escritura en memoria de las instrucciones.
Suponiendo que se quiera salir del Debug, se debe tipear Q (Quit) para volver al DOS:
-Q (figura1.jpg "figura1.6") (para salir del Debug)
C:\>   (el DOS espera comando)

---
[^1] De ac� en adelante se designa con la palabra "figura" a porciones de la pantalla que se ver�an usando cl programa Debug.

---

1-35
---

###�C�mo encuentra la UC en memoria la primer instrucci�n y las siguientes de un programa a ejecutar, mediante registro IP?
---

Anteriormente se estableci� que el registro puntero de instrucci�n (IP) tiene la funci�n de indicar la direcci�n de memoria donde se encuentra la pr�xima instrucci�n a ejecutar.
En el programa codificado (figura 1.15) la primer instrucci�n comienza en la direcci�n 0200H, y las dos siguientes en 0203H y en 0207H. Por lo tanto, en este caso IP deber� contener sucesivamente los valores binarios que en hexa son: 0200H, 0203H y 0207H, como se verificar� cuando se ejecuten esas instrucciones.
Suponiendo que IP empiece con el valor 0200H �ya veremos c�mo� puesto que el c�digo de I(1) ocupa 3 bytes, (esto lo "conocer�" la UC al ejecutar 1(1)), si la UC hace la suma (con su calculador que es la UAL) 0200 + 3 = 0203, podr� determinar el nuevo valor que debe tener IP, que es la direcci�n donde est� I(2)] Del mismo modo, cuando ejecuta I(2) �que ocupa 4 bytes�, podr� calcular 0203 + 4 = 0207 para ubicar I(3).
Por �ltimo si a 0207 le sumamos 4 (cantidad de bytes de I(3)), obtenemos 020B, direcci�n de I(4) (en hexa despu�s de 7 siguen 8, 9, A, B) As� sucesivamente la UC va cambiando el valor de IP [^1] para ir localizando en memoria las sucesivas instrucciones que debe ejecutar.
Esta es la forma pensada para que la UC localice y ejecute, en el orden establecido, cada una de las instrucciones que forman una secuencia. Por lo tanto, para respetar estas "reglas de juego" las instrucciones a ejecutar deben estar escritas en posiciones'consecutivas de memoria.
Una "> instrucci�n de salto " �a tratar� permite no seguir la ejecuci�n de un programa con la instrucci�n que est� escrita a continuaci�n de ella en memoria, sino continuar con otra instrucci�n, cuya direcci�n debe permitir formar instrucci�n de salto. El valor de esta direcci�n debe pasar al IP.
O sea que igualmente esta instrucci�n permite encontrar la que le sigue.
 

> Por la tanto, cada instrucci�n permite determinar donde est� la siguiente a ejecutar, y por consiguiente, establecer el valor que tendr� el registro IP


### �Qui�n se encarga de proporcionar la direcci�n de la primer instrucci�n de cada programa a ejecutar?
---

En las pr�cticas que realizaremos con el Debug, seremos nosotros quienes nos encargaremos de escribir en el IP la direcci�n de la primer instrucci�n de una secuencia que queremos ejecutar.
Puesto que un computador pasa autom�ticamente de la ejecuci�n de un programa a otro, se supone que tiene que existir un mecanismo para hacer esto. A continuaci�n daremos un esbozo acerca de c�mo esto �ltimo tiene lugar, o sea qui�n se encarga de dar al IP la direcci�n donde comienza cada nuevo programa a ejecutar, una vez que el mismo y los datos se han escrito en memoria.
Cuando se enciende un computador, el primer programa que se ejecuta es siempre el mismo. Los c�digos de sus instrucciones est�n permanentemente en la porci�n ROM de memoria principal,
siendo que el hardware (circuiter�a) provee la direcci�n de la primer instrucci�n a ejecutar.O sea que el hardware inicializa el valor del IP al encender el equipo, as� como el valor de otros registros [^2] Las primeras generaciones de computadoras que se construyeron �hoy visibles en fotos o museos� presentaban un gran panel frontal lleno de llaves "si-no". El operador ten�a que cargar mediante dichas llaves, un registro equivalente al IP con la direcci�n donde estaba la primera instrucci�n del primer programa a ejecutar. Algo semejante haremos muy pronto mediante el teclado y el programa Debug.
Como resultado de la ejecuci�n de dicho programa almacenado en ROM, se escribe en memoria principal una copia de programas que est�n en el disco. Estos al ser ejecutados traen a memoria los programas del "sistema operativo", que tambi�n est�n en el disco como archivos. Luego de lo cual en pantalla aparece C> o alguna imagen con opciones, para indicar al sistema operativo mediante un comando, qu� programa se desea traer a memoria.

> Esto es, un programa del sistema operativo permite traer del disco a memoria, una copia del programa que necesita el usuario, y se encarga de que en el IP aparezca la direcci�n de la primer instrucci�n del programa a ejecutar.

Esto se consigue si la �ltima instrucci�n del programa del SO que se encarga de esta tarea, es una instrucci�n de salto, que indique la direcci�n donde est� la primer instrucci�n del programa del usuario a ejecutar. 

---

[^1] La UC necesita "anotar" en IP el valor de la direcci�n que calcul� mediante la UAL De no memorizado en IP, se perder�a dicho valor
[^2] Como el registro CS (code segment) de la UCP que junto con IP constituyen un contador de programa (CP)
---

1-36
---

Como se describi�, esta direcci�n se instala en el IP, con lo cual en forma autom�tica, sin intervenci�n humana, la pr�xima instrucci�n que la UC ejecuta - luego que ejecut� la �ltima instrucci�n de salto citada ser� la primera del programa de usuario. A partir de �sta se hallan las siguientes de la forma vista.
Debe consignarse que el sistema operativo registra la direcci�n d�nde dej� la memoria la primera instrucci�n del programa que trajo del disco, la cual es proporcionada al IP por la isntrucci�n de salto citada.

> Cuando termina de ejecutarse este programa, la �ltima instrucci�n del mismo llamar� al sistema operativo.
Ser� una instrucci�n que en esencia ordena saltar a la direcci�n de memoria donde est� la primer instrucci�n de un programa del SO. Este decidir� cu�l es el pr�ximo programa que debe ejercutar la UC.

De esta forma se pasa autom�ticamente de la ejecuci�n de un programa a otro, sin intervenci�n humana.
Las instrucciones de salto, son pues las que permiten cambiar autom�ticamente el valor del IP, y pasar a ejecutar una instrucci�n que est� en cualquier lugar de la memoria, que ser� la primera de una secuencia escrita en posiciones sucesivas de memoria. Esta secuencia puede ser el propio programa en ejecuci�n, o pertenecer a otro programa que debe ejecutarse a continauci�n.

### �C�mo se cambia la direcci�n de instrucci�n que indica el IP?
---
Conforme a lo anticipado mas arriba, mediante el Debug cargaremos en el IP la direcci�n de la primera instrucci�n a ejecutar, que como hemos establecido es 0200H. Para realizar esto, una vez que mediante el Debug hemos escrito los datos y las instrucciones, le damos la orden:

-R IP (figura1.jpg "figura1.6")  (comando al debug para examinar el valor del Registro IP y cambiarlo si se desea)										
IP 0100  (el Debug informa que actualmente el IP contine 0100)										
: 0200 (figura1.jpg "figura1.6") (al lado de los dos puntos se deja el Debug escribimos 0200, nuevo valor que debe tener IP)										
   (figura3.jpg "figura3.6")					

Teniendo en el IP la direcci�n de L, ya se puede ejecutar la secuencia de instrucciones escritas, como sigue.

### �C�mo puede visualizarse mediante el Debug la forma en que se van procesando los datos, al ejercutarse las instrucciones en una PC?
---

As� como el debug permite examinar y modificar la memoria, tambi�n puede mostrar en pantalla una "radiograf�a" del contenido de registros del microprocesador (UCP). Observando los datos a procesar en memoria, y como a partir de ellos se obtienen resultados, puede seguirse la evoluci�n de un proceso de datos.
Adem�s con el Debug esto puede hacerse paso a paso, dado que permite ejecutar en "c�mara lenta" una a una las instrucciones de un programa o secuencia de modo de poder ver como van cambiando de valor los registro de la UCP y posiciones de memoria. Esto es lo que haremos a continauci�n, con las instrucciones escritas anteriormente, experiencia que puede hacerse con cualquier PC. Antes de ejecutar dichas instrucciones, y por m�todo, primero conviene examinar los registros de la UCP y otros datos que muestra el Debug[^1], de los cuales s�lo nos interesan en esta etapa los que indicaremos en negrita.
Hemos usado el comando R IP - para conocer el valor de un registro particular[^2] y poder luego cambiarlo.
Si se usa el comando R a secas, se visualiza el valor de registros de la UCP sin poder modificarlos:


- R	(figura1.jpg "figura1.6") (Examinar registros)									
> AX=0000	BX=0000	CX=0000		DX=0000	SP=FFEE		BP=0000		SI=0000	DI=0000
DS=309D	ES=309D	SS=309D		CS=309D	> IP=0200	NV	UP    EI	PL	NZ    NA	PE    NC
	
309D:0200			MOV AC.[5000] [^3] 					DS:5000=1020	
-										
   (figura4.jpg "figura4.6")					

---
[^1] El Dubug simula un 80286, pero como �ste es compatible con el 386, 486 y el Pentium (que tienen registros de 32 bits) puede
usarse con cualquier PC. Hay programas m�s completos que el Debug, pero lo hemos elegido por que est� a la mano en cualquier PC.
[^2] Este comando, seguido del nombre de cualquier registro de la UCP, permite leer su valor y poderlo cambiar. As� R AX permite
leer y cambiar AC. La lista de todos los comandos del Debug se obtiene mediante la tecla ? seguida de Enter.
[^3] En cada tercer rengl�n, a la derecha del c�digo de m�quina de la pr�xima instrucci�n que se ejecutar�(en este caso A10050), siempre
aparece su codificaci�n equivalente en lenguaje Assembler (en este caso MOV AC,[5000]. a tratar en la Unidad 3 de la presente obra.


---

1-37
---
Los dos primeros renglones indican el estado de registros de la UCP. De �stos en primer lugar por el momento �nicamente importan AX e IP[^1]. 
Como primer medida verificamos qu� IP est� con el valor 0200 que le hab�amos asignado mediante R IP. Si bien AX contiene 000H (16 ceros en binario), este valor particular no interesa, pues I(1) ordena escribir 1020H, destruyendo el valor anterior (000H).
El tercer rengl�n se refiere a la memoria principal. El valor 0200 (igual al de IP) corrobora la direcci�n donde empieza la pr�xima instrucci�n a ejecutar, y al lado del mismo el c�digo A10050, que es el que hab�amos escrito en memoria para I�, como puede verificarse (que ser� el valor que tendr� el registro RI) O sea que es la instrucci�n que queremos ejecutar en primer lugar. 
En la parte derecha indica que en la direcci�n 5000 (involucrada en la instrucci�n) se tiene el valor 1020 (dato antes escrito) Puesto que IP=0200, el dato 1020 y el c�digo A10050 de la instrucci�n son correctos, podemos ejecutar �sta. Para ello simplemente se da el comando T, y luego el Debug visualiza la misma informaci�n que la figura 1.18, pero con los cambios habidos luego de la ejecuci�n de la instrucci�n:

�T (figura1.jpg "figura1.6") + (Ejecuci�n de la instrucci�n I�) 
> AX=1020   BX=0000  CX=0000   DX=0000   SP=FFEE	 BP=0000    SI=0000    DI=0000
DS=309D   ES=309D  SS=309D   CS=309D    > IP=0203      NV  UP EI  PL NZ   NA   PO   NC
309D: 0203    > 03060050		 ADD    AX, [5000]� 		             > DS: 000=1020
_

  Figura 1.19
  

Constatamos que I(1) se ha ejecutado correctamente, pues se ha cumplido la orden que portaba su c�digo: escribir en AX una copia del contenido de la posici�n 5000, que era 1020. 
Si observamos el tercer rengl�n vemos que en 5000 sigue estando 1020. Tambi�n ha cambiado IP a 0203, para apuntar la direcci�n de I(2), 
como hab�amos previsto al hablar de IP. Asimismo vemos que 
el c�digo 03060050 de I2 es el correcto, por lo que podemos ejecutar I(2)[^2]:

�T (figura1.jpg "figura1.6")  + (Ejecuci�n de la instrucci�n I2)
> AX=2040	BX=0000	CX=0000     DX=0000     SP=FFEE       BP=0000      S1=0000        DI=0000
DS=309D	ES=309D	SS=309D     CS=309D      > IP=0207         NV UP El  PL NZ NA PO NC
309D: > 0207     2B060650        SUB    AX. [5006]2 	                DS: > 5006=2040
_

  Figura 1.20
  

Se ha realizado lo que ordenaba I(2): sumar al valor 1020 de AX el contenido de 5000 (que es 1020), 
y el resultado (2040) escribirlo en lugar de 1020. 
Tambi�n se verifica que el dato es 2040, y que 2B060650 es el c�digo de I3, instrucci�n de resta que pasaremos a ejecutar:

�T (figura1.jpg "figura1.6")  + (Ejecuci�n de la instrucci�n I(3))
> AX=0000	BX=0000       CX=0000     DX=0000       SP=FFEE        BP=0000      S1=0000          DI=0000
DS=309D	ES=309D       SS=309D     CS=309D       IP=020B     NV   UP   El   PL   ZR   NA   PE    NC
309D: > 020B     > A31050                 MOV [15010], AXD                     DS: > 5010=FD11
_

   Figura 1.21
   

I(3) ordenaba restar a AX el contenido de 5006, que es 2040H, o sea que se ha efectuado 2040H - 2040H = = 000H, como aparece en AX.

�T (figura1.jpg "figura1.6")   + (Ejecuci�n de la instrucci�n I4)
> AX=0000	BX=0000	CX=0000	DX=0000	SP=FFEE BP=0000    SI=0000        DI=0000
DS=309D	ES=309D	SS=309D	CS=309D	> IP=020E	NV UP El	PL ZR NA PE NC
309D: 020B	BB1026	MOV BX, 2610
_


  Figura 1.22

---
[^1] En la Unidad 3 al ejemplificar secuencias m�s complejas, usaremos casi todos ellos, al igual que muy pronto los �flags" o indicadores de estado (NV UP El. etc.). Los registros DS. CS. SS. ES, todos con el valor de referencia 309D mencionado en un pie de p�gina anterior.
De tener valores diferentes cada un, permiten definir para Datos. C�digo, Stack y Extensi�n, cuatro zonas independientes de memoria de 64000 direcciones (posiciones de un byte). Como todos tienen igual valor, las cuatro zonas (�segmentos ") est�n superpuestas en una sola. 
[^2] Por razones did�cticas se ha elegido el mismo dato para I� e I�. pudiendo estar en otra direcci�n el dato que se opera en I�

---

1-38
---
El registro IP pas� a 020E H. En esa posici�n y en las dos siguientes quedaron al azar los valores BBj _y_26. .(como resulta de leer el tercer rengl�n) que el Debug interpreta como correspondientes a instrucci�n. Como ya hemos ejecutado I(1) I(2),I(3), e I(4) no seguimos ejecutando ninguna instrucci�n mas.

---
> Un programa termina con una instrucci�n (que no hemos usado) cuyo c�digo ordena que se pase a ej< un programa del sistema operativo, para que �ste decida cu�l es el pr�ximo programa que se debe ejecutar.
---

Si queremos verificar que en las direcciones 5010 y 5011 se escribi� el 
resultado que est� en AX. Hacemos:

-E5010 (figura1.jpg "figura1.6") (Examinar memoria)
309D- > 5010  00.	00. (figura1.jpg "figura1.6")

con lo cual constatamos que efectivamente se cumpli� lo que ordena I(4)


### �C�mo ordenar que los c�digos de m�quina dei proceso anterior sea ejecutados una tras otro autom�ticamente, conforme sucede realmente?
---

Por razones did�cticas se ha ejecutado instrucci�n por instrucci�n, para ver luego de cada ejecuci�n coa cambiaba el interior del computador. 
Fue necesario antes de ejecutar cada instrucci�n la intervenci�n humana para pulsar T (figura1.jpg "figura1.6") entre otras cosas. Esto se parece al manejo de una calculadora cada vez que apretamos una tecla = . Si las computadoras funcionaran de esa manera, no tendr�a mucho sentido su existencia, puesto qf justamente su velocidad de procesamiento de datos es quiz�s el mayor de sus atributos.
Con el Debug tambi�n es factible hacer que se ejecuten, una tras otra, a la velocidad del computador, fc instrucciones escritas en memoria, y as� obtener casi instant�neamente los resultados requeridos.

> As� puede corroborarse que una vez que datos e instrucciones est�n en memoria, la UCP realiza u proceso de datos en forma autom�tica, sin intervenci�n humana, merced a la acci�n de circuitos electr�nicos que responden a las �rdenes que portan las instrucciones.


Luego de haber ejecutado las instrucciones una por una, puesto que los datos e instrucciones permanecen a memoria sin cambios, y que I(1) no requiere que AX est� en cero, si se ejecutan nuevamente dichas instrucciones se obtendr�n los mismos resultados. Esto es lo que haremos, pero en vez de ejecutarlas una por una, daremos la orden de ejecutar una tras otra, I(1), I(2), I(3) e I(4) Antes de dar el comando debemos hacer que I -que qued� en 020B� pase a tener el valor 0200 H, para apuntar a la direcci�n donde comienza I(1), para lo cual debemos ordenar R IP de la forma vista. Despu�s, como paso previo a la ejecuci�n, para constatar que todo est� en orden podemos hacer como antes:

-R (figura1.jpg "figura1.6") (Examinar registros)
> AX=0000	BX=0000	CX=0000	DX=0000	SP=FFEE	BP=0000	S1=0000	DI=0000
DS=309D	ES=309D	SS=309D	CS=309D	> IP=0200	NV	UP El	PL	NZ NA	
PO NC
309D:> 0200	> AI0050	MOV AX,[5000j	DS:> 5000=I020
El comando para ejecutar las instrucciones que van de la direcci�n 200 a la 20F [^1] es

-G =0200 020E (figura1.jpg "figura1.6")
> AX=0000	BX=0000	CX=0000	DX=0000	SP=FFEE	BP=0000	SI=0000	DI=0000	L
DS=309D	ES=309D	SS=309D	CS=309D	> IP=020E	NV	UP El	PL	ZR NA	PE NC
309D:020B	BB1026 MOV BX.2610


Puede verificarse que se ha obtenido el mismo resultado que en la figura 1.22, correspondiente al mismo proceso realizado instrucci�n por instrucci�n con intervenci�n del operador.

---
> Es importante aclarar que G -02(X) 020E - es una orden para el Debug, para que se ejecute el progrant que comienza en la direcci�n indicada, y no una orden para la UC, que permanentemente est� ejecutando programas. Sin ir m�s lejos se ejecuta un programa cada vez que pulsamos o soltamos cada tecla de comando G = 0200 020E, as� como se ejecuta otro cada 0,018 seg. para actualizar la hora y el calendario del computador, entre otros. Como se estableci�, es mediante instrucciones de salto, antes citadas, que se cambia el valor del IP para que la UC en forma autom�tica pase de la ejecuci�n de un programa a otro.

---
[^1] Direcci�n donde comienza una instrucci�n que sigue a I(5) que no queremos ejecutar.

---
