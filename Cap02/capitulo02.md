##Representacion Numerica.

### 2.1.  Introdución.

*Desde hace tiempo el hombre en su vida diaria se expresa, comunica, almacenan información, la manipula, mediante letras y números. Para la representación numérica utiliza el sistema de representación decimal, en tanto que, dependiendo del idioma, dispone de un alfabeto que representa estas letras. Siguiendo el mismo principio que guía al hombre, las computadoras tienen su propio sistema de representación. Debido a su construcción basada fundamentalmente en circuitos electrónicos digitales, utiliza un sistema binario. Esto obliga a transformar a la representación binaria para que la maquina sea capaz de procesarlos.* 
Como veremos más adelante, tanto el sistema decimal como el binario están basados en los mismos principios. En ambos, la representación de un numero se afectúa por medio de cadenas de símbolos, los cuales representan una determinada cantidad dependiendo de cada símbolo y la posición que ocupa dentro de la cadena con respecto al denominado punto (o coma) decimal.  *
*Por cuestiones de índole técnica, los circuitos electrónicos que conforman una computadora suelen estar capacitados para reconocer señales eléctricas de tipo digital; por lo tanto, se hace necesario que los métodos de codificación internos tengan su origen en el sistema binario, y con ellos se pueda representar todo tipo de informaciones y ordenes que sean manejadas por la computadora.*
 *En los circuitos electrónicos suele representarse la presencia de tensión (electricidad) en un punto de un circuito por medio de un 1, en tanto que un 0 representa la ausencia de dicha tensión.*

## 2.2 Sistema de Numeracion

*Se denomina sistema de numeración al conjunto de simbolos y reglas que se utilizan para la representacion de datos numericos o cantidades. Un sistema de numeracion se caracteriza fundamentalmente por su base, que es el numero de simbolos distintos que utiliza y ademas es el coeficiente que determina cual es el valor de cada simbolo dependiendo de la posicion que ocupe.*
*Los sistemas de numeracion actuales son sistemas posicionales, en los que el valor relativo que representa cada simbolo o cifra de una determinada cantidad depende de su valor absoluto y de la posicion relativa que ocupa dicha con respecto a la coma decimal.*
##2.2.1. Teorema fundamental de la numeración
*Se trata de un teorema que relaciona una cantidad expresada en cualquier
sistema de numeración posicional con la misma cantidad expresada en el sistema
decimal. Supongamos una cantidad expresada en un sistema cuya base es B y
representamos por xi cada uno de los dígitos que contiene dicha cantidad, donde
el subíndice i indica la posición del dígito con respecto a la coma fraccionaria,
la posición se numera en forma creciente hacia la izquierda y decreciente hacia
la derecha de la coma (posición 0), en ambos casos de a 1.
El Teorema Fundamental de la Numeración dice que el valor decimal de una
cantidad expresada en otro sistema de numeración, está dado por la fórmula:
Número =
Xn
i=−m
(dígitoi) × (base)
i
(2.1)
donde el número en base B es . . . x4x3x2x1x0x−1x−2 . . . , o sea:
Número = x−m × B
−m + x−m+1 × B
−m+1 + · · · +
+ x−2 × B
−2 + x−1 × B
−1 + x0 × B
0 + x1 × B
1 + x2 × B
2 + · · · +
+ xn−1 × B
n−1 + xn × B
n
1 (2.2)*
##2.2.2. Sistemas decimal, binario y hexadecimal###
*El sistema que ha usado el hombre para contar desde hace bastante tiempo
es el denominado sistema decimal, adoptado por contar con los diez dedos de la
mano. El sistema decimal es uno de los denominados posicionales, que utiliza
un conjunto de 10 símbolos, xi0, 1, ..., 9. Un valor determinado o cantidad, que
se denomina número decimal, se puede expresar por la fórmula del Teorema 2.1,
donde la base es 10.*
###¿Cuál es la interpretación de la representación de la cantidad 3,1416?###
*Siguiendo el Teorema Fundamental de la Numeración, utilizando la base 10,
resulta*:
3, 1416 = 3 × 100 + 1 × 10−1 + 4 × 10−2 + 1 × 10−3 + 6 × 10−4
(2.3)

*El sistema binario es el sistema de numeración que utiliza internamente el
hardware de las computadoras actuales. La base o número de símbolos que
utiliza el sistema binario es 2, siendo los símbolos 0 y 1, los utilizados para la
representación de cantidades*.###¿Qué número decimal representa el número binario 1001,1?###
*Utilizando el Teorema Fundamental de la Numeración*:
1001, 1(2 = 1 × 2
3 + 0 × 2
2 + 0 × 2
1 + 1 × 2
0 + 1 × 2
−1
(2.4)

*Al igual que los anteriores, el sistema hexadecimal es un sistema posicional
pero que utiliza dieciséis símbolos para la representación de cantidades. Estos
símbolos son los siguientes: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E y F; donde las
letras A, B, C, D, E y F equivalen a 10, 11, 12, 13, 14 y 15 del sitema decimal
respectivamente*.

###¿Qué número decimal representa el número hexadecimal 2CA?###
*Siguiendo el Teorema Fundamental de la Numeración:
2CA(16 = 2 × 162 + C × 161 + A × 160
(2.5)
2CA(16 = 2 × 162 + 12 × 161 + 10 × 160
(2.6)
2CA(16 = 512 + 192 + 10 = 714 (2.7)*

##2.2.3. Operaciones de Suma y Resta Binaria##
*Las operaciones aritméticas son similares a las del sistema decimal, con la
diferencia que se manejan sólo los dígitos 0 y 1. Al realizar la suma parcial de
dos dígitos, si el resultado excede el valor del máximo dígito (el 1) se debe pasar
el sobrante (denominado acarreo) a la suma parcial siguiente hacia la izquierda.
Sumemos los números binarios 100100 y 10110*
1 −→ carry
1 0 0 1 0 0
+ 1 0 1 1 0 =1 1 1 0 1 0

*En la resta binaria hay que tener en cuenta que al realizar las restas parciales
entre dos dígitos de idénticas posiciones, uno del minuendo y otro del sustraendo,
si el segundo excede al primero, se sustrae una unidad del dígito de más a la
izquierda en el minuendo –pedir prestado-. Si el dígito siguiente de la izquierda
es 0, se busca en los sucesivos teniendo en cuenta que su valor se multiplica por
dos a cada desplazamiento sucesivo a derecha.
Restemos los números binarios 111100 y 101010*
10 −→ borrow
1 1 1 ✁1 ✁0 0
- 1 0 1 0 1 0 = 0 1 0 0 1 0##2.2.4. Conversiones entre los sistemas de numeración##*Se denomina conversión entre números representados en distintos sistemasde numeración a la transformación de una determinada cantidad expresada enuno de dichos sistemas de numeración, a su representación equivalente en el otrosistema.Conversión decimal-binarioEl método de conversión de un número decimal a un número binario consisteen efectuar, sobre la parte entera del número decimal, divisiones sucesivas de loscocientes por el número 2, hasta que el cociente entre una de las divisiones tomeel valor 0. La unión de todos los restos obtenidos, escritos en orden inverso, nosproporciona el número inicial expresado en sistema binario*. ![](http://www.carlospes.com/curso_representacion_datos/imagenes/ejemplo_02_73_1.gif)**Figura 2.1**: *Convirtiendo el número decimal 19 a binarioPara convertir una fracción decimal a su equivalente binario se debe multiplicardicha fracción por dos, obteniendo en la parte entera del resultado elprimero de los dígitos binarios de la fracción que buscamos. A continuación,se repite el proceso con la parte fraccionaria del resultado anterior, obteniendoen la parte entera del nuevo resultado el segundo de los dígitos buscados. Elproceso se repite hasta que desaparezca la parte fraccionaria de los resultadosparciales (se haga 0) o hasta que tengamos los suficientes dígitos binarios*.0, 828125 ×2 = 1, 656250, 65625 ×2 = 1, 31250, 3125 ×2 = 0, 6250, 625 ×2 = 1, 250, 25 ×2 = 0, 50, 5 ×2 = 10, 828125(10 = 0, 110101(2***Figura 2.2**: Convirtiendo el número decimal 0,828125 a binarioConversión hexadecimal-binario y viceversaPara convertir un número hexadecimal a binario se sustituye cada dígitohexadecimal por su representación binaria con cuatro dígitos según el Cuadro 2.1***Hexadecimal Binario**![](http://4.bp.blogspot.com/_9fqFNLzPrtk/SicgckxUvXI/AAAAAAAAABk/f9KuH47Gv9U/s320/Tabla+Hex-Dec-Bin.png)**Cuadro 2.1**: Tabla de conversión **Hexadecimal-Binario***En tanto que la conversión binaria hexadecimal se realiza un proceso inverso.Se agrupan los dígitos binario de a 4 a partir del punto decimal hacia la izquierday hacia la derecha, sustituyendo cada cuarteto por su correspondiente dígitohexadecimal*.**Convertimos el número hexadecimal 7BA3,BC a binario**7........ B........A..... 3 ,.......B..... C0111 1011 1010 0111 , 1011 1100*Entonces luego de la conversión, escribimos el número. Omitimos los 0 no significativos*:7BA3, BC(16 = 111101110100111, 101111(2**Convertimos el número binario 110010100100,1011011 a hexadecimal***Completamos con 0 para obtener los cuartetos necesarios para la conversión.Realizamos la conversión inmediata utilizando el cuadro 2.1.*0001 1001 0100 1000 , 1011 0110 ---1-----9------ 4----- 8 , ----B----- 6Finalmente resulta: 1100101001000, 1011011(2 = 1948, B6(16**Conversión de cualquier base a decimal***Para ello se utiliza el teorema fundamental de la numeración y se convierteel número de la base que se disponga a la decimal.*##2.3. Representación de números enteros##*Las computadoras utilizan cuatro métodos para la representación interna denúmeros enteros (positivos y negativos)*:Módulo y signoComplemento a 1Complemento a 2Exceso a 2n−1*Estas representaciones de números utilizan el sistema binario y siempre seconsidera que tenemos un número limitado de bits para cada dato. Este númerode bits disponibles lo representamos generalmente con la letra n. También sepueden representar mediante estos métodos números reales, como veremos másadelante.Al tener una cantidad limitada de bits para representar, vamos a estar limitadosen la cantidad de números que podemos representar. Se denomina rangode representación en un método determinado al conjunto de número representablesen el mismo*.##2.3.1. Módulo y signo##*En este sistema de representación, el bit que está situado más a la izquierda(bit más significativo, MSB, most significant bit en inglés) representa el signo, ysu valor será 0 para el signo positivo (+) y 1 para el signo negativo (−). Los bitsrestantes (n−1) representan el módulo del número. Suponemos en principio quelos números no poseen parte decimal, por lo que la coma se supone implícita ala derecha.Por ejemplo, supongamos que disponemos de n = 8 bits, y queremos representarlos números 10 y −10. Veamos cuales son sus representaciones.*(0 es positivo +) 0 0 0 1 0 1 0módulo = 10**Figura 2.3**: Representación del número 10.(1 es negativo -) 0 0 0 1 0 1 0 módulo = -10**Figura 2.4**: Representación del número -10.**Rango***Para módulo y signo el rango de representación de una palabra de n bitsestá determinado por*:−2n−1 + 1 ≤ Rango ≤ 2n−1 − 1 (2.8).En el caso de n = 8 bits, el rango de representación va desde −127 a 127.La ventaja que presenta este sistema frente a otros es la de poseer un rangosimétrico (igual cantidad de números positivos que negativos). Mientras que sumayor inconveniente es el de poseer dos representaciones para el número 0. Elcual se representa tanto con un signo positivo (0) como con uno negativo (1) yel resto de los bits en 0.2.3.2. Complemento a 1En este sistema de representación también el bit de más a la izquierda seinterpreta como el signo, correspondiendo el 0 para el signo positivo (+) y el1 para el signo negativo (−). Para los números positivos, los n − 1 bits de laderecha representan el módulo (igual que en el sistema anterior). El negativo deun número positivo se obtiene complementando todos sus dígitos (cambiandoceros por uno y viceversa) incluido el signo.Veamos la representación en complemento a 1 de los números 10 y −10 parael caso de n = 8 bits.0 0 0 0 1 0 1 0+ módulo = 10Figura 2.5: Representación del número 10.1 1 1 1 0 1 0 1- módulo = 117Figura 2.6: Representación del número -10.RangoPara el complemento a 1 el rango de representación de n bits:−2n−1 + 1 ≤ Rango ≤ 2n−1 − 1 (2.9)*En el caso de n = 8 bits, el rango de representación va desde −127 a 127.La ventaja que presenta este sistema frente a otros es la de poseer un rangosimétrico (igual cantidad de números positivos que negativos). Mientras que sumayor inconveniente es el de poseer dos representaciones para el número 0. Elcual se representa tanto con un signo positivo con todos sus bits en cero (0), ycon signo negativo, con todos los bits en 1*.##2.3.2. Complemento a 1##En este sistema de representación también el bit de más a la izquierda seinterpreta como el signo, correspondiendo el 0 para el signo positivo (+) y el1 para el signo negativo (−). Para los números positivos, los n − 1 bits de laderecha representan el módulo (igual que en el sistema anterior). El negativo deun número positivo se obtiene complementando todos sus dígitos (cambiandoceros por uno y viceversa) incluido el signo.Veamos la representación en complemento a 1 de los números 10 y −10 parael caso de n = 8 bits.(0+) 0 0 0 1 0 1 0 módulo = 10**Figura 2.5**: Representación del número 10.(1-)1 1 1 0 1 0 1 módulo = 117**Figura 2.6:** Representación del número -10.**Rango***Para el complemento a 1 el rango de representación de n bits:−2n−1 + 1 ≤ Rango ≤ 2n−1 − 1 (2.9)En el caso de n = 8 bits, el rango de representación va desde −127 a 127.La ventaja que presenta este sistema frente a otros es la de poseer un rangosimétrico (igual cantidad de números positivos que negativos). Mientras que sumayor inconveniente es el de poseer dos representaciones para el número 0. Elcual se representa tanto con un signo positivo con todos sus bits en cero (0), y*##2.3.3. Complemento a 2##*Al igual que los anteriores, este sistema de representación interpreta el bitde más a la izquierda como el signo, correspondiendo el 0 para el signo positivo(+) y el 1 para el signo negativo (−). Para los números positivos, los restantes(n − 1) bits de la derecha representan el módulo (igual que en los dos sistemasanteriores). El negativo de un número positivo se obtiene en dos pasos:1- Se complementa el número positivo en todos sus bits (cambiando ceros poruno y viceversa), incluido el bit de signo. Es decir se hace el complementoa 1.*2- Al resultado obtenido se le suma 1 (en binario), despreciando el últimoacarreo si existiera.Veamos la representación en complemento a 2 de los números 10 y −10 parael caso de n = 8 bits.(0+) 0 0 0 1 0 1 0 módulo = 10**Figura 2.7**: Representación del número 10.(1-) 1 1 1 0 1 1 0 módulo = 118**Figura 2.8:** Representación del número -10.**Rango**Para el complemento a 2 el rango de representación de n bits:−2n−1 ≤ Rango ≤ 2n−1 − 1 (2.10)*Para el caso de n = 8 bits, el rango de representación va desde −128 a 127.La principal ventaja es la de tener una única representación para el número 0.Como principal desventaja de este sistema es que el rango de representación denúmeros no es simétrico.*##2.3.4. Exceso a 2 n-1##*Este método de representación no utiliza la convención del bit más significativopara identificar el signo, con lo cual todos los bits representan un número ovalor. Este valor se corresponde con el número representado más el exceso, quepara n bits viene dado por 2n−1*. *El signo del número resulta de una operaciónaritmética. Por ejemplo, para n = 8 bits el exceso será 128, con lo cual para representarun número deberá sumársele dicho exceso. De esta manera el número10, que veníamos representando, recibirá la adición del número 128, con lo querepresentaremos el número decimal 138 en binario. Por otro lado, el número 10,se representará como el número decimal 118 en binario (−10 + 128)*. De estaforma quedarán:(1+) 0 0 0 1 0 1 0 módulo = 138**Figura 2.9**: Representación del número 10.(0-) 1 1 1 0 1 1 0 módulo = 118**Figura 2.10**: Representación del número -10.**Rango**El rango de representación en exceso a 2n−1 viene dado por:−2n−1 ≤ Rango ≤ 2n−1 − 1 (2.11)*La principal ventaja de este sistema de representación resulta que tiene unaúnica forma de representar el cero (0). Mientras que su principal desventaja esque el rango resulta asimétrico. La representación del 0 consiste en representarel exceso, por ejemplo 128 para 8 bits.Resulta interesante observar que todo número representado en exceso a 2n−1tiene la misma representación que un complemento a 2 con el bit de signocambiado. Podría decirse entonces, que el bit mas significativo representaría elsigno pero esta vez utilizando el 0 para el signo positivo (+) y el 1 para el signonegativo (−).La representación en exceso a 2n−1es simplemente desplazar el cero de sulugar, a donde está el exceso.*#2.3.5. Suma en complemento a 1#*En la aritmética de complemento a 1, dos números se suman de igual formaque en binario a 1, con la única diferencia que en caso de existir un últimoacarreo debe sumarse al resultado.Sumamos los números 10 y −3 en complemento a 1 para n = 8 bitsLa representación de los números es:Decimal Binario (valor absoluto) Complemento a 1*Decimal:10 Binario (valor absoluto): 00001010 =  Complemento a 1: 00001010Decimal: -3  Binario (valor absoluto):00000011 Complemento a 1: 11111100Por lo tanto la suma:0 0 0 0 1 0 1 0 10(ca1 1 1 1 1 1 1 0 0 −3(ca1 1 0 0 0 0 0 1 1 0 6(ca1 0 0 0 0 0 0 0 1 1(ca1 →carry0 0 0 0 0 1 1 1 7(ca1**Sumamos los números 110 y 30 en complemento a 1 para n = 8 bits**0 1 1 0 1 1 1 0 110(ca1
 0 0 0 1 1 1 1 0 30(ca1
1 0 0 0 1 1 0 0 −115(ca1*Cuando sumamos 110 y 30 en complemento a 1 el resultado que obtenemoses −113, esto es debido a que la suma entre estos números es 140 y está fueradel rango posible de representación del complemento a 1 de 8 bits. Obtenemoslo que se conoce como sobrecarga u “overflow”.*#2.3.6. Suma en complemento a 2#En la aritmética de complemento a 2, dos números se suman de igual formaque en complemento a 1, con la única diferencia que se desprecia el últimoacarreo en el caso que el mismo exista.**Sumamos los números 10 y −3 en complemento a 2 para n = 8 bits**La representación de los números es:Decimal Binario (valor absoluto) Complemento a 2Decimal: 10  Binario (valor absoluto): 00001010 Complemento a 2: 00001010Decimal: −3 Binario(valor absoluto): 00000011 Complemento a 2: 11111101Por lo tanto para la suma:0 0 0 0 1 0 1 0 10(ca2 1 1 1 1 1 1 0 1 −3(ca21 0 0 0 0 0 1 1 1 7(ca2 el acarreo se descarta.Sumamos los números 110 y 30 en complemento a 2 para n = 8 bits0 1 1 0 1 1 1 0 110(ca2  0 0 0 1 1 1 1 0 30(ca21 0 0 0 1 1 0 0 −116(ca2*Cuando sumamos 110 y 30 en complemento a 2 el resultado que obtenemoses −116, esto es debido a que la suma entre estos números es 140 y tambiénestá fuera del rango posible de representación del complemento a 2 de 8 bits.Acá también obtenemos una sobrecarga u “overflow”.*##2.4. Representación en coma o punto fijo##*El nombre de esta representación surge de suponer la coma decimal situadaen una posición fija. El punto fijo es utilizado para la representación de nú-meros enteros, suponiéndose la coma decimal ubicada a la derecha de los bits.Cualquiera de los sistemas de representación de enteros vistos en el apartadoanterior es una representación de punto fijo, donde por lo general la parte decimales nula. También, el programador puede utilizar la representación en puntofijo para representar fracciones binarias escalando los números, de modo que lacoma decimal quede ubicada implícitamente en otra posición entre los bits, yen el caso límite a la izquierda de todos ellos describiendo un número fraccionalbinario puro (menor a 1).*##2.5. Representación en coma flotante*La coma o punto flotante surge de la necesidad de representar números realesy enteros con un rango de representación mayor que el que nos ofrece la representaciónen punto fijo y posibilitar a la computadora el tratamiento de númerosmuy grandes y muy pequeños. Estas ventajas que nos ofrece la coma flotante traen como contraprestación una disminución (relativamente pequeña) en la precisiónde los números representados. En su representación se utiliza la notacióncientífica o exponencial matemática en la que una cantidad se representa de lasiguiente forma*:numero = mantisa × base exponente (2.12)*Un número en esta notación científica tiene infinitas representaciones, delas que se toma como estándar la denominada normalizada. Consiste en que lamantisa no tiene parte entera y el primer dígito o cifra a la derecha del puntodecimal es significativo, es decir, distinto de 0, salvo en la representación delnúmero 0.Representemos el número 835,4 con base de exponenciación 10Con este ejemplo podemos observar cómo se construyen las infinitas representaciones.A nosotros nos va a interesar sólo la representación normalizada*.8354 × 10−1 = 835, 4 × 100 = 83, 54 × 101 = 8, 354 × 102 = 0, 8354 × 103(2.13)*A comienzos de los ´80, cada fabricante de computadoras tenía su propioformato de punto flotante. A fin de rectificar esta situación a fines de los ´70 elIEEE (Institute of Electrical and Electronics Engineers, Instituto de IngenierosEléctricos y Electrónicos) formó un comité para estandarizar la aritmética depunto flotante. Con esto se podría no sólo intercambiar los datos de puntoflotante entre diferentes computadoras sino que además proporcionaría a losdiseñadores de hardware un diseño que se sabía correcto. Como resultado elIEEE presenta el estándar internacional de punto flotante, más conocido comoIEEE 754. El estándar define tres formatos, precisión simple (32 bits), precisióndoble (64 bits) y precisión extendida (80 bits). Este último por lo general esutilizado en las unidades aritmético-lógicas de punto flotante, con la intenciónde reducir los errores por redondeo, por lo que sólo nos limitaremos a hablar delos primeros dos formatos.En todos los casos, como la computadora utiliza el sistema binario, la base enla que representaremos el número será la base 2. En ambos formatos la palabrabinaria en la que se almacena el número en punto flotante se divide en 3 partes.La primera consiste en el signo, la segunda es la representación del exponentey por último la representación de la fracción.La definición del punto flotante de una computadora sigue las siguientesreglas*:

- *El primer bit es utilizado como bit de signo, si este es 0 el signo es positivo(+) y si es 1 el signo es negativo (−), tanto en precisión simple como enprecisión doble*.



- *El exponente se representa en exceso a 2n−1, siendo siempre un númeroentero. Para el caso de la precisión simple el exceso será de 127 y de 1023para la precisión doble. Los exponentes máximos (255 y 2047) y mínimo(0) se utilizan en casos especiales que describiremos más adelante.*





-  *Los restantes bits representan la fracción del número.*![](http://blogs.ua.es/jpm33/files/2013/06/ieee754_floating_point.gif)**Figura 2.11**: Formato de representación IEEE-754 simple y doble precisión*Una fracción normalizada comienza con la coma decimal seguida de un biten 1 y luego el resto de la fracción. Por ejemplo: 0, 10010001010101111101101.Siguiendo una práctica iniciada en la PDP-11, los autores del estándar se dieroncuenta que el bit inicial de la fracción no tiene por qué almacenarse, ya que puedesimplemente darse por hecho que está presente. Por lo tanto la norma definela fracción de una manera un tanto diferente a lo acostumbrado. La fracciónconsiste en un bit implícito, seguido de la coma decimal y los siguientes 23 o52 bits correspondientes. De esta manera si los 23 o 52 bits son todos ceros lafracción representada es el número binario 1, 0. Si todos los bits de la fracciónestán en uno, la fracción representa un número poco menor que el decimal 2, 0.Por lo general para simplicidad en la lectura, los números escritos en estanorma suelen representarse en su equivalente hexadecimal.***2.5.1. Convertimos en IEEE-754 de simple precisión al número −6, 2734375**Representamos este número en punto fijo. Primero tomamos la parte enteray la escribiremos en binario y luego convertiremos la parte decimal como vimosanteriormente:Parte entera: 6(10 = 110(20, 2734375 ×2 = 0, 5468750, 546875 ×2 = 1, 093750, 09375 ×2 = 0, 18750, 1875 ×2 = 0, 3750, 375 ×2 = 0, 750, 75 ×2 = 1, 50, 5 ×2 = 1, 00, 0 ×2 = 0Parte decimal: 0, 2734375(10 = 0, 0100011(2Entonces el número decimal −6, 2734375 en binario se escribe −110, 0100011**Figura 2.12**: Convirtiendo el número decimal −6, 2734375 a binarioUn número representado en coma fija, es igual a un número expresado ennotación científica con la base elevada al exponente 0:−6, 2734375 × 100 ≡ −110, 0100011 × 20Ahora que tenemos la notación científica, hallamos la forma normalizadapara representar en **IEEE-754**:−110, 0100011 × 20 = −11, 00100011 × 21 = −1, 100100011 × 22(2.15)Con el número normalizado tenemos el valor del exponente que debemoscolocar. En este caso como estamos utilizando precisión simple, 32 bits, el exponenteutiliza 8 bits por lo tanto el exceso es de 127:127 + 2 = 129(10 = 10000001(2 (2.16)Finalmente escribimos los 32 bits para formar la palabra de precisión simpleen la norma **IEEE-754**. Como el número es negativo, el bit de signo será 1.Luego seguirán los 8 bits correspondientes a la representación del exponente(10000001) y por último los valores que quedaron detrás de la coma decimalen la forma normalizada del número en base 2 (100100011) seguidos de 0 paracompletar los últimos 23 bits.-signo: 1 -exponente: 1000 0001 1001  -mantisa: 0001 1000 0000 0000 000Como mencionamos anteriormente por lo general para simplicidad en lalectura se suele escribir el número en **IEEE-754** con sus bytes hexadecimales:1100 0000 1100 1000 1100 0000 0000 0000 =C 0 C 8 C 0 0 0#2.5.2. Casos particularesEn el caso de que el exponente sea todo 0 el número representado en lafracción es un número desnormalizado. El cero se representa con el exponenteen 0 y la fracción también en 0. Si tenemos el exponente representando el númeromáximo podremos representar en caso de tener la fracción en 0 a los infinitos. Sitenemos algún patrón distinto de cero en la fracción tendremos la representaciónde “ningún número” o NaN (por sus siglas en inglés, Not a Number).![](http://www.carlospes.com/curso_representacion_datos/imagenes/fig_02_29_de_simple_a_10.gif)![](http://www.carlospes.com/curso_representacion_datos/imagenes/fig_02_30_de_doble_a_10.gif)
*El rango de representación en punto flotante debe ser analizado teniendo en
cuenta los máximos y mínimos valores representables tanto con signo positivo
como negativo*:



- mínimo número negativo = −(mantisaMAX) × 
base exponente MAX


- máximo número negativo = −(mantisaM IN ) × base−exponenteMAX


- mínimo número positivo = mantisaM IN × base−exponenteMAX

- máximo número positivo = mantisaMAX × base exponente
![](http://www.portalhuarpe.com.ar/Medhime20/Sitios%20con%20Medhime/Computaci%C3%B3n/COMPUTACION/Menu/modulo%203/imagenes/22figura.GIF)##2.6.1. Códigos alfanuméricos##*Una computadora puede trabajar internamente con un conjunto de caracteresque nos permitirán manejar datos, informaciones, instrucciones, órdenes decontrol, etc. Este conjunto de caracteres podemos subdividirlo en los siguientesgrupos*:

- Caracteres alfabéticos

- Letras mayúsculas (A..Z sin la Ñ)

- Letras minúsculas (a..z sin la ñ)

- Cifras decimales: los números 0, 1, ..., 9

- Caracteres especialescaracteres como el . , ; : * @, etc.

- Ordenes de control: Equivalen a las teclas enter, tabulación, esc, etc.
*En general cada carácter se maneja internamente en una computadora pormedio de un conjunto de 8 bits mediante un sistema de codificación binario quedenominaremos código de caracteres.Cada computadora tiene su código de caracteres definidos por el fabricante,si bien la mayoría de ellos adaptan a sus equipos códigos estándar de los yaestablecidos. En estos códigos se representa cada carácter por medio de un byte,con lo cual todo tipo de información puede ser utilizada internamente, formandocadenas de bytes sucesivos que representarán cadenas de caracteres para que lamáquina las maneje e interprete. No todos los tipos de códigos utilizan para larepresentación de caracteres los ocho bits de un byte; en la actualidad se tiendea utilizar códigos de 8 bits aunque siguen existiendo algunos códigos de 6 y 7bits*.*El primer código alfanumérico fue el código Baudot de 5 bits (aunque nointerpretado como nosotros lo hacemos ahora) se utilizaba en los teletipos deprincipios del siglo XX. Los primeros códigos utilizados en informática fueronde 6 bits, que permitían la representación de 64 caracteres, que generalmente secorresponden a:*

- 26 letras mayúsculas

- 10 cifras numéricas

- 28 caracteres especiales y de control*Un ejemplo de código de 6 bits es el código FIELDATA utilizado durante ladécada del ´50 por el ejército de los Estados Unidos. Con el nacimiento de loslenguajes de programación de alto nivel comenzaron a utilizarse códigos de 7bits que permiten la representación de los mismos caracteres que los códigos de6 bits añadiendo las letras minúsculas y caracteres cuyo significado son órdenesde control entre periféricos. Un ejemplo muy utilizado de este tipo de códigoses el ASCII (American Standard Code for Information Interchange) de 7 bits.Hoy los códigos utilizados son los de 8 bits, de los cuales los más conocidosson el EBCDIC (Extended Binary Coded Decimal Interchage Code), el ASCIIextendido que agrega un bit a la representación extendiendo la cantidad desímbolos disponibles a 256 y el Unicode*.