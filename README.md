# Conceptos Básicos
## Distributed Ledger Technology (DLT)
### Qué son las DLT
Las DLT son un conjunto de tecnologías que permiten diseñar una estructura de sistemas, los cuales funcionan como una base de datos descentralizada. Lo que significa que no existirá un ordenador central que contenga toda la información, aumentando la seguridad y evitando así que se pueda hackear el sistema.
Esta tecnología se usa principalmente para gestionar los sistemas de pago.
![DLT_esquema](https://www.iebschool.com/blog/wp-content/uploads/2021/07/dlt-payments.jpg)
Sin embargo, no todos los sistemas DLT tienen que estar completamente descentralizados. Pueden tener distintos grados:
- Descentralización completa (sin un núcleo de control).
- Descentralización Distribuida (uno o varios núcleos de control, junto a varios nodos de apoyo).
- Descentralización Federada (donde los núcleos locales tienen gran autonomía).

El acceso a estos sistemas puede ser privado o público, dependiendo del nivel de seguridad que se quiera aplicar al sistema.

En resumen, una red DLT permite el funcionamiento seguro de una base de datos digital no centralizada, eliminando la dependencia de una autoridad central que controle todo.

### Diferencias entre DLT y Blockchain
Se podría decir que Blockchain es un subconjunto de las tecnologías DLT. Lo que significa que todas las Blockchain son DLT pero no todas las DLT son Blockchain.
Con una representación gráfica, esto se ve reflejado de mejor forma:
![DLT_vs_Blockchain](https://www.iebschool.com/blog/wp-content/uploads/2021/07/dltv-vs-blockchain-1024x564.png)
Como se puede observar en la imagen, DLT está también formada por otros subconjuntos de tecnologías como Tempo o Dag, además de Blockchain.
Por otro lado, Blockchain es un sistema que depende de generar bloques en los cuales se almacena la información. Estos bloques son enlazados entre sí generando así la cadena de bloques. Esta cadena termina generando un registro enlazado y no modificable de la información que está contenida en dichos bloques.
Para garantizar la seguridad, tanto DLT como Blockchain, utilizan protocolos P2P (peer-to-peer). En éstos, al igual que en las DLT, existen distintos grados de descentralización (los mismos tipos que los mencionados anteriormente).
Sin embargo, no todo son similitudes. A diferencia de Blockchain, las DLT no necesitan estar estructuradas en bloques de datos. Una DLT simplemente es un tipo de base de datos distribuida.

### Cómo funcionan las DLT
Con las DLT se puede almacenar información de forma segura mediante la criptografía, accediendo a datos mediante claves y firmas criptográficas. Una vez se haya almacenado la información, se convierte en una base de datos inmutable y que sigue las reglas establecidas por la red.
Para que un ataque cibernético a una DLT tenga éxito, la única forma de conseguirlo es atacando todas las copias almacenadas en la red al mismo tiempo, lo que resulta prácticamente imposible.
Además, el uso del protocolo P2P hace que sea mucho más rápido, eficaz y económico el proceso de intercambio y actualización de datos.

### Bibliografía
https://www.iebschool.com/blog/que-son-las-dlt-y-en-que-se-diferencian-de-blockchain-digital-business/

## Bitcoin
### 1. Introducción
El dinero físico permite realizar transferencias de dinero sin intermediarios. En cambio, si se desea realizar de forma digital, se necesita una entidad de por medio (p.e: un banco), lo que implica:
- Se cobrará una comisión por la transacción.
- Se guardará información de las partes implicadas en la transacción.

Lo que buscamos es encontrar una forma de realizar pagos de forma digital la cual sea segura y sin interferencias de mediadores externos, evitando así los dos puntos mencionados anteriormente.

### 2. Transacciones
En primer lugar, poseer bitcoins no es como poseer dinero físico o en la cuenta del banco. El saldo del que dispone una persona se calcula en función de las transacciones, las cuales están encadenadas entre ellas. Si decides realizar una transacción a una persona y ésta realiza otra a otra persona, ambas pertenecerán a la misma cadena. El dinero del que dispones está definido por las transacciones que has recibido y las que has realizado.
#### Conceptos necesarios
##### Función hash criptográfica (Cryptographic hash function)
Una función hash recibe como parámetro una cadena de texto (p.e: "Hello World!") y devuelve un string de longitud fija (p.e: "98b0f4b363af4aceb81bc42fd81117e1").
Para que una función hash pueda ser usada en criptografía, debe cumplir varios puntos:
- Si se introduce el mismo parámetro siempre tiene que devolver la misma salida.
- Tiene que ser fácil de computar.
- No tiene que ser posible realizar desencriptar el código (p.e: convertir "98b0f4b363af4aceb81bc42fd81117e1" en "Hello World!") a no ser que se realice mediante fuerza bruta (prueba y error).
- Un pequeño cambio en el parámetro tiene que cambiar completamente la salida generada.
- Dos parámetros diferentes no pueden generar la misma salida.
##### Criptografía asimétrica (Asymmetric cryptography)
Permite que la comunicación sea segura a través un canal inseguro.
Un típico uso es en el caso de que una persona A quiera enviar un mensaje a una persona B, y que sólo B pueda leer.
Otro caso es utilizarla para verificar quién es el emisor del mensaje, ¿realmente envió A ese mensaje?.
Este último caso es en el que estamos interesados. Bitcoin utiliza actualmente el estándar ECDSA para realizar esta función.
##### Estándar ECDSA (Elliptic Curve Digital Signature Algorithm)
Consiste en un par de claves, una privada y una pública, generados para cada entidad (p.e: la persona A, un ordenador, una dirección bitcoin..), con los cuales se puede firmar documentos de forma similar al mundo físico.
La persona A puede usar su clave privada para firmar un documento (p.e: la renta de su casa) y todo el mundo puede utilizar la clave pública de A para comprobar que realmente A es quien ha firmado el documento. No hay ninguna forma de que otra persona haya firmado el documento sin tener acceso a la clave privada de A.

##### Direcciones bitcoin (Bitcoin addresses)
Una dirección bitcoin es generada mediante varias funciones hash de una clave pública ECDSA. Por tanto, al igual que cualquier persona puede generar un par de claves pública/privada único, también puede generar direcciones bitcoin únicas. 

#### La cadena (The chain)
Una transacción es una transferencia de un valor Bitcoin de una o varias entradas a una o varias salidas.

![bitcoin_transactions](https://miro.medium.com/max/640/1*KEva3f4PHE2z7g92m2xp4A.webp)

Esto es una representación de 2 transacciones  (simplificadas a una entrada y una salida) pertenecientes a una cadena. El contenido de la caja de transacción representa cómo está firmada:
Vamos a suponer que somos el dueño 1 ("Owner 1") y estamos generando la transacción de la derecha ("Transaction" [der.]). Utilizamos la clave pública de la persona destinataria ("Owner 2's Public Key") y la transacción anterior ("Transaction" [izq.]) para crear la cadena ("Hash" [der.]), la cual firmaremos utilizando nuestra clave privada.
La cadena ("Hash") se crea para establecer un tamaño fijo y que éste no sea cada vez mayor. De esta forma se aumenta la velocidad.
Una vez generada la transacción, ¿cómo sabemos que podemos gastar los bitcoin que tenemos asignados?. Esta es la razón por la cual el dueño 0 ("Owner 0" [no incl.]) ha incluido nuestra clave pública en su firma, al igual que hicimos nosotros con el dueño 2 ("Owner 2"). De esta forma, el dueño 0 ha firmado que tenemos derecho a gastar una determinada cantidad.

Podríamos pensar por qué necesitamos direcciones bitcoin (bitcoin adresses), si realmente estamos enviando bitcoins utilizando las claves públicas. Añadir las direcciones encima de cada transacción otorga un nivel más de seguridad. En el caso de que alguien consiga atravesar una capa de seguridad, lo único que podría conseguir es la fecha de transacción y la dirección de destino.
Para más seguridad, es recomendado utilizar una dirección y par de claves privadas diferentes para cada transacción.

#### Un ejemplo
A continuación se muestra un ejemplo de una transacción real en formato JSON.
```json
{
   "txid":"64317d1c1626ae040ba2cb48b66b8a514320e4415e7d00394bbaa5beff343a3c",
   "vin":[
      {
         "txid":"672aeb1bc62b3941f2e9a530ff6d12e5e70c257632d536d5b0633e12b68a915d",
         "vout":1,
         "scriptSig":{
            "asm":"3044022066941da0cbe35013d5f92261bb3eeaef9f9729a62dafb1ef1f743cd0fed22f2a02202f3461bcad5c9a80af0f21033de2302563998ffac394d09c14791b285b661014[ALL] 030a13a4fe430d3bf0c1e3ed5ea31e6dad19b56e5c60322a60a283d1d430acddf8"
         },
         "addr":"1HKqcNrf3NPuz4s2MdoAzpYYfjYvbbsxZf",
         "value":0.0468234
      },
      {
         "txid":"d1dc8deb93ba5a0747c898859db99c03ff5a4f50686716d6c61d757dd5c63b27",
         "vout":0,
         "scriptSig":{
            "asm":"3044022069d043bcb1401169c8e9ce88c47ebf6b973abba5302efdb44df6801af9f1d79d02202ffad54fecb31edd63c805bb7a7553d77a20ebfce820e8ac198c1898e86ffcfc[ALL] 026ed1317c4a225c461b7dbbca89332f4e2f725fe823f05bd29d4c60da4d5dbd1d"
         },
         "addr":"1CMzyZjERPYvecNcn2GDxpHCLqPCwAst3c",
         "value":0.0016471
      }
   ],
   "vout":[
      {
         "value":"0.03847050",
         "n":0,
         "scriptPubKey":{
            "asm":"OP_DUP OP_HASH160 1d49a050b1e965f59301f304bc9914378044364e OP_EQUALVERIFY OP_CHECKSIG",
            "addresses":[
               "13froCnxWczJNiJXYLQQikWygvyMFXqVUJ"
            ],
            "type":"pubkeyhash"
         }
      },
      {
         "value":"0.00775226",
         "n":1,
         "scriptPubKey":{
            "asm":"OP_DUP OP_HASH160 f362e8796d04713dda1796b3c609d4b7cd325187 OP_EQUALVERIFY OP_CHECKSIG",
            "addresses":[
               "1PBugsUY1N3TvikrtDpQBBYuMBFoQWTHXi"
            ],
            "type":"pubkeyhash"
         }
      }
   ],
   "valueOut":0.04622276,
   "valueIn":0.0484705,
   "fees":0.00224774
}
```
Primero, observamos un "txid", el cual es el id de la transacción. Es un hash basado en el contenido de la propia transacción.
Después, se pueden ver las colecciones "vin" y "vout". Son las entradas (inputs) y salidas (outputs), respectivamente.
En cada "vin" hay:
- "txid": el hash de la anterior transacción (la que nos envió los bitcoins).
- "vout": qué output se selecciona de la anterior transacción.
- "scriptSig": la firma de la transacción (explicada arriba).
- "addr": la dirección del destinatario de los bitcoins.
- "value": el número de bitcoins que son enviados.

En cada "vout" hay:
- "value": la cantidad que finalmente enviamos.
- "n": el número de salidas (output).
- "scriptPubKey": contiene la dirección ("adresses") del destinatario, el script para verificar quién puede consumir la cantidad ("asm") y el tipo de script ("type").

Por último, tenemos "valueIn", "valueOut" y "fees", los cuales son un resumen de los valores de los bitcoins de entrada y salida y la comisión que se lleva la máquina que realiza la transacción.

Según el ejemplo anterior, tenemos 0.0468234 + 0.0016471 = 0.0484705 bitcoins de entrada, de las direcciones 1HKqcNrf3NPuz4s2MdoAzpYYfjYvbbsxZf + 1CMzyZjERPYvecNcn2GDxpHCLqPCwAst3c, de los cuales, enviamos 0.0384705 a 13froCnxWczJNiJXYLQQikWygvyMFXqVUJ y 0.00775226 a 1PBugsUY1N3TvikrtDpQBBYuMBFoQWTHXi. Estamos enviando un total de 0.04622276, lo que nos deja con una comisión de 0.00224774.
En este caso específico, podríamos proponer el siguiente escenario. Una persona A (quien posee las dos direcciones de entrada), envía 0.0384705 a una persona B (quien posee la primera salida). La segunda salida pertenece a la persona A, por lo que sería el cambio que obtiene de la transacción. En caso de no haber una segunda salida, ésta se habría ido como comisión.

#### Doble gasto (Double spending)
Es un problema potencial de los sistemas de efectivo digital. Consiste en el envío simultáneo de los mismos fondos a dos destinatarios distintos. Esto proboca que los usuarios no tengan forma de verificar que los fondos que reciban no han sido gastados ya en otro sitio.

### 3. Servidor de sellado de tiempo (Timestamp server)
Un timestamp (sellado de tiempo) determina cuándo ha ocurrido un evento (p.e: convierte la fecha "04/15/2018 @ 11:56am (UTC)" en "1523793381").
Lo podemos utilizar en la generación del hash de las transacciones para guardar la fecha y hora a la que se ha producido.

### 4. Prueba de trabajo (Proof of Work) //TODO
Proof of Work (PoW) es un mecanismo para prevenir dobles gastos. La mayoría de las criptomonedas lo utilizan como un algoritmo de consenso, un método para proteger el libro mayor contable de la criptomoneda.
Necesitamos encontrar una forma de incentivar a distintas máquinas para obtener la información de cuál es el estado y el orden de las transacciones de los bloques que forman la blockchain.
Si no hubiese un coste asociado a la generación de cada bloque, sería manipulable de forma gratis para cualquier persona, lo que vulnerabilizaría el sistema.
Lo que hace bitcoin es aplicar la función hash a los encabezados de los bloques, entre los que se encuentran el hash del bloque anterior, el timestamp y el nonce, entre otros. El nonce es un número totalmente aleatorio de 32 bits.

### 5. La red (Network)
La red se comporta de la siguiente forma:
- Las nuevas transacciones se transmiten a todos los nodos.
- Cada nodo agrupa las transacciones en un bloque.
- Una vez se encuentren las transacciones, éstas son validadas.
- Una vez validadas, se ejecuta en ellas el PoW para formar el bloque.
- Una vez aplicado el PoW de un nuevo bloque, el nodo acepta la cadena (chain).

Se considera como correcta la cadena (chain) más larga, aunque las demás ramas se guardan por si acaso aumentan sus tamaños.

Existe un bloque llamado "genesis block", el cual es el primer bloque existente en la blockchain y está hardcodeado con el core de bitcoin por Satoshi Nakamoto.

### 6. Incentivos
Cada bloque minado tiene una primera transacción llamada "coinbase transaction". Es la que da la recompensa al minero por haber realizado su PoW. Así fue cómo inicialmente los bitcoins fueron puestos en circulación y la cantidad recompensada disminuye cada 210000 bloques (~4 años) a la mitad.
Otro incentivo es la tasa de transacción ("transaction fee"), la cual está definida por las entradas de transacción ("transaction inputs") no gastadas

### 7. Recuperación de espacio en disco
El tamaño de cada transacción varía dependiendo del número de entradas (inputs) y salidas (outputs).
Una buena fórmula para medirlo es la siguiente:
``` 
n_inputs*180B + n_outputs*34B + 10B + (+-n_inputs)
```
Actualmente, hay una cantidad enorme de transacciones. En caso de que queramos guardarlas todas sería muy difícil, ya que superan la capacidad de almacenamiento de muchos dispositivos.
![bitcoin_block](https://miro.medium.com/max/640/1*Vkqb67E_FcBEE-UfLUCF1w.webp)
El encabezado de bloque ("block header") sin transacciones ocupa muchísimo menos.
Por tanto, si fuésemos capaces de reducir todas las transacciones (Tx0, Tx1, Tx2, Tx3) a un único hash (Root Hash), ahorraríamos una cantidad enorme de almacenamiento sin romper los bloques.
Para ello, debemos poder relacionar todas las transacciones entre ellas. Esto se conseguirá con el árbol hash de Merkle.

#### Árbol de Merkle (Merkle Tree)
Es un árbol binario donde los nodos hoja (Hash0, Hash1...) son funciones hash aplicadas a datos (Tx0, Tx1...), y a su vez, los nodos superiores (Hash01, Hash23), son funciones hash aplicadas a la concatenación de sus respectivos nodos hijos. El nodo Root Hash es el nodo superior, está incluido en el encabezado del bloque (Block Header) y almacena las transacciones presentes.
Al realizarlo de esta forma, y no juntando todos los hashes en uno, conseguiremos un coste logarítmico a la hora de, por ejemplo, comprobar si una transacción está en un bloque.

### 8. Verificación de pago simplificada (Simplified Payment Verification) //TODO
Suponiendo que tenemos un cliente que no tiene acceso a las transacciones, sino sólo a los encabezados de los bloques, debemos encontrar una forma de comprobar que una transacción específica es válida.
![payment_verification](https://miro.medium.com/max/640/1*Iqq6mIujzYYCzg9RlaNRHA.webp)

### 9. Combinar y dividir el valor
Cuando existen numerosas transacciones dependiendo de otras, no debemos preocuparnos por recorrer el árbol entero. Simplemente debemos fijarnos en la salida de la última transacción, ya que ésta refleja el total de monedas disponibles.

### 10. Privacidad
En los bancos tradicionales, la forma de privacidad es limitando el acceso a las transacciones que se producen y a las partes que intervienen en ellas. Sin embargo, bitcoin debe anunciar publicamente cada transacción, por tanto, esto no es posible.
La privacidad se consigue manteniendo anónimas las claves públicas y/o utilizando direcciones (addreses) en su lugar. Una buena práctica es utilizar un nuevo par de claves y direcciones por cada transacción.

### Referencias
Probar el funcionamiento de firmas ECDSA:
https://kjur.github.io/jsrsasign/sample/sample-ecdsa.html
Vídeo funcionamiento de Blockchain:
https://www.youtube.com/watch?v=_160oMzblY8

### Bibliografía
https://medium.com/coinmonks/bitcoin-white-paper-explained-part-1-4-16cba783146a
https://academy.binance.com/es/articles/double-spending-explained
https://medium.com/@sgerov/bitcoin-white-paper-explained-part-2-4-d79fbc5e2adf
https://academy.binance.com/es/articles/proof-of-work-explained
https://medium.com/coinmonks/bitcoin-white-paper-explained-part-3-3-c06c1791a31b

## Elliptic Curve Cryptography
El sistema de criptografía está basado en las matemáticas de las curvas elípticas.
Una curva elíptica es un conjunto de puntos (x,y) que satisfacen la siguiente ecuación:
```
y² = x³ +ax + b
```
Una curva elíptica se vería así:
![elliptic_curve1](https://miro.medium.com/max/640/1*KKdvscN4y-NcGZ8Nnx1ZYQ.webp)

Si tomamos un punto cualquiera P=(x,y) de la curva y lo sumamos a otro punto cualquiera Q de la curva, volveremos a obtener un punto ubicado en la curva:
![elliptic_curve2](https://miro.medium.com/max/640/1*O6Hxnd6uwz6FY-AZm0ZExg.webp)

Si ahora cogemos un punto P de la curva y lo sumamos x veces a sí mismo, seguiremos obteniendo un punto perteneciente a la curva.
```
P+P+…+P = xP = R
```
Este último caso nos interesa.
Se demuestra que es computacionalmente inviable calcular el número x sólo conociendo los puntos P y R. Es el llamado problema del logaritmo discreto.
En criptografía, se elige un punto P de la curva elíptica y se genera un número natural aleatorio suficientemente grande. Este número es la clave privada (private key). Con el punto P elegido y la clave privada, se calcula el punto R en la curva, el cual será la clave pública (public key).
Dicho esto, se puede observar que las claves públicas y privadas están fuertemente conectadas entre ellas.
La clave pública no podría existir sin la privada y la privada es prácticamente imposible obtenerla a partir de la pública debido al problema del logaritmo discreto.

### Bibliografía
https://medium.com/coinmonks/learn-how-to-code-elliptic-curve-cryptography-a952dfdc20ab

## Ethereum
Ethereum es un blockchain con un ordenador incorporado en él. Es la base para crear aplicaciones y organizaciones de forma descentralizada.
En el universo Ethereum hay un único ordenador llamado Ethereum Virtual Machine (EVM), cuyo estado ha sido acordado por todos los participantes de la red. Cualquier persona que participe en la red de Ethereum (cada nodo) guarda una copia del estado de este ordenador.
Además, cualquier participante puede emitir una petición para que este ordenador realice un cálculo arbitrario (llamadas solicitudes de transacción). Cuando se emite esta solicitud, otros participantes de la red verifican, validan y ejecutan el cálculo. La ejecución causa un cambio en el estado de la EVM, el cual se realiza y propaga por toda la red.
Una vez verificadas y añadidas a la cadena de bloques, las transacciones no se pueden volver a manipular. Esto garantiza que las transacciones se firmen y ejecuten con permisos apropiados (p.e: Sólo la persona A puede enviar activos desde la cuenta de la persona A).

### Ether
Ether (ETH) es la criptomoneda de Ethereum. Su propósito es posibilitar la existencia de un mercado de computación, en el cual se proporciona un incentivo económico a los participantes que verifican y ejecutan solicitudes de transacciones y proporcionan recursos a la red.
Cualquier participante que solicite una transacción debe también ofrecer una cantidad de ether adicional a la red como recompensa para la persona que realice la verificación de la transacción, la ejecute, la registre en la cadena de bloques y la emita en la red.
La cantidad de ether a incentivar depende del tiempo necesario para completar el cálculo.
Esta cantidad también sirve para evitar que participantes maliciosos realicen ataques (p.e: spam), ya que deberán pagar por los cálculos.

### Ethereum Virtual Machine (EVM)
La EVM no se puede describir como una nube o una ola, pero sí como una única entidad sustentada por miles de ordenadores conectados ejecutando un cliente de Ethereum.
El protocolo Ethereum existe sólo para mantener el funcionamiento continuo e inmutable de esta máquina, la cual alberga todas las cuentas de Ethereum y los contratos inteligentes.
En cualquier bloque de la cadena, Ethereum tiene un único estado "canónico", y la EVM es la que define las reglas de cálculo de un nuevo estado válido de bloque a bloque.

#### Del libro de contabilidad a la máquina de estado
La analogía del libro de contabilidad es utilizada en blockchains como Bitcoin, donde existe una moneda descentralizada que utiliza herramientas fundamentales de criptografía. Esta moneda se comporta "normal" porque sigue unas reglas a la hora de modificar el libro de contabilidad (p.e: una dirección de bitcoin no puede gastar más de lo que tiene).
Por otro lado, Ethereum, sigue casi las mismas reglas aunque también permite el uso de una función mucho más poderosa: los contratos inteligentes. En lugar de un libro mayor distribuido, Ethereum es una máquina de estado distribuida.
El estado de Ethereum es una gran estructura de datos, que sostiene tanto todas las cuentas y saldos, como el estado de la máquina. Las reglas específicas de cambiar el estado de bloque a bloque las define la EVM.
![Ethereum_EVM](https://ethereum.org/static/e8aca8381c7b3b40c44bf8882d4ab930/302a4/evm.png)

#### Función de transición de estado
La EVM se comporta como una función matemática: dada una entrada, se produce una determinada salida. Por tanto, es bastante útil describir Ethereum como una función de transición de estado:
```
Y(S,T)=S'
```
Dado un estado válido anterior (S) y un nuevo conjunto de transacciones válidas (T), la función de transición de estado de Ethereum Y(S,T) produce un nuevo estado de salida válido S'.

#### Estado
El estado es una gran estructura de datos llamada Árbol de Patricia Merkle, la cual mantiene todas las cuentas enlazadas mediante los hashes reducibles a un solo hash raíz almacenado en la blockchain.

#### Instrucciones de la EVM
La EVM se ejecuta como una máquina de pila.
Durante la ejecución, la EVM mantiene una memoria temporal que no se conserva entre transacciones.
Sin embargo, los contratos contienen un Árbol Patricia Merkle de almacenamiento asociado a la cuenta en cuestión y que forma parte del estado global.
![Ethereum_EVM2](https://ethereum.org/static/9628ab90bfd02f64cf873446cbdc6c70/302a4/gas.png)

### Ethereum wallet
Las wallets (carteras) de Ethereum son aplicaciones que permiten la interacción con tu cuenta de Ethereum. Tu wallet te permite ver tu saldo, enviar transacciones y conectar con aplicaciones.
Es una herramienta para únicamente gestionar la cuenta de Ethereum. Por tanto, se puede cambiar a otras wallets sin problema.
Hay diferentes tipos de wallet:
- Dispositivos físicos de hardware que permiten mantener las criptomonedas desconectadas (mucha seguridad).
- Aplicaciones móviles que permiten acceder a los fondos desde cualquier sitio.
- De navegador web que permiten ser accedidas directamente desde el navegador.
- Extensiones de navegador que permiten interactuar con tu cuenta y aplicaciones mediante el navegador.
- Aplicaciones de escritorio que permiten gestionar los fondos deste macOS, Windows o Linux.

### Cuentas de Ethereum
Ethereum tiene dos tipos de cuenta: de propiedad externa y de contrato. Ambas pueden recibir almacenar y enviar ETH y tokens a la par que interactuar con contratos inteligentes implementados.
#### Cuenta de propiedad externa (EOA)
Cualquier persona que disponga de las claves privadas puede controlarla.
Crearla no tiene ningún coste.
Se pueden iniciar transacciones.
Las transacciones entre cuentas de propiedad externa sólo pueden ser transferencias con ETH/tokens.

#### Cuenta de contrato
Se trata de un contrato inteligente implementado en la red y controlado mediante código. 
Crear un contrato tiene un coste porque se está usando almacenamiento en la red.
Sólo se pueden enviar transacciones como respuesta a una transacción recibida.
Las transacciones de cuentas externas a una cuenta de contrato pueden activar código, que a su vez realiza muchas acciones distintas, como transferir tokens o incluso crear otro contrato.

#### Información detallada de una cuenta
Las cuentas Ethereum tienen cuatro campos:
- "nonce": un contador que indica el número de transacciones enviadas desde la cuenta. Esto asegura que las transacciones sólo se procesan una vez. En una cuenta de contrato, este número representa el número de contratos creados por la cuenta.
- "saldo": número de wei pertenecientes a esa dirección (existen 1e+18 wei por cada ETH).
- "codeHash": hash que hace referencia al código de una cuenta en la EVM. Las cuentas de contrato tienen fragmentos de código programados que pueden realizar operaciones. Este código se ejecuta si la cuenta recibe una llamada de mensaje. Este campo no se puede modificar, a diferencia del resto. Para las cuentas EOA, este hash es el de una cadena vacía.
- "storageRoot": hash del nodo raíz de un Árbol de Patricia Merkle que codifica el contenido de almacenamiento de la cuenta (por defecto está vacío).
![Ethereum_Accounts](https://ethereum.org/static/19443ab40f108c985fb95b07bac29bcb/302a4/accounts.png)

#### Pares de claves
Una cuenta está formada por un par criptográfico de claves: pública y privada, las cuales ayudan a probar que una transacción fue realmente firmada por el remitente y prevenir falsificaciones.
La clave privada se utiliza para firmar transacciones y garantiza la custodia de los fondos relacionados con la cuenta.
(Esto ya ha sido explicado más en profundidad)

#### Creación de cuentas
A la hora de crear una cuenta de Ethereum, la mayoría de bibliotecas generan una clave privada aleatoria que se puede cifrar con una contrasela.
La clave pública se genera a partir de la privada, utilizando el algoritmo de firma digital de la curva elíptica.
Las cuentas de contrato poseen además una dirección hexadecimal de 42 caracteres (más corta que las claves), la cual se asigna cuando un contrato se implementa en la cadena de bloques de Ethereum y se obtiene de la dirección del creador y el número de transacciones enviadas desde esa dirección (el "nonce").

### Transacciones
Las transacciones son instrucciones firmadas criptográficamente que se emiten desde cuentas. Una cuenta iniciará una transacción para actualizar el estado de la red Ethereum. La transacción más sencilla es transferir ETH de una cuenta a otra.
![Ethereum_Transactions1](https://ethereum.org/static/570dedb843948d6bef5e21a6769d5c35/302a4/tx.png)
Modifican el estado de la EVM y se deben transmitir a toda la red.
Cualquier nodo puede transmitir una solicitud de una transacción que se va a ejecutar en la EVM; a continuación, un minero ejecutará la transacción y propagará la modificación de estado derivada al resto de la red.
Las transacciones implican el pago de una comisión y deben minarse para convertirse en transacciones válidas.

Incluyen la siguiente información:
- ```from```: identificador del remitente, generado cuando, mediante la clave privada, se firma la transacción y se confirma que el remitente la ha autorizado.
- ```to```: la dirección del destinatario (si es una EOA, se transerirá valor. Si es una cuenta de contrato, se ejecutará el código de contrato).
- ```nonce```: un contador incremental que indica el número de transacción de la cuenta.
- ```value```: cantidad de ETH a transferir (en WEI).
- ```data```: campo opcional para incluir datos.
- ```gasLimit```: la cantidad máxima de unidades de gas que pueden ser consumidas en la transacción.
- ```maxPriorityFeePerGas```: la cantidad máxima de gas que se incluirá como propina al validador.
- ```maxFeePerGas```: la cantidad máxima a pagar deseada para la transacción.

El gas es una referencia al cálculo necesario para que el minero procese la transacción. Los usuarios tienen que pagar una comisión por ese cálculo. Los valores ```gasLimit``` y ```maxPriorityFeePerGas``` determinan la comisión por transacción máxima que se le paga al minero.

A continuación se muestra un ejemplo de cómo se verá el objeto de la transacción:
```json
{
  "from": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
  "to": "0xac03bb73b6a9e108530aff4df5077c2b3d481e5a",
  "gasLimit": "21000",
  "maxFeePerGas": "300",
  "maxPriorityFeePerGas": "10",
  "nonce": "0",
  "value": "10000000000"
}
```
Sin embargo, es necesario firmar este objeto mediante la clave privada del emisor, y así demostrar que la transacción no ha sido enviada de forma fraudulenta.
El proceso de firma se puede realizar con un cliente de Ethereum como Geth.

Ejemplo de una llamada para realizar la firma:
```json
{
  "id": 2,
  "jsonrpc": "2.0",
  "method": "account_signTransaction",
  "params": [
    {
      "from": "0x1923f626bb8dc025849e00f99c25fe2b2f7fb0db",
      "gas": "0x55555",
      "maxFeePerGas": "0x1234",
      "maxPriorityFeePerGas": "0x1234",
      "input": "0xabcd",
      "nonce": "0x0",
      "to": "0x07a565b7ed7d7a678680a4c162885bedbb695fe0",
      "value": "0x1234"
    }
  ]
}
```
Ejemplo de respuesta:

```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "result": {
    "raw": "0xf88380018203339407a565b7ed7d7a678680a4c162885bedbb695fe080a44401a6e4000000000000000000000000000000000000000000000000000000000000001226a0223a7c9bcf5531c99be5ea7082183816eb20cfe0bbc322e97cc5c7f71ab8b20ea02aadee6b34b45bb15bc42d9c09de4a6754e7000908da72d48cc7704971491663",
    "tx": {
      "nonce": "0x0",
      "maxFeePerGas": "0x1234",
      "maxPriorityFeePerGas": "0x1234",
      "gas": "0x55555",
      "to": "0x07a565b7ed7d7a678680a4c162885bedbb695fe0",
      "value": "0x1234",
      "input": "0xabcd",
      "v": "0x26",
      "r": "0x223a7c9bcf5531c99be5ea7082183816eb20cfe0bbc322e97cc5c7f71ab8b20e",
      "s": "0x2aadee6b34b45bb15bc42d9c09de4a6754e7000908da72d48cc7704971491663",
      "hash": "0xeba2df809e7a612a0a0d444ccfa5c839624bdc00dd29e3340d46df3870f8a30e"
    }
  }
}
```
- La propiedad ```raw``` es la transacción firmada en Recursive Length Prefix (RLP).
- La propiedad ```tx``` es la transacción firmada en formato JSON.

#### Tipos de transacciones
En Ethereum hay algunos tipos diferentes de transacciones:
- Transacciones regulares: una transacción desde una cartera a otra.
- Transacciones de despliegue de contratos: una transacción sin la dirección "a", donde el campo de datos se usa para el código de contrato.
- Ejecución de un contrato: una transacción que interactúa con un contrato desplegado. En este caso, la dirección "a" es la dirección del contrato.

Tal y se ha mencionado, las transacciones necesitan gas para ejecutarse. Las transacciones de transferencia simple requieren 21.000 unidades de gas.
De modo que, para que Bob pueda enviar a Alice 1 ETH con un coste de baseFeePerGas de 190 gwei y de maxPriorityFeePerGas de 10 gwei, Bob tendrá que pagar la siguiente comisión:
```
(190 + 10) * 21000 = 4,200,000 gwei
--or--
0.0042 ETH
```
- A la cuenta de Bob se le restarán -1,0042 ETH
- A la cuenta de Alice se añadirán +1,0 ETH
- La comisión base que se quemará será de 0,00399 ETH
- El minero se queda con la propina (+0.000210 ETH)

El gas también es necesario para cualquier interacción del contrato inteligente.
Cualquier gas no utilizado en una transacción es reembolsado a la cuenta de usuario.
![Ethereum_EVM_Gas](https://ethereum.org/static/c3638b26a1210d2c73a7ec2335c57351/302a4/gas-tx.png)

#### Ciclo de vida de una transacción
Una vez que la transacción ha sido enviada ocurre lo siguiente:
1. Una vez que envíes una transacción, la criptografía genera un hash de transacción: 0x97d99bc7729211111a21b12c933c949d4f31684f1d6954ff477d0477538ff017
2. A continuación, la transacción se transmite a la red y se incluye en un pool con muchas otras transacciones.
3. Un minero debe elegir tu transacción e incluirla en un bloque para verificar la transacción y considerarla "exitosa".
    - Puede que deba esperar en esta fase si la red está ocupada y los mineros no son capaces de mantenerse al día.
4. Tu transacción recibirá «confirmaciones». El número de confirmaciones indica el número de bloques creados desde el bloque en el cual se incluyó su transacción. Cuanto mayor sea el número, mayor será la certeza de que la red procesó y reconoció la transacción.
    - Los bloques recientes pueden sufrir un proceso de reorganización, con lo que dará la impresión de que la transacción ha fallado. Sin embargo, es posible que la transacción todavía sea válida pero que se incluya en otro bloque.
    - La probabilidad de que se lleve a cabo una reorganización disminuye con cada bloque minado posterior, es decir, cuanto mayor es el número de confirmaciones, más inmutable es la transacción.

#### Typed transaction envelope
Inicialmente, Ethereum tenía un formato único para las transacciones. Cada transacción contenía un nonce, un precio de gas, un límite de gas, una dirección, un importe, datos, y v, r y s. Estos campos se codifican en RLP, y tiene esta apariencia:

```RLP([nonce, gasPrice, gasLimit, to, value, data, v, r, s])```

Hoy en día, Ethereum ha mejorado y ahora es compatible con múltiples tipos de transacciones, lo que permite que se implementen nuevas características como listas de acceso y EIP-1559 sin afectar los formatos de transacción antiguos.

EIP-2718: Typed Transaction Envelope se refiere a un tipo de transacción que funciona como un sobre para futuros tipos de transacción.

El EIP-2718 es un nuevo sobre generalizado para transacciones escritas. En el nuevo modelo, las transacciones se interpretan de la siguiente forma:

```TransactionType || TransactionPayload```

Donde los nuevos campos indican:

- ```TransactionType``` - un número entre 0 y 0x7f, para un total de 128 posibles tipos de transacción.
- ```TransactionPayload``` - una matriz de bytes arbitraria definida según el tipo de transacción.

#### Gas
El gas hace referencia a la unidad que mide la cantidad de esfuerzo computacional requerida para ejecutar operaciones específicas en la red de Ethereum.
Como cada transacción de Ethereum requiere recursos computacionales para ejecutarse, cada transacción requiere una comisión. El gas hace referencia a la comisión necesaria para llevar a cabo una transacción en Ethereum con éxito.
![Ethereum_gas](https://ethereum.org/static/9628ab90bfd02f64cf873446cbdc6c70/302a4/gas.png)
Las comisiones de gas se pagan en ether (ETH).
Los precios del gas están indicados en Gwei (1 Gwei = 0,000000001 ETH ó 10-9 ETH) y significa "giga-wei" (1 Gwei = 1.000.000.000 wei).
El wei es la unidad más pequeña de ETH.

##### Antes de la actualización de Londres
Se calculaba el gas de la siguiente forma:
Supongamos que Alice tiene que pagar 1 ETH a Bob. En la transacción, el límite de gas es de 21.000 unidades y el precio del gas es de 200 gwei.
El coste total hubiera sido de:

```Gas units (limit) * Gas price per unit```

Aplicando esta fórmula al problema nos queda:
```21,000 * 200 = 4,200,000 gwei o 0,0042 ETH```

Cuando Alice enviase el dinero, se deducirían 1,0042 ETH de la cuenta de Alice. A Bob se le acreditaría 1,0000 ETH. El minero recibiría 0,0042 ETH.

##### Después de la actualización de Londres
Ahora, cada bloque tiene:
- Una comisión base: precio mínimo por unidad de gas para la inclusión en este bloque, la cual se calcula mediante la red en función de los requisitos de espacio del bloque.
- Una propina: Debido a que la comisión base está quemada, se espera que los usuarios establezcan también una propina para los mineros.

Para calcular el total de la comisión por transacción se sigue esta fórmula:

```Gas units (limit) * (Base fee + Tip)```

Supongamos que Jordan debe pagar a Taylor 1 ETH. En la transacción, el límite de gas es de 21.000 unidades y la comisión base es 100 gwei. Jordan incluye una propina de 10 gwei.

Utilizando la fórmula anterior podemos calcular esto como:
```21,000 * (100 + 10) = 2,310,000 gwei o 0,00231 ETH```

Lo que se traduce en: cuando Jordan envía el dinero, se deducirán 1,00231 ETH de la cuenta de Jordan. A Taylor se le acreditarán 1,0000 ETH. El minero recibe la propina de 0,00021 ETH. Se aplica una comisión base de 0,0021 ETH.

Asimismo, Jordan también puede establecer una comisión máxima (maxFeePerGas) para esa transacción. La diferencia entre la comisión máxima y la comisión real se le reintegra a Jordan, es decir, ```refund = max fee - (base fee + priority fee)```. Jordan puede establecer una cantidad máximo a pagar para que la transacción se ejecute, sin preocuparse de pagar una cantidad superior a la comisión base cuando se ejecute la transacción.

##### ¿Por qué existen comisiones de gas?
En resumen, las comisiones de gas ayudan a mantener la seguridad de la red de Ethereum. Al requerir una comisión por cada operación ejecutada en la red, prevenimos que los actores maliciosos envíen spam a la red. Para prevenir la generación de bucles hostiles infinitos o accidentales, así como de otros desperdicios computacionales generados en el código, cada transacción debe establecer un límite del número de pasos computacionales de ejecución de código que puede utilizar. La unidad fundamental del cálculo computacional es el gas.

Aunque una transacción incluye un límite, el gas no utilizado en una transacción se devuelve al usuario (es decir, se devuelve ```max fee - (base fee + tip)```).

#### MetaMask
MetaMask es una de las carteras de criptomonedas (crypto wallets) más grandes actualmente.
Se basa en la integración en el navegador y abre puertas para conectarse al mundo Web3, DeFi y NFTs

Consiste en un plugin de navegador que ofrece una cartera de Ethereum y se instala como cualquier otra extensión.
Una vez instalado, permite al usuario almacenar ETH y otros tokens ERC-20, habilitando las transacciones con cualquier dirección Ethereum.

También habilita la conexión con aplicaciones descentralizadas basadas en Ethereum, lo que nos permite gastar monedas en juegos, stakear tokens, hacer trading en exchanges descentralizados, etc.

![Metamask](https://img.decrypt.co/insecure/rs:fit:950:0:0:0/plain/https://cdn.decrypt.co/wp-content/uploads/2019/01/image2.png@webp)

### Nodos y Clientes
Un "Nodo" es una pieza de software cliente en ejecución.
Un "Cliente" es una implementación de Ethereum, que verifica todas las transacciones en cada bloque, manteniendo la red segura y la precisión de los datos.

Representación de las características del cliente de Ethereum:
![Ethereum_Client](https://ethereum.org/static/47d8930ceed4a270e55737d7740bcf9c/cf4cc/client-diagram.png)

#### Tipos de Nodos
- Nodo completo:
    - Almacena datos completos de la cadena de bloques.
    - Participa en la validación de bloques, verifica todos los bloques y estados.
    - Todos los estados pueden derivarse de un nodo completo.
    - Sirve a la red y proporciona datos si se le solicita.
- Nodo ligero:
    - Almacena la cadena de cabecera y solicita todo lo demás.
    - Puede verificar la validez de los datos contra las raíces del estado en las cabeceras de bloques.
    - Es útil para dispositivos de baja capacidad, como dispositivos incrustados o teléfonos móviles, que no pueden permitirse almacenar gigabytes de datos de blockchain.
- Nodo de almacenamiento:
    - Almacena todo lo que se guarda en el nodo completo y construye un archivo de estados históricos. Esto es necesario si quieres consultar algún elementos como el saldo de una cuenta en el bloque número 4.000.000 o simplemente probar sus propias transacciones sin minarlas usando OpenEthereum.
    - Estos datos representan unidades de terabytes lo que hace que los nodos de archivo sean menos atractivos para los usuarios medios, pero pueden ser útiles para servicios como los exploradores de bloques, proveedores y análisis de cadena.

#### ¿Por qué debería ejecutar un nodo de Ethereum?
Ejecutar un nodo permite usar Ethereum de forma confiable y privada mientras das soporte al ecosistema.
Permite utilizar Ethereum de una manera realmente privada, autosuficiente y sin confianza. No se necesita confiar en la red porque uno mismo puede verificar los datos con su cliente. "No confíes, verifica" es un mantra popular en blockchain.

Si ejecuta un nodo completo, toda la red Ethereum se beneficia de él.. Un conjunto diverso de nodos es importante para la salud, seguridad y resiliencia operativa de Ethereum.

![Ethereum_Node](https://ethereum.org/static/aab39e6ce2a2a0ec074d19c4613281c1/ac25d/nodes.png)

#### Go-Ethereum
Go Ethereum (Geth, para abreviar) una de las implementaciones originales del protocolo de Ethereum. Actualmente, es el cliente más difundido con la mayor base de usuarios y variedad de herramientas para usuarios y desarrolladores. Está escrito en Go, es de código totalmente abierto y se comercializa con la licencia GNU LGPL v3.

### Infura
Infura se ha diseñado para hacer más fácil la vida a los desarrolladores. Ahora, en lugar de crear y mantener su propio nodo para lanzar su aplicación en Ethereum, los desarrolladores pueden dejar que los “nodos como servicio” de Infura se ocupen de ese trabajo. Esto tiene ventajas importantes para el universo Web3 en desarrollo.

Sin embargo, vuelve la centralización; muchas dApps utilizan Infura como proveedor de nodos, por lo que los problemas de Infura son problemas de todo el sistema.
Infura es un servicio centralizado, por lo que es posible que un gobierno o un tercero realice un seguimiento de este servicio y censure operaciones. Esto va contra el principio fundamental del espacio descentralizado y elimina lo que hace de la Web3 algo único.

### Referencias
Vídeo de pares de claves:
https://youtu.be/QJ010l-pBpE
Vídeo de transacciones:
https://youtu.be/er-0ihqFQB0
Calculadora de precios del gas:
https://etherscan.io/gastracker
Mapa de Nodos Ethereum en tiempo real:
https://etherscan.io/nodetracker

### Bibliografía
https://ethereum.org/en/developers/docs/
https://www.ledger.com/es/academy/que-es-infura

## Contratos Inteligentes (Smart Contracts)
Un contrato inteligente es un programa que se ejecuta en la blockchain de Ethereum.
Es un grupo de código (funciones) y datos (su estado) que existe en una dirección específica en la blockchain de Ethereum.

Los contratos inteligentes son un tipo de cuenta de Ethereum. Esto significa que tienen un saldo y pueden enviar transacciones por la red. Sin embargo, no están controlados por un usuario, sino que están implementados en la red y se ejecutan como se hayan programado. Las cuentas de usuario pueden interactuar con un contrato inteligente enviando transacciones que ejecuten una función definida en el contrato inteligente. Los contratos inteligentes pueden definir reglas, como un contrato normal, y automáticamente se ejecutan a través del código.

### Metáfora de la máquina expendedora
Para explicar mejor los contratos inteligentes, se puede utilizar la metáfora de una máquina expendedora, donde, con las entradas adecuadas se garantiza una producción.

Para obtener un snack de una máquina expendedora:
```dinero + selección del snack = obtención del snack```

En un contrato inteligente, se podría expresar de la siguiente forma:
```js
pragma solidity 0.8.7;

contract VendingMachine {

    // Declarar las variables del estado del contrato
    address public owner;
    mapping (address => uint) public cupcakeBalances;

    // Cuando se implementa el contrato "VendingMachine":
    // 1. configurar la dirección de implantación como el propietario del contrato
    // 2. configurar el saldo de magdalenas del contrato inteligente implementado en 100
    constructor() {
        owner = msg.sender;
        cupcakeBalances[address(this)] = 100;
    }

    // Permitir que el propietario aumente el saldo de magdalenas del contrato inteligente
    function refill(uint amount) public {
        require(msg.sender == owner, "Only the owner can refill.");
        cupcakeBalances[address(this)] += amount;
    }

    // Permitir que cualquier persona compre magdalenas
    function purchase(uint amount) public payable {
        require(msg.value >= amount * 1 ether, "You must pay at least 1 ETH per cupcake");
        require(cupcakeBalances[address(this)] >= amount, "Not enough cupcakes in stock to complete this purchase");
        cupcakeBalances[address(this)] -= amount;
        cupcakeBalances[msg.sender] += amount;
    }
}
```
Del mismo modo que una máquina expendedora elimina la necesidad de un empleado, los contratos inteligentes pueden sustituir los intermediarios en muchas industrias.

### Sin permiso
Cualquiera puede escribir e implementar un contrato inteligente.
Sólo es necesario aprender un lenguaje de contrato inteligente (Solidity o Vyper) y tener una cantidad suficiente de ETH en la cuenta.

Implementar un contrato inteligente es una transacción, por tanto, es necesario pagar gas. Sin embargo, los costes de gas son mucho más elevados.

### Composición de contratos
Los contratos inteligentes son públicos en Ethereum. Por tanto, se puede acceder a otros contratos desde un contrato. Los contratos pueden incluso implementar otros contratos.

### Limitaciones
Los contratos inteligentes no pueden obtener información sobre eventos del mundo real porque no pueden enviar solicitudes HTTP.

Esto se debe a que confiar en información externa puede perjudicar la seguridad y la descentralización. 

### Ciclo de vida
#### 1. Crear
Es importante la negociación y reiteración en la primera fase. Las partes involucradas deben llegar a un consenso sobre los términos que se enumeran en el contrato. Es muy similar a las negociaciones de contratos tradicionales que estamos acostumbrados a hacer físicamente, solo que se mantienen digitalmente.

Los participantes del contrato también deben tener una billetera en la cadena de bloques que se utiliza para redactar el contrato inteligente. Una vez finalizado el contenido del contrato, éste debe ser codificado. Debido a la naturaleza personalizada de cada contrato inteligente, la codificación a veces se vuelve difícil. La mayoría de los desarrolladores de blockchain, por lo tanto, proporcionan los medios para probar el comportamiento de un contrato inteligente en el momento de la creación para imitar el comportamiento real del mismo.

Este requisito multiiterativo a menudo justifica una mayor comunicación entre las partes que realizan la transacción y el programador. Tras el acuerdo mutuo de los términos después de la codificación, el contrato inteligente se carga en la red blockchain y se vuelve irreversible. Si es necesario volver a modificar los términos, se debe crear un nuevo contrato.

#### 2. Congelar
Las transacciones en una cadena de bloques son validadas por un conjunto de computadoras a través de la red llamadas nodos. Estos nodos no son más que mineros de blockchain que dedican la potencia informática a su disposición para garantizar una gobernanza justa del contrato inteligente. A cambio de sus servicios, estos mineros también reciben una pequeña tarifa. Este marco garantiza que la cadena de bloques solo tenga contratos legítimos y no esté obstruida por entradas falsas.

Durante la fase de ‘congelación’, el contrato y sus participantes quedan abiertos al público en el libro mayor público. Cualquier tipo de transferencia de fondos está bloqueada durante este período ya que los nodos actúan como un órgano de gobierno que verifica si se han cumplido las condiciones previas para la ejecución del contrato.

#### 3. Ejecutar
Los nodos de autenticación verifican la integridad de un contrato inteligente y el motor de interferencia del contrato (o el compilador) ejecuta el código. Cuando las entradas de una de las partes se reciben en forma de monedas (como un compromiso de intercambio de bienes), el motor de interferencia crea una transacción activada por los criterios cumplidos.

Luego, los nuevos datos de transacción se agregan a la cadena de bloques y los nodos de control los verifican una vez más para garantizar el cumplimiento de acuerdo con los términos acordados en el contrato. Este proceso de verificación se rige por el ‘mecanismo de consenso’, es decir, Prueba de trabajo (los mineros comprometen poder de cómputo a la cadena de bloques para convertirse en nodos) o Prueba de participación (los mineros asignan criptomonedas a la cadena de bloques para convertirse en nodos).

#### 4. Finalizar
Una vez que los datos de la transacción se han escrito en el libro mayor distribuido de la cadena de bloques, el mecanismo de consenso verifica que los activos transferidos por la primera parte se hayan recibido y los descongela para la parte receptora. Esto marca la finalización del contrato inteligente, que luego se cierra y registra. No se puede modificar ni alterar, un concepto llamado ‘finalidad’.

#### ¿Se pueden destruir los contratos inteligentes?
La cadena de bloques de Ethereum permite una disposición para ejecutar la función de autodestrucción, en caso de que algo salga mal. Para los desarrolladores, esta es una espada de doble filo ya que esta función permite la transferencia de fondos etiquetando la situación como una emergencia. Esto proporciona un canal para que los atacantes cibernéticos también obtengan transferencias ilegítimas de fondos. Esta vulnerabilidad agrega complejidad a la codificación de un contrato inteligente.

Sin embargo, cuando se descubren tales fallas, los desarrolladores también agregan protocolos actualizados para implementar medidas de seguridad reforzadas. Una vez que se cierran las brechas, se crea un nuevo contrato utilizando los protocolos actualizados.

### Solidity
Solidity es un lenguaje de programación. Pero no está diseñado para crear programas normales, sino que es un lenguaje específicamente creado para programar contratos inteligentes. Su sintaxtis está basada en ECMAScript, y similar a otros lenguajes como JavaScript y C, pero con la diferencia de implementar un tipado fuerte a la hora de declarar el tipo de variables y argumentos. Esto es así para garantizar el rigor del contrato.

Además, debido a la similitud entre la cadena de bloques de Ethereum y otras similares como Polygon o Binance, Solidity también se puede implementar en otras redes de forma que su funcionamiento siga siendo predecible. Su compilador analizará el código del contrato en tiempo de ejecución para verificar que intentamos realizar la operación adecuada con el tipo de valor adecuado.

Para empezar a programar con Solidity existen varios programas. Sin embargo, uno de los más recomendados es Remix IDE. Se trata de un entorno de desarrollo basado en el navegador, desde el se pueden escribir, compilar a implementar los contratos inteligentes.

### Referencias
Cómo llamar a un contrato inteligente desde JS: 
https://ethereum.org/es/developers/tutorials/calling-a-smart-contract-from-javascript/
web3.js interactúa con contratos inteligentes:
https://programmerclick.com/article/4316865055/

### Bibliografía
https://ethereum.org/es/developers/docs/
https://101noticias.com/ciclo-de-vida-de-los-contratos-inteligentes-en-una-cadena-de-bloques/
https://www.xataka.com/basics/solidity-que-sirve-este-lenguaje-programacion