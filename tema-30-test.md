# Tema 30 — Test de Autoevaluación

> **Título**: Administración de redes de área local. Gestión de usuarios. Gestión de dispositivos. Monitorización y control de tráfico.
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-27
> **Fuentes**: ver tema-30-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: Arquitectura LAN, segmentación, VLAN y redundancia (P1-P12), DHCP y DNS (P13-P20), Directorio, autenticación, directivas y roles (P21-P32), Gestión de dispositivos de red y de puesto (P33-P44), Monitorización, calidad de servicio, análisis de tráfico, registros y ENS (P45-P60).

---

### Pregunta 1

**En el modelo jerárquico de tres capas de una red de campus, ¿cuál es la función propia de la capa de distribución?**

A) Conectar directamente los equipos de usuario aplicando calidad de servicio y control de admisión
B) Agregar los conmutadores de acceso, encaminar entre VLAN y aplicar las políticas de filtrado
C) Transportar tráfico a la máxima velocidad posible sin aplicar ninguna política

<details><summary>Respuesta</summary>

**Correcta: B) Agregar los conmutadores de acceso, encaminar entre VLAN y aplicar las políticas de filtrado** La regla de oro del modelo es que la política se aplica en la distribución y el núcleo se limita a transportar. La opción A describe la capa de acceso y la C, la de núcleo.

*Referencia: §1.1.1 [SWITCH-VENDORS]*
</details>

---

### Pregunta 2

**¿Qué reduce realmente la segmentación de una red en VLAN?**

A) El dominio de difusión
B) El dominio de colisión
C) El retardo de propagación de la señal en el medio físico

<details><summary>Respuesta</summary>

**Correcta: A) El dominio de difusión** Cada VLAN delimita un dominio de difusión. Los dominios de colisión los eliminó la conmutación: cada puerto de un conmutador es ya un dominio de colisión propio. Confundir ambos es el error más repetido del temario.

*Referencia: §1.1.1 [IEEE8023] [IEEE8021Q]*
</details>

---

### Pregunta 3

**¿Cuántos bits tiene el campo VID de la etiqueta 802.1Q y cuántas VLAN son utilizables?**

A) 10 bits y 1022 VLAN utilizables
B) 12 bits y 4096 VLAN utilizables
C) 12 bits y 4094 VLAN utilizables

<details><summary>Respuesta</summary>

**Correcta: C) 12 bits y 4094 VLAN utilizables** Doce bits dan 4096 valores posibles, pero el 0 y el 4095 están reservados, de modo que las VLAN utilizables son las numeradas del 1 al 4094.

*Referencia: §1.1.2 [IEEE8021Q]*
</details>

---

### Pregunta 4

**¿Qué valor tiene el campo TPID de una trama etiquetada según 802.1Q y cuánto ocupa la etiqueta completa?**

A) 0x8100, y la etiqueta ocupa 4 bytes
B) 0x0800, y la etiqueta ocupa 2 bytes
C) 0x8100, y la etiqueta ocupa 8 bytes

<details><summary>Respuesta</summary>

**Correcta: A) 0x8100, y la etiqueta ocupa 4 bytes** La etiqueta se compone de TPID (16 bits, valor fijo 0x8100), PCP (3 bits), DEI (1 bit) y VID (12 bits): 32 bits en total, es decir, 4 bytes. Por eso la trama etiquetada mide 4 bytes más.

*Referencia: §1.1.2 [IEEE8021Q]*
</details>

---

### Pregunta 5

**Un puerto configurado como troncal transporta las VLAN 10, 20 y 30, y tiene declarada la VLAN 99 como nativa. ¿Cómo circula el tráfico de la VLAN 99 por ese enlace?**

A) No circula: la VLAN nativa queda bloqueada en los troncales
B) Circula etiquetada con el VID 99, como las demás
C) Circula sin etiquetar

<details><summary>Respuesta</summary>

**Correcta: C) Circula sin etiquetar** La VLAN nativa es precisamente la única cuyo tráfico viaja sin etiqueta por el troncal. Si los dos extremos declaran VLAN nativas distintas, el tráfico de una acaba silenciosamente en la otra, y ese desajuste es también la base del ataque de salto de VLAN por doble etiquetado.

*Referencia: §1.1.2 [IEEE8021Q]*
</details>

---

### Pregunta 6

**Dos equipos están conectados al mismo conmutador, uno en la VLAN 10 y otro en la VLAN 20. ¿Pueden comunicarse entre sí?**

A) Sí, porque están en el mismo conmutador y el nivel 2 los une automáticamente
B) Solo si interviene un dispositivo de nivel 3: un encaminador o el propio conmutador con una interfaz virtual de VLAN
C) Sí, siempre que el puerto de ambos esté configurado como troncal

<details><summary>Respuesta</summary>

**Correcta: B) Solo si interviene un dispositivo de nivel 3: un encaminador o el propio conmutador con una interfaz virtual de VLAN** Dos VLAN nunca se comunican en el nivel 2. Esa frontera de encaminamiento es además el punto natural donde aplicar las listas de control de acceso, porque todo el tráfico entre segmentos está obligado a pasar por ella.

*Referencia: §1.1.2 [IEEE8021Q]*
</details>

---

### Pregunta 7

**¿En qué norma quedó integrado el protocolo rápido de árbol de expansión, publicado inicialmente como 802.1w?**

A) En la norma 802.1Q, junto con el árbol de expansión múltiple
B) En la norma 802.1AX, junto con la agregación de enlaces
C) En la edición 802.1D-2004

<details><summary>Respuesta</summary>

**Correcta: C) En la edición 802.1D-2004** El RSTP se publicó como 802.1w-2001 y se incorporó a la edición de 2004 de 802.1D. El árbol de expansión múltiple (MSTP), publicado como 802.1s, es el que quedó integrado en 802.1Q.

*Referencia: §1.1.3 [IEEE8021D] [IEEE8021Q]*
</details>

---

### Pregunta 8

**¿Cómo se determina el puente raíz en una topología con árbol de expansión?**

A) Es el conmutador con el menor identificador de puente, formado por una prioridad configurable y su dirección MAC
B) Es el conmutador con mayor número de puertos activos
C) Es el primer conmutador que se encendió en el dominio

<details><summary>Respuesta</summary>

**Correcta: A) Es el conmutador con el menor identificador de puente, formado por una prioridad configurable y su dirección MAC** Como la prioridad se configura, la elección del raíz es una decisión de diseño y debe fijarse expresamente en un conmutador de distribución o de núcleo. Dejarla al azar de las direcciones MAC es un error de diseño frecuente.

*Referencia: §1.1.3 [IEEE8021D]*
</details>

---

### Pregunta 9

**Un usuario conecta un pequeño conmutador doméstico a la roseta de su despacho. ¿Qué combinación de protecciones evita que eso altere la topología de la red?**

A) Seguridad de puerto más inspección ARP dinámica
B) Puerto de borde más guarda de BPDU, complementados con guarda de raíz
C) Control de tormentas más agregación de enlaces

<details><summary>Respuesta</summary>

**Correcta: B) Puerto de borde más guarda de BPDU, complementados con guarda de raíz** El puerto de borde hace que el puerto pase a reenviar de inmediato para el usuario legítimo, y la guarda de BPDU lo deshabilita en cuanto recibe una BPDU, que es la señal inequívoca de que se ha conectado un conmutador. La guarda de raíz impide además que ese equipo se convierta en puente raíz.

*Referencia: §1.1.3 [IEEE8021D]*
</details>

---

### Pregunta 10

**Se agregan cuatro enlaces de 1 Gbit/s entre dos conmutadores mediante 802.1AX con LACP. ¿Qué capacidad obtiene una única transferencia de fichero entre dos equipos?**

A) 1 Gbit/s, porque el reparto se hace por flujo y una conversación no se divide entre varios enlaces
B) 4 Gbit/s, porque los enlaces se suman también para cada conversación individual
C) 2 Gbit/s, porque la agregación reserva la mitad de los enlaces para redundancia

<details><summary>Respuesta</summary>

**Correcta: A) 1 Gbit/s, porque el reparto se hace por flujo y una conversación no se divide entre varios enlaces** La función de dispersión asigna cada flujo a un enlace concreto para no entregar los paquetes desordenados. La agregación suma capacidad agregada, no capacidad por conversación.

*Referencia: §1.1.3 [IEEE8021AX]*
</details>

---

### Pregunta 11

**¿Cuál es el protocolo estándar para dotar de redundancia a la puerta de enlace predeterminada de una VLAN?**

A) LACP
B) MSTP
C) VRRP

<details><summary>Respuesta</summary>

**Correcta: C) VRRP** VRRP permite que dos encaminadores compartan una dirección IP virtual, de modo que la caída del activo sea transparente para los equipos de usuario. HSRP y GLBP son los equivalentes propietarios. LACP negocia agregaciones de enlaces y MSTP es una variante del árbol de expansión.

*Referencia: §1.1.3 [RFC2328] [PROPIETARIOS]*
</details>

---

### Pregunta 12

**¿Qué ventaja específica aporta MSTP frente a RSTP?**

A) Elimina por completo la necesidad de bloquear puertos redundantes
B) Permite agrupar VLAN en instancias con árboles distintos, repartiendo la carga entre los enlaces
C) Reduce el tiempo de convergencia de segundos a milisegundos

<details><summary>Respuesta</summary>

**Correcta: B) Permite agrupar VLAN en instancias con árboles distintos, repartiendo la carga entre los enlaces** Con RSTP se bloquea siempre el mismo enlace para todas las VLAN; con MSTP cada instancia puede tener su propio raíz y usar un camino distinto. Quien elimina el bloqueo es la agregación de enlaces, no MSTP.

*Referencia: §1.1.3 [IEEE8021Q]*
</details>

---

### Pregunta 13

**¿Cuáles son los cuatro mensajes del ciclo DORA de DHCP y cuáles de ellos envía el cliente en difusión?**

A) Discover, Offer, Request y Ack; el cliente envía en difusión Discover y Request
B) Discover, Offer, Reply y Accept; el cliente envía en difusión solo el Discover
C) Detect, Offer, Request y Ack; el cliente envía todo en unidifusión una vez conoce al servidor

<details><summary>Respuesta</summary>

**Correcta: A) Discover, Offer, Request y Ack; el cliente envía en difusión Discover y Request** El Request se envía también en difusión para que los demás servidores que hubieran ofrecido dirección sepan que pueden liberarla.

*Referencia: §1.2.1 [RFC2131]*
</details>

---

### Pregunta 14

**¿Qué puertos utiliza DHCP en IPv4?**

A) TCP 67 en el cliente y TCP 68 en el servidor
B) UDP 546 en el servidor y UDP 547 en el cliente
C) UDP 67 en el servidor y UDP 68 en el cliente

<details><summary>Respuesta</summary>

**Correcta: C) UDP 67 en el servidor y UDP 68 en el cliente** Los puertos 546 y 547 corresponden a DHCPv6, y el protocolo funciona sobre UDP, no sobre TCP.

*Referencia: §1.2.1 [RFC2131] [RFC8415]*
</details>

---

### Pregunta 15

**Un cliente DHCP recibe una concesión de 8 días. ¿Cuándo intentará renovarla por primera vez y de qué modo?**

A) A los 8 días, en difusión, cuando la concesión ya ha expirado
B) A los 4 días, es decir, al 50 % del tiempo de concesión, mediante unidifusión al mismo servidor que se la concedió
C) A las 24 horas, en difusión, para comprobar que el servidor sigue activo

<details><summary>Respuesta</summary>

**Correcta: B) A los 4 días, es decir, al 50 % del tiempo de concesión, mediante unidifusión al mismo servidor que se la concedió** Es el temporizador T1. Si no lo consigue, vuelve a intentarlo al 87,5 % (temporizador T2), esta vez en difusión y aceptando a cualquier servidor.

*Referencia: §1.2.1 [RFC2131]*
</details>

---

### Pregunta 16

**¿Para qué sirve el agente de retransmisión DHCP?**

A) Para convertir la difusión del cliente en unidifusión hacia un servidor central, evitando tener un servidor DHCP en cada VLAN
B) Para repartir la carga entre dos servidores DHCP en alta disponibilidad
C) Para impedir que un servidor DHCP no autorizado entregue direcciones en la red

<details><summary>Respuesta</summary>

**Correcta: A) Para convertir la difusión del cliente en unidifusión hacia un servidor central, evitando tener un servidor DHCP en cada VLAN** Como las difusiones no atraviesan un encaminador, sin agente de retransmisión haría falta un servidor por VLAN. Quien impide los servidores no autorizados es la inspección DHCP, no el agente.

*Referencia: §1.2.1 [RFC2131]*
</details>

---

### Pregunta 17

**¿Qué información añade la opción 82 de DHCP y qué utilidad administrativa tiene?**

A) El nombre de dominio y los servidores DNS, para que el cliente no tenga que configurarlos
B) El identificador de circuito y el identificador remoto, es decir, el conmutador y el puerto de origen, lo que permite trazar desde qué roseta se pidió cada dirección
C) La duración máxima de la concesión negociada entre el cliente y el servidor

<details><summary>Respuesta</summary>

**Correcta: B) El identificador de circuito y el identificador remoto, es decir, el conmutador y el puerto de origen, lo que permite trazar desde qué roseta se pidió cada dirección** Es la base de la trazabilidad de las concesiones y responde de inmediato a la pregunta clásica en un incidente: qué equipo tenía esa IP y dónde estaba enchufado.

*Referencia: §1.2.1 [RFC3046]*
</details>

---

### Pregunta 18

**¿Qué mecanismo del conmutador impide que un servidor DHCP no autorizado reparta direcciones en la red y sirve además de base a la inspección ARP dinámica?**

A) La guarda de BPDU
B) El control de tormentas de difusión
C) La inspección DHCP, que declara no confiables todos los puertos salvo el que lleva al servidor legítimo

<details><summary>Respuesta</summary>

**Correcta: C) La inspección DHCP, que declara no confiables todos los puertos salvo el que lleva al servidor legítimo** Además de descartar los mensajes de servidor en los puertos no confiables, construye una tabla que asocia MAC, IP, VLAN y puerto, sobre la que se apoyan la inspección ARP dinámica y la guarda de origen IP.

*Referencia: §1.2.1 [RFC2131]*
</details>

---

### Pregunta 19

**Un equipo de una sede no consigue iniciar sesión en el dominio, pero navega por internet sin problemas. ¿Cuál es la primera hipótesis a comprobar?**

A) Que el equipo no está resolviendo los registros SRV que localizan a los controladores de dominio
B) Que el árbol de expansión ha bloqueado el puerto del equipo
C) Que la agregación de enlaces hacia el centro de proceso de datos está degradada

<details><summary>Respuesta</summary>

**Correcta: A) Que el equipo no está resolviendo los registros SRV que localizan a los controladores de dominio** El síntoma «no puedo iniciar sesión pero navego bien» es el clásico de un problema de DNS interno: servidor DNS caído, servidor incorrecto entregado por DHCP o filtrado del puerto 53 hacia el resolutor interno.

*Referencia: §1.2.2 [RFC1034] [MS-DNS]*
</details>

---

### Pregunta 20

**¿Qué aporta DNSSEC a las respuestas del sistema de nombres de dominio?**

A) Confidencialidad, porque cifra las consultas entre el cliente y el resolutor
B) Disponibilidad, porque replica automáticamente las zonas entre servidores
C) Autenticidad e integridad, mediante la firma criptográfica de las zonas, pero no confidencialidad

<details><summary>Respuesta</summary>

**Correcta: C) Autenticidad e integridad, mediante la firma criptográfica de las zonas, pero no confidencialidad** Las consultas siguen viajando en claro. La confidencialidad del canal la aportan DNS sobre TLS (puerto 853) y DNS sobre HTTPS.

*Referencia: §1.2.2 [RFC4033] [RFC7858]*
</details>

---

### Pregunta 21

**¿Qué protocolo y puerto se utilizan para consultar un directorio corporativo de forma cifrada?**

A) Kerberos sobre el puerto 88
B) LDAPS sobre el puerto 636, o LDAP con STARTTLS sobre el 389
C) RADIUS sobre los puertos 1812 y 1813

<details><summary>Respuesta</summary>

**Correcta: B) LDAPS sobre el puerto 636, o LDAP con STARTTLS sobre el 389** LDAP simple en el puerto 389 transmite las credenciales de la operación de vinculación sin cifrar, por lo que nunca debe usarse para validar contraseñas. Kerberos y RADIUS resuelven autenticación, no consulta del directorio.

*Referencia: §2.1, §2.2.1 [RFC4511]*
</details>

---

### Pregunta 22

**En un servicio de directorio, ¿cuál es el verdadero límite de seguridad?**

A) La unidad organizativa, porque en ella se delega la administración
B) El dominio, porque define la política de contraseñas y el ámbito de replicación
C) El bosque, porque comparte esquema, configuración y catálogo global

<details><summary>Respuesta</summary>

**Correcta: C) El bosque, porque comparte esquema, configuración y catálogo global** Dentro de un mismo bosque, quien controla un dominio puede alcanzar los demás por las relaciones de confianza. El dominio es límite de replicación y de política de cuentas, y la unidad organizativa no es en absoluto un límite de seguridad.

*Referencia: §2.1.2 [MS-AD]*
</details>

---

### Pregunta 23

**¿Qué determina un sitio en la estructura física de un directorio?**

A) A qué controlador de dominio se autentican los equipos de esas subredes y cómo se programa la replicación
B) Qué directivas de grupo se aplican a los usuarios de ese ámbito territorial
C) Qué unidades organizativas cuelgan de cada dominio

<details><summary>Respuesta</summary>

**Correcta: A) A qué controlador de dominio se autentican los equipos de esas subredes y cómo se programa la replicación** El sitio se define asociándole subredes IP y pertenece a la estructura física, que es independiente de la lógica: un dominio puede abarcar muchos sitios y un sitio puede alojar controladores de varios dominios.

*Referencia: §2.1.1 [MS-AD]*
</details>

---

### Pregunta 24

**Se da de baja a un empleado borrando su cuenta y, dos meses después, se vuelve a crear una cuenta con exactamente el mismo nombre. ¿Recupera sus permisos anteriores?**

A) Sí, porque los permisos se conceden al nombre de la cuenta
B) No, porque los permisos se conceden al identificador de seguridad, que es nuevo e irrepetible
C) Sí, siempre que se cree en la misma unidad organizativa

<details><summary>Respuesta</summary>

**Correcta: B) No, porque los permisos se conceden al identificador de seguridad, que es nuevo e irrepetible** Por la misma razón, renombrar una cuenta sí conserva todos sus accesos. Ante una baja temporal, la operación correcta es deshabilitar la cuenta, nunca borrarla.

*Referencia: §2.1.3 [MS-AD]*
</details>

---

### Pregunta 25

**¿Qué describe correctamente el anidamiento AGDLP?**

A) Las cuentas se incluyen en grupos globales, estos en grupos locales de dominio, y es a estos últimos a los que se conceden los permisos sobre el recurso
B) Los permisos se conceden a las cuentas y estas se agrupan después para facilitar la administración
C) Los grupos locales de dominio se incluyen en grupos globales, y los permisos se conceden a las cuentas individuales

<details><summary>Respuesta</summary>

**Correcta: A) Las cuentas se incluyen en grupos globales, estos en grupos locales de dominio, y es a estos últimos a los que se conceden los permisos sobre el recurso** El grupo global representa quién es alguien, y el grupo local de dominio, a qué da derecho algo. Su ventaja decisiva es que un traslado de servicio se resuelve con dos operaciones y no recorriendo todos los recursos.

*Referencia: §2.1.3 [MS-AD] [NIST-RBAC]*
</details>

---

### Pregunta 26

**¿Cuál es el orden correcto de aplicación de las directivas de grupo?**

A) Dominio, sitio, unidad organizativa y, por último, local
B) Unidad organizativa, dominio, sitio y, por último, local
C) Local, sitio, dominio y unidad organizativa, ganando la última en aplicarse

<details><summary>Respuesta</summary>

**Correcta: C) Local, sitio, dominio y unidad organizativa, ganando la última en aplicarse** Es la regla L-S-D-UO. Dentro de unidades organizativas anidadas se aplican de la más externa a la más interna, de modo que prevalece la más próxima al objeto.

*Referencia: §2.2.2 [MS-GPO]*
</details>

---

### Pregunta 27

**Una unidad organizativa tiene activado el bloqueo de herencia. ¿Qué ocurre con una directiva vinculada al dominio y marcada como forzada?**

A) No se aplica, porque el bloqueo de herencia prevalece sobre cualquier vínculo superior
B) Se aplica igualmente, porque la marca de forzada prevalece sobre el bloqueo de herencia
C) Se aplica solo su rama de configuración de equipo, y no la de usuario

<details><summary>Respuesta</summary>

**Correcta: B) Se aplica igualmente, porque la marca de forzada prevalece sobre el bloqueo de herencia** Una directiva forzada prevalece tanto sobre las que se aplican después como sobre el bloqueo de herencia. Es el mecanismo con el que una organización asegura que ciertos ajustes mínimos alcanzan a todo el parque.

*Referencia: §2.2.2 [MS-GPO]*
</details>

---

### Pregunta 28

**¿Qué diferencia hay entre un permiso y un derecho de usuario?**

A) El permiso se refiere a lo que se puede hacer sobre un objeto concreto; el derecho, a lo que se puede hacer sobre el sistema
B) El permiso lo concede el directorio y el derecho lo concede el propietario del fichero
C) El permiso caduca con la sesión y el derecho es permanente

<details><summary>Respuesta</summary>

**Correcta: A) El permiso se refiere a lo que se puede hacer sobre un objeto concreto; el derecho, a lo que se puede hacer sobre el sistema** Los permisos viven en la lista de control de acceso del recurso; los derechos, en la asignación de derechos de usuario de la directiva. Una cuenta puede tener permiso de lectura sobre una carpeta y no poder iniciar sesión en el servidor que la aloja.

*Referencia: §2.2.3 [MS-GPO]*
</details>

---

### Pregunta 29

**En las listas de control de acceso, ¿qué ocurre si una cuenta recibe una concesión de lectura por un grupo y una denegación explícita por otro?**

A) Prevalece la concesión, porque es la más antigua
B) Se aplica el permiso más restrictivo solo si ambos proceden del mismo grupo
C) Prevalece la denegación explícita

<details><summary>Respuesta</summary>

**Correcta: C) Prevalece la denegación explícita** La denegación explícita se impone sobre cualquier concesión. Por esa misma razón la denegación debe usarse con mucha prudencia: aplicada a un grupo amplio, produce bloqueos difíciles de diagnosticar.

*Referencia: §2.2.3 [MS-GPO]*
</details>

---

### Pregunta 30

**¿Por qué Kerberos exige que los relojes de los equipos estén sincronizados?**

A) Porque el protocolo transmite la contraseña cifrada con la hora del sistema
B) Porque los tiques llevan sello de tiempo y se rechazan fuera de una tolerancia habitual de cinco minutos
C) Porque el centro de distribución de claves emite un tique nuevo cada minuto

<details><summary>Respuesta</summary>

**Correcta: B) Porque los tiques llevan sello de tiempo y se rechazan fuera de una tolerancia habitual de cinco minutos** De ahí que NTP forme parte de la infraestructura crítica de identidad. Un servidor con la hora desajustada rechaza autenticaciones perfectamente válidas. La contraseña, por lo demás, no viaja por la red.

*Referencia: §2.2.1 [RFC4120] [RFC5905]*
</details>

---

### Pregunta 31

**¿Qué caracteriza al modelo de control de acceso basado en roles (RBAC)?**

A) Los permisos se asignan a roles y las personas se asignan a roles, de modo que nunca se conceden permisos a personas
B) El propietario de cada recurso decide discrecionalmente quién accede a él
C) El sistema asigna automáticamente los permisos según etiquetas de clasificación de la información

<details><summary>Respuesta</summary>

**Correcta: A) Los permisos se asignan a roles y las personas se asignan a roles, de modo que nunca se conceden permisos a personas** La opción B describe el modelo discrecional (DAC) y la C, el obligatorio (MAC). El modelo que decide evaluando atributos y contexto —hora, ubicación, estado del dispositivo— es el basado en atributos (ABAC).

*Referencia: §2.2.4 [NIST-RBAC]*
</details>

---

### Pregunta 32

**¿Cuál es la única contramedida realmente eficaz frente a la acumulación de privilegios de un empleado que ha pasado por varios destinos?**

A) Obligar a cambiar la contraseña con periodicidad trimestral
B) Deshabilitar la cuenta durante los traslados y volver a habilitarla al incorporarse
C) La revisión periódica de accesos, en la que los responsables funcionales confirman que cada persona sigue necesitando lo que tiene

<details><summary>Respuesta</summary>

**Correcta: C) La revisión periódica de accesos, en la que los responsables funcionales confirman que cada persona sigue necesitando lo que tiene** La acumulación de privilegios es el hallazgo más frecuente de las auditorías del ENS y se corrige con recertificación, no con diligencia en el alta. El ENS la respalda en la medida op.acc.4, proceso de gestión de derechos de acceso.

*Referencia: §2.2.4 [ENS] [NIST-RBAC]*
</details>

---

### Pregunta 33

**¿Qué protocolo normalizado permite descubrir automáticamente los vecinos de nivel de enlace y reconstruir la topología real de la red?**

A) CDP
B) LLDP, definido en IEEE 802.1AB
C) NETCONF, definido en el RFC 6241

<details><summary>Respuesta</summary>

**Correcta: B) LLDP, definido en IEEE 802.1AB** CDP es su equivalente propietario. LLDP es la base del inventario automático de topología y su extensión LLDP-MED permite que un teléfono IP descubra su VLAN de voz y su política de calidad de servicio.

*Referencia: §3.1.1 [IEEE8021AB] [PROPIETARIOS]*
</details>

---

### Pregunta 34

**¿Qué diferencia esencial hay entre la gestión dentro de banda y la gestión fuera de banda de un dispositivo de red?**

A) La gestión fuera de banda utiliza una vía independiente del plano de datos, por lo que sobrevive a la caída de la red que se administra
B) La gestión fuera de banda solo permite consultar el estado del equipo, nunca modificar su configuración
C) La gestión dentro de banda exige siempre presencia física ante el equipo

<details><summary>Respuesta</summary>

**Correcta: A) La gestión fuera de banda utiliza una vía independiente del plano de datos, por lo que sobrevive a la caída de la red que se administra** Puerto de consola, servidor de consolas, puerto de gestión dedicado o acceso por red móvil son vías fuera de banda. Quien exige presencia física es el puerto de consola en concreto, no la gestión dentro de banda.

*Referencia: §3.1.2 [ENS]*
</details>

---

### Pregunta 35

**¿Cuál es la única versión de SNMP que ofrece autenticación e integridad y, además, cifrado?**

A) SNMPv1, mediante la cadena de comunidad
B) SNMPv2c, que introdujo la operación GETBULK
C) SNMPv3, con sus modos authNoPriv y authPriv

<details><summary>Respuesta</summary>

**Correcta: C) SNMPv3, con sus modos authNoPriv y authPriv** Las versiones 1 y 2c se autentican con una cadena de comunidad que viaja en claro, equivalente a una contraseña visible en la red; las comunidades predeterminadas siguen siendo un hallazgo habitual de auditoría.

*Referencia: §3.1.3, §4.1.1 [RFC3411]*
</details>

---

### Pregunta 36

**¿Qué puertos utiliza SNMP y para qué sirve cada uno?**

A) UDP 162 para las consultas del gestor y UDP 161 para las notificaciones del agente
B) UDP 161 para las consultas del gestor y UDP 162 para las notificaciones del agente
C) TCP 161 para las consultas y TCP 830 para las notificaciones

<details><summary>Respuesta</summary>

**Correcta: B) UDP 161 para las consultas del gestor y UDP 162 para las notificaciones del agente** Conviene recordar además que las notificaciones son de dos tipos: trap, que no se confirma, e inform, que sí. El puerto 830 corresponde a NETCONF sobre SSH.

*Referencia: §4.1.1 [RFC3411] [RFC6241]*
</details>

---

### Pregunta 37

**¿Qué medida del ENS obliga a mantener un inventario de activos, y por qué es determinante para todo lo demás?**

A) La medida mp.eq.4, porque sin ella no se controlan las impresoras y las cámaras
B) La medida op.mon.2, porque el inventario forma parte del sistema de métricas
C) La medida op.exp.1, porque lo que no se sabe que existe no se puede proteger, actualizar ni monitorizar

<details><summary>Respuesta</summary>

**Correcta: C) La medida op.exp.1, porque lo que no se sabe que existe no se puede proteger, actualizar ni monitorizar** Es la primera medida del marco operacional por esa razón lógica. La medida mp.eq.4 se refiere a otros dispositivos conectados a la red, y op.mon.2, al sistema de métricas.

*Referencia: §3.2.1, §4.2.4 [ENS]*
</details>

---

### Pregunta 38

**En un proceso de gestión de parches, ¿cuál es el paso que con más frecuencia se omite y que convierte el proceso en algo medible?**

A) La verificación en el inventario del porcentaje de parque que ha quedado realmente actualizado
B) La lectura de los boletines de seguridad de los fabricantes
C) La prueba del parche en un grupo piloto antes de la difusión general

<details><summary>Respuesta</summary>

**Correcta: A) La verificación en el inventario del porcentaje de parque que ha quedado realmente actualizado** Un despliegue lanzado no es un despliegue aplicado: siempre hay equipos apagados, sin comunicación o con el agente averiado. Sin ese paso final el proceso no es medible y la organización cree estar parcheada sin estarlo.

*Referencia: §3.2.2 [ENS]*
</details>

---

### Pregunta 39

**Una aplicación certificada obliga a mantener un servidor con una versión antigua que ya no recibe parches. ¿Cuál es la actuación profesional correcta?**

A) Desconectarlo de la red de inmediato hasta que el fabricante certifique una versión actual
B) Documentar el riesgo, aislarlo en un segmento con acceso estrictamente filtrado, reforzar su vigilancia y planificar con fecha su sustitución
C) Ignorarlo, puesto que la aplicación certificada exime del cumplimiento del ENS

<details><summary>Respuesta</summary>

**Correcta: B) Documentar el riesgo, aislarlo en un segmento con acceso estrictamente filtrado, reforzar su vigilancia y planificar con fecha su sustitución** Un riesgo aceptado y documentado es una decisión de gestión; un riesgo desconocido es una avería esperando fecha. Apagarlo sin más traslada el problema al servicio que sostiene.

*Referencia: §3.2.2 [ENS]*
</details>

---

### Pregunta 40

**En 802.1X, ¿qué papel desempeña el conmutador al que se conecta el equipo?**

A) El de suplicante, porque presenta las credenciales del equipo al servidor
B) El de servidor de autenticación, porque decide si el equipo entra
C) El de autenticador, porque mantiene el puerto cerrado, retransmite el diálogo y aplica la decisión

<details><summary>Respuesta</summary>

**Correcta: C) El de autenticador, porque mantiene el puerto cerrado, retransmite el diálogo y aplica la decisión** El suplicante es el equipo que quiere entrar y el servidor de autenticación es el RADIUS, que verifica contra el directorio y devuelve la decisión y los atributos aplicables.

*Referencia: §3.2.3 [IEEE8021X]*
</details>

---

### Pregunta 41

**Antes de que un dispositivo complete la autenticación 802.1X, ¿qué tráfico permite el puerto del conmutador?**

A) Únicamente tramas EAPOL
B) Tráfico DHCP y DNS, para que el equipo pueda obtener dirección y resolver nombres
C) Todo el tráfico, pero confinado en la VLAN de invitados

<details><summary>Respuesta</summary>

**Correcta: A) Únicamente tramas EAPOL** El puerto no deja pasar nada más hasta que la autenticación tiene éxito: ni DHCP, ni DNS. La VLAN de invitados es uno de los destinos posibles una vez resuelta la autenticación, no el estado previo.

*Referencia: §3.2.3 [IEEE8021X] [RFC3748]*
</details>

---

### Pregunta 42

**¿Qué permite la extensión CoA de RADIUS, definida en el RFC 5176?**

A) Autenticar dispositivos que carecen de suplicante 802.1X mediante su dirección MAC
B) Modificar o terminar una sesión de red ya autorizada, moviendo por ejemplo un equipo a cuarentena sin esperar a que se desconecte
C) Cifrar el diálogo entre el autenticador y el servidor de autenticación

<details><summary>Respuesta</summary>

**Correcta: B) Modificar o terminar una sesión de red ya autorizada, moviendo por ejemplo un equipo a cuarentena sin esperar a que se desconecte** Es lo que convierte el control de admisión en un control continuo y no en una comprobación única en el momento de conectar. La autenticación por MAC es MAB.

*Referencia: §3.2.3 [RFC2865]*
</details>

---

### Pregunta 43

**¿Por qué la autenticación por dirección MAC (MAB) no puede considerarse una autenticación en sentido estricto?**

A) Porque solo funciona en redes inalámbricas
B) Porque exige un certificado digital que la mayoría de dispositivos no puede almacenar
C) Porque una dirección MAC se falsifica trivialmente, de modo que funciona como un inventario aplicado y no como una credencial

<details><summary>Respuesta</summary>

**Correcta: C) Porque una dirección MAC se falsifica trivialmente, de modo que funciona como un inventario aplicado y no como una credencial** Es un mecanismo de respaldo para dispositivos que no admiten suplicante —impresoras, cámaras, sensores— y debe reforzarse con perfilado y con VLAN muy restringidas.

*Referencia: §3.2.3 [IEEE8021X]*
</details>

---

### Pregunta 44

**¿Cuál es la fase imprescindible antes de aplicar un control de admisión a la red en una sede en producción?**

A) Desplegarlo en modo de supervisión, en el que la política se evalúa y se registra pero no se aplica
B) Sustituir previamente toda la electrónica de acceso por modelos con soporte de MACsec
C) Migrar todos los dispositivos a direccionamiento estático para evitar interferencias con DHCP

<details><summary>Respuesta</summary>

**Correcta: A) Desplegarlo en modo de supervisión, en el que la política se evalúa y se registra pero no se aplica** Permite descubrir cuántos dispositivos fallarían antes de dejar sin red a media plantilla. Junto a ello deben redundarse los servidores de autenticación y definirse el comportamiento de contingencia si ninguno responde.

*Referencia: §3.2.3 [IEEE8021X] [ENS]*
</details>

---

### Pregunta 45

**¿Qué significan las siglas FCAPS en la gestión de redes?**

A) Fallos, Cableado, Acceso, Puertos y Servicios
B) Fallos, Configuración, Contabilidad o uso, Prestaciones y Seguridad
C) Fiabilidad, Capacidad, Auditoría, Protección y Supervisión

<details><summary>Respuesta</summary>

**Correcta: B) Fallos, Configuración, Contabilidad o uso, Prestaciones y Seguridad** Es el modelo funcional de referencia de la gestión de redes formulado por ISO. Describe funciones permanentes, no fases de un proyecto.

*Referencia: §1.1 [SWITCH-VENDORS]*
</details>

---

### Pregunta 46

**Los contadores `ifInOctets` e `ifOutOctets` de la MIB-II son acumulativos. ¿Cómo se obtiene a partir de ellos la velocidad de un enlace?**

A) Leyendo directamente su valor, que ya expresa bits por segundo
B) Dividiendo el valor entre el tiempo transcurrido desde el arranque del dispositivo
C) Calculando la diferencia entre dos lecturas y dividiéndola por el intervalo transcurrido entre ambas

<details><summary>Respuesta</summary>

**Correcta: C) Calculando la diferencia entre dos lecturas y dividiéndola por el intervalo transcurrido entre ambas** Además, los contadores de 32 bits desbordan en pocos minutos a velocidades de gigabit, por lo que en enlaces rápidos deben usarse los contadores de 64 bits.

*Referencia: §4.1.1 [RFC1213]*
</details>

---

### Pregunta 47

**¿Qué diferencia funcional hay entre SNMP y syslog en un sistema de monitorización?**

A) SNMP entrega valores numéricos consultados periódicamente y syslog entrega eventos con marca de tiempo
B) SNMP solo funciona en dispositivos de red y syslog solo en servidores
C) SNMP registra los eventos de seguridad y syslog mide el rendimiento de las interfaces

<details><summary>Respuesta</summary>

**Correcta: A) SNMP entrega valores numéricos consultados periódicamente y syslog entrega eventos con marca de tiempo** Dicho brevemente: SNMP mide y syslog narra. Un sistema de monitorización serio necesita ambos, y los dos exigen NTP para que sus tiempos sean comparables.

*Referencia: §4.1.1 [RFC3411] [RFC5424]*
</details>

---

### Pregunta 48

**Una disponibilidad comprometida del 99,9 % anual equivale aproximadamente a:**

A) 53 minutos de parada al año
B) 8,8 horas de parada al año
C) 3,65 días de parada al año

<details><summary>Respuesta</summary>

**Correcta: B) 8,8 horas de parada al año** Los 53 minutos corresponden al 99,99 % y los 3,65 días, al 99 %. Cada nueve adicional divide la indisponibilidad entre diez y multiplica el coste mucho más que por diez.

*Referencia: §4.1.2 [SWITCH-VENDORS]*
</details>

---

### Pregunta 49

**Un enlace troncal de 1 Gbit/s presenta una utilización media del 12 % y un 0,7 % de errores de entrada. ¿Cuál es la hipótesis principal?**

A) Saturación del enlace, que debe ampliarse a 10 Gbit/s
B) Un bucle de nivel 2 que el árbol de expansión no ha conseguido resolver
C) Un problema de capa física o de negociación: latiguillo, conector, óptica degradada o desajuste de dúplex

<details><summary>Respuesta</summary>

**Correcta: C) Un problema de capa física o de negociación: latiguillo, conector, óptica degradada o desajuste de dúplex** Utilización baja más errores altos apunta casi siempre a la capa física. Ampliar la capacidad no habría corregido nada. Conviene mirar los contadores del otro extremo, porque un desajuste de dúplex produce errores asimétricos característicos.

*Referencia: §4.1.2 [RFC1213]*
</details>

---

### Pregunta 50

**¿Por qué se recomienda medir la utilización de un enlace por su percentil 95 y no por su media?**

A) Porque la media oculta los picos, y el percentil 95 refleja el valor que solo se supera el 5 % del tiempo
B) Porque el percentil 95 elimina los errores de lectura de los contadores SNMP
C) Porque la media solo puede calcularse con contadores de 64 bits

<details><summary>Respuesta</summary>

**Correcta: A) Porque la media oculta los picos, y el percentil 95 refleja el valor que solo se supera el 5 % del tiempo** Es además el criterio habitual de facturación de los operadores. Como regla de diseño de campus, un enlace que sostiene el 70 % en su percentil 95 debe estar ya planificado para ampliación.

*Referencia: §4.1.2 [SWITCH-VENDORS]*
</details>

---

### Pregunta 51

**¿Qué mide la fluctuación (*jitter*) y por qué afecta especialmente a la voz sobre IP?**

A) El porcentaje de paquetes descartados por congestión, que provoca cortes en la conversación
B) La variación del retardo entre paquetes consecutivos, que obliga a usar memorias intermedias y produce voz entrecortada
C) El tiempo total de tránsito extremo a extremo, que debe mantenerse por debajo de 150 milisegundos

<details><summary>Respuesta</summary>

**Correcta: B) La variación del retardo entre paquetes consecutivos, que obliga a usar memorias intermedias y produce voz entrecortada** Una red con retardo alto pero constante permite una conversación incómoda pero inteligible; una con retardo bajo y muy variable resulta peor. El valor de referencia habitual para voz es una fluctuación menor o igual a 30 milisegundos.

*Referencia: §4.1.3 [RFC4594]*
</details>

---

### Pregunta 52

**¿Cuál de estas afirmaciones sobre la calidad de servicio es correcta?**

A) No crea capacidad: únicamente decide qué tráfico sufre cuando la capacidad no alcanza
B) Aumenta el caudal disponible del enlace priorizando las aplicaciones críticas
C) Solo tiene efecto cuando el enlace está por debajo del 50 % de utilización

<details><summary>Respuesta</summary>

**Correcta: A) No crea capacidad: únicamente decide qué tráfico sufre cuando la capacidad no alcanza** Si un enlace está saturado de forma sostenida, la solución es ampliarlo. La calidad de servicio gestiona la congestión transitoria, que es la que ocurre en toda red real varias veces al día.

*Referencia: §4.1.3 [RFC2475]*
</details>

---

### Pregunta 53

**¿En qué se diferencian el marcado PCP y el marcado DSCP?**

A) PCP tiene 6 bits y viaja en la cabecera IP; DSCP tiene 3 bits y viaja en la etiqueta 802.1Q
B) Ambos tienen 6 bits, pero PCP se aplica al tráfico de entrada y DSCP al de salida
C) PCP tiene 3 bits, vive en la etiqueta 802.1Q y se pierde al encaminar; DSCP tiene 6 bits, vive en la cabecera IP y sobrevive extremo a extremo

<details><summary>Respuesta</summary>

**Correcta: C) PCP tiene 3 bits, vive en la etiqueta 802.1Q y se pierde al encaminar; DSCP tiene 6 bits, vive en la cabecera IP y sobrevive extremo a extremo** De ahí que el marcado que importa de extremo a extremo sea el DSCP, y que el PCP solo exista mientras la trama circula etiquetada por un troncal.

*Referencia: §4.1.4 [IEEE8021Q] [RFC2474]*
</details>

---

### Pregunta 54

**¿Qué valor de DSCP corresponde al comportamiento por salto reservado a la voz?**

A) AF41, con valor decimal 34
B) EF, con valor decimal 46
C) CS3, con valor decimal 24

<details><summary>Respuesta</summary>

**Correcta: B) EF, con valor decimal 46** El reenvío acelerado (EF) se reserva a la voz y se sirve en cola de prioridad, siempre con un límite máximo para que un flujo averiado o malicioso no ahogue al resto. AF41 se destina al vídeo interactivo y CS3, a la señalización de llamadas.

*Referencia: §4.1.4 [RFC2597] [RFC4594]*
</details>

---

### Pregunta 55

**¿Cuál es la diferencia entre vigilar (*policing*) y modelar (*shaping*) el tráfico?**

A) La vigilancia descarta o remarca el exceso sin introducir retardo; el modelado lo almacena y lo entrega más tarde, evitando descartes pero añadiendo retardo
B) La vigilancia se aplica a la voz y el modelado a los datos de mejor esfuerzo
C) La vigilancia actúa sobre el marcado DSCP y el modelado sobre el marcado PCP

<details><summary>Respuesta</summary>

**Correcta: A) La vigilancia descarta o remarca el exceso sin introducir retardo; el modelado lo almacena y lo entrega más tarde, evitando descartes pero añadiendo retardo** La regla práctica asociada es que se vigila en la entrada y se modela en la salida.

*Referencia: §4.1.4 [RFC2475]*
</details>

---

### Pregunta 56

**¿Por qué el marcado de calidad de servicio que llega desde el equipo de un usuario no debe considerarse fiable?**

A) Porque el campo DSCP se corrompe al atravesar un conmutador de nivel 2
B) Porque los sistemas operativos de escritorio no admiten marcar paquetes
C) Porque cualquier aplicación puede marcar sus paquetes como voz, y por eso se clasifica y remarca en el borde de la red

<details><summary>Respuesta</summary>

**Correcta: C) Porque cualquier aplicación puede marcar sus paquetes como voz, y por eso se clasifica y remarca en el borde de la red** Es el concepto de frontera de confianza: los conmutadores de acceso clasifican y remarcan —confiando todo lo más en el teléfono IP identificado por LLDP-MED— y el núcleo se limita a encolar según lo marcado.

*Referencia: §4.1.4 [RFC2475] [IEEE8021AB]*
</details>

---

### Pregunta 57

**¿Cuál es la ventaja de un TAP frente a un espejo de puertos (SPAN) para capturar tráfico?**

A) Que puede activarse por configuración sin desplazarse al armario de comunicaciones
B) Que es una derivación física pasiva, fiel al cien por cien y sin consumir recursos del conmutador ni descartar en saturación
C) Que permite capturar el tráfico ya descifrado de las sesiones TLS

<details><summary>Respuesta</summary>

**Correcta: B) Que es una derivación física pasiva, fiel al cien por cien y sin consumir recursos del conmutador ni descartar en saturación** El SPAN, en cambio, se activa por configuración pero puede descartar si el tráfico de origen supera la capacidad del puerto de destino, y puede no copiar las tramas con error. Ninguno de los dos descifra TLS.

*Referencia: §4.2.1 [WIRESHARK]*
</details>

---

### Pregunta 58

**¿Cuál es la relación entre NetFlow v9 e IPFIX?**

A) IPFIX es la normalización abierta que el IETF hizo de NetFlow v9, publicada en el RFC 7011
B) NetFlow v9 es la evolución que Cisco hizo de IPFIX tras su publicación por el IETF
C) Son protocolos independientes: NetFlow exporta flujos e IPFIX exporta muestras de paquetes

<details><summary>Respuesta</summary>

**Correcta: A) IPFIX es la normalización abierta que el IETF hizo de NetFlow v9, publicada en el RFC 7011** Por eso se le llama coloquialmente NetFlow v10. Quien trabaja por muestreo estadístico de paquetes es sFlow (RFC 3176), no IPFIX.

*Referencia: §4.2.2 [RFC3954] [RFC7011] [SFLOW]*
</details>

---

### Pregunta 59

**Un enlace hacia el centro de proceso de datos se satura cada mañana. Se sabe cuánto tráfico circula, pero no quién lo genera. ¿Qué instrumento es el adecuado?**

A) Una captura completa de paquetes durante toda la franja, para conocer el contenido de las comunicaciones
B) El aumento de la frecuencia de sondeo SNMP sobre los contadores de la interfaz
C) Los registros de flujo, que dicen quién habla con quién, cuánto y cuándo, sin contenido y con volumen asumible

<details><summary>Respuesta</summary>

**Correcta: C) Los registros de flujo, que dicen quién habla con quién, cuánto y cuándo, sin contenido y con volumen asumible** SNMP ya responde al cuánto y sondearlo más a menudo no añade el quién. Una captura completa generaría un volumen inmanejable y recogería comunicaciones personales sin necesidad, lo que sería desproporcionado.

*Referencia: §4.2.2 [RFC7011]*
</details>

---

### Pregunta 60

**En syslog, ¿qué relación hay entre el valor numérico de la severidad y la gravedad del suceso?**

A) A mayor número, mayor gravedad: el 7 corresponde a emergencia y el 0 a depuración
B) A menor número, mayor gravedad: el 0 corresponde a emergencia y el 7 a depuración
C) La severidad no es numérica, sino una etiqueta de texto sin orden definido

<details><summary>Respuesta</summary>

**Correcta: B) A menor número, mayor gravedad: el 0 corresponde a emergencia y el 7 a depuración** Es lo contrario de lo que sugiere la intuición y por eso se pregunta con frecuencia. Un dispositivo configurado en severidad 7 hacia un servidor central puede inundarlo, de modo que el nivel debe elegirse conscientemente.

*Referencia: §4.2.3 [RFC5424]*
</details>
