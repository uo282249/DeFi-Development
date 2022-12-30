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
```json
{
  from: "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
  to: "0xac03bb73b6a9e108530aff4df5077c2b3d481e5a",
  gasLimit: "21000",
  maxFeePerGas: "300",
  maxPriorityFeePerGas: "10",
  nonce: "0",
  value: "10000000000"
}
```

### Referencias
Vídeo de pares de claves:
https://youtu.be/QJ010l-pBpE

### Bibliografía
https://ethereum.org/en/developers/docs/





