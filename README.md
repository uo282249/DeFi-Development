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
### Introducción
El dinero físico permite realizar transferencias de dinero sin intermediarios. En cambio, si se desea realizar de forma digital, se necesita una entidad de por medio (p.e: un banco), lo que implica:
- Se cobrará una comisión por la transacción.
- Se guardará información de las partes implicadas en la transacción.

Lo que buscamos es encontrar una forma de realizar pagos de forma digital la cual sea segura y sin interferencias de mediadores externos, evitando así los dos puntos mencionados anteriormente.

### Transacciones
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

### La cadena (The chain)
Una transacción es una transferencia de un valor Bitcoin de una o varias entradas a una o varias salidas.

![bitcoin_transactions](https://miro.medium.com/max/640/1*KEva3f4PHE2z7g92m2xp4A.webp)
Esto es una representación de 2 transacciones  (simplificadas a una entrada y una salida) pertenecientes a una cadena. El contenido de la caja de transacción representa cómo está firmada:
Vamos a suponer que somos el dueño 1 ("Owner 1") y estamos generando la transacción de la derecha ("Transaction" [der.]). Utilizamos la clave pública de la persona destinataria ("Owner 2's Public Key") y la transacción anterior ("Transaction" [izq.]) para crear la cadena ("Hash" [der.]), la cual firmaremos utilizando nuestra clave privada.


### Referencias
Probar el funcionamiento de firmas ECDSA:
https://kjur.github.io/jsrsasign/sample/sample-ecdsa.html
### Bibliografía
https://medium.com/coinmonks/bitcoin-white-paper-explained-part-1-4-16cba783146a
