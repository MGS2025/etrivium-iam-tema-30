# Tema 30 — Índice

> **Título oficial**: Administración de redes de área local. Gestión de usuarios. Gestión de dispositivos. Monitorización y control de tráfico.
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Administración de redes de área local**
   1.1. Fundamentos y arquitectura de administración de redes LAN
   1.1.1. Modelos de diseño jerárquico y segmentación de red
   1.1.2. Redes de área local virtuales (VLAN) y enlace de troncales
   1.1.3. Protocolos de conmutación y redundancia en el nivel de enlace
   1.2. Servicios de red fundamentales para la administración LAN
   1.2.1. Configuración y gestión dinámica de direccionamiento (DHCP)
   1.2.2. Servicio de resolución de nombres de dominio (DNS)

2. **Gestión de usuarios y servicios de directorio**
   2.1. Arquitectura de directorio activo e identidad digital
   2.1.1. Estructura lógica y física de servicios de directorio
   2.1.2. Dominios, árboles, bosques y unidades organizativas
   2.1.3. Objetos de directorio, cuentas de usuario, grupos y esquemas
   2.2. Autenticación, autorización y políticas de gestión
   2.2.1. Mecanismos y protocolos de autenticación en red
   2.2.2. Directivas de grupo y gestión centralizada de políticas
   2.2.3. Aplicación de directivas de seguridad y asignación de derechos
   2.2.4. Control de accesos basado en roles y principio de mínimo privilegio

3. **Gestión y administración de dispositivos de red y puestos de trabajo**
   3.1. Administración de equipos e infraestructura de red
   3.1.1. Gestión centralizada de elementos de red y electrónica de conmutación
   3.1.2. Interfaces de gestión en banda y fuera de banda
   3.1.3. Protocolos de administración segura
   3.2. Gestión del ciclo de vida del puesto de trabajo y dispositivos finales
   3.2.1. Despliegue, aprovisionamiento e inventariado de dispositivos
   3.2.2. Gestión de parches, actualizaciones y mantenimiento de firmware
   3.2.3. Control de admisión a la red y autenticación de dispositivos

4. **Monitorización, análisis y control del tráfico de red**
   4.1. Monitorización y gestión del rendimiento de red
   4.1.1. Protocolos e instrumentos de monitorización de red
   4.1.2. Métricas de rendimiento, disponibilidad y calidad de servicio
   4.1.3. Parámetros de calidad de servicio en redes de área local
   4.1.4. Mecanismos de clasificación, marcado y priorización de tráfico
   4.2. Análisis de tráfico, auditoría y control de seguridad
   4.2.1. Captura, inspección y análisis de paquetes de red
   4.2.2. Monitorización basada en flujos de tráfico de red
   4.2.3. Auditoría, registro de eventos y gestión de logs
   4.2.4. Cumplimiento del Esquema Nacional de Seguridad en la administración LAN

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| Dominio de colisión / difusión | Cada **puerto de conmutador** es un dominio de **colisión**; cada **VLAN** (o cada interfaz de encaminador) delimita un dominio de **difusión**. Segmentar en VLAN reduce el dominio de difusión, no el de colisión |
| Etiqueta 802.1Q | Se inserta en la trama Ethernet: **TPID 0x8100** + **PCP (3 bits)** + **DEI (1 bit)** + **VID (12 bits)**. VID útiles **1-4094**; **0** y **4095** están reservados. La trama etiquetada mide **4 bytes más** [IEEE8021Q] |
| Acceso frente a troncal | Puerto de **acceso**: una sola VLAN, tramas **sin etiqueta** hacia el equipo final. Puerto **troncal**: varias VLAN **etiquetadas** más, opcionalmente, una **VLAN nativa sin etiquetar** |
| Enrutamiento entre VLAN | Dos VLAN **nunca** se comunican en el nivel 2: hace falta un **encaminador** o un **conmutador de nivel 3** con interfaz virtual (SVI). Es el punto natural donde aplicar listas de control de acceso |
| STP / RSTP / MSTP | **STP** (802.1D) evita bucles bloqueando puertos; converge en decenas de segundos. **RSTP** (802.1w, integrado en 802.1D-2004) converge en **segundos**. **MSTP** (802.1s, integrado en **802.1Q**) agrupa VLAN en **instancias** para repartir la carga |
| Agregación de enlaces | **802.1AX** (antes **802.3ad**) con **LACP**: varios enlaces físicos actúan como **uno lógico**; suma capacidad y aporta redundancia **sin** que STP bloquee. El reparto se hace **por flujo**, no paquete a paquete |
| DHCP | Ciclo **DORA**: *Discover* (difusión del cliente) → *Offer* → *Request* → *Ack*. Puertos UDP **67** (servidor) y **68** (cliente). Renovación al **50 %** (T1) y **87,5 %** (T2) del tiempo de concesión [RFC2131] |
| Agente de retransmisión DHCP | El *relay* (`ip helper-address`) convierte la difusión del cliente en **unidifusión** hacia el servidor: permite un servidor DHCP central para muchas VLAN. La **opción 82** añade puerto y conmutador de origen [RFC3046] |
| DNS | Espacio jerárquico de nombres dividido en **zonas**. Registros: **A/AAAA** (nombre→IP), **PTR** (IP→nombre, zona `in-addr.arpa`), **CNAME** (alias), **MX**, **NS**, **SOA**, **SRV** (localización de servicios: base del inicio de sesión en el dominio) [RFC1034] [MS-DNS] |
| DNSSEC | Firma las zonas: aporta **autenticidad e integridad**, **no confidencialidad**. La confidencialidad la dan **DoT** (puerto 853) y **DoH** [RFC4033] [RFC7858] |
| LDAP / X.500 | Directorio jerárquico (**DIT**) optimizado para **lectura**. Entradas identificadas por **DN**; puertos **389** y **636** (sobre TLS). LDAP es la simplificación de **X.500** sobre TCP/IP [RFC4511] [X500] |
| Bosque / árbol / dominio / UO | **Bosque** = límite de **seguridad** y de **esquema**; **dominio** = límite de **replicación** y de **directiva**; **unidad organizativa** = contenedor de **administración delegada** y de **aplicación de GPO**. La UO **no** es un límite de seguridad [MS-AD] |
| Sitio (*site*) | Elemento de la estructura **física**: agrupa subredes bien conectadas. Determina a **qué controlador se autentica** el usuario y cómo se **replica**. Es independiente de la estructura lógica |
| Kerberos | Autenticación por **tiques** (TGT del KDC y tique de servicio), con **sello de tiempo**: exige relojes sincronizados (tolerancia habitual **5 minutos**). Puerto **88**. La contraseña **no viaja** por la red [RFC4120] |
| Orden de aplicación de GPO | **L-S-D-UO**: Local → Sitio → Dominio → Unidad organizativa. **Gana la última** que se aplica, salvo que una superior esté **forzada** (*enforced*), que prevalece sobre el bloqueo de herencia [MS-GPO] |
| RBAC y mínimo privilegio | Los permisos se asignan a **roles**, no a personas. Cada cuenta recibe **solo** lo imprescindible y **solo** el tiempo necesario; se completa con **segregación de funciones** y **cuenta administrativa separada** de la de trabajo [NIST-RBAC] [ENS `op.acc.3`] |
| 802.1X | **Suplicante** (equipo) — **autenticador** (conmutador o punto de acceso) — **servidor de autenticación** (RADIUS). El puerto solo deja pasar **EAPOL** hasta que la autenticación tiene éxito. Alternativas de respaldo: **MAB** por MAC y **VLAN de invitados** [IEEE8021X] [RFC2865] |
| SNMP | **Gestor** consulta al **agente** (UDP **161**); el agente envía **notificaciones** no solicitadas (*trap*/*inform*, UDP **162**). Datos organizados en la **MIB** por **OID**. Solo **SNMPv3** autentica y cifra: v1 y v2c usan **comunidad en claro** [RFC3411] |
| Dentro / fuera de banda | **Dentro de banda**: se gestiona por la misma red que transporta los datos; si la red cae, se pierde la gestión. **Fuera de banda**: vía independiente (puerto de consola, red de gestión dedicada, acceso celular) que sobrevive a la caída |
| Espejo de puertos (SPAN) | Copia el tráfico de un puerto o VLAN hacia un puerto de análisis. **RSPAN/ERSPAN** lo llevan a otro conmutador o lo encapsulan sobre IP. Alternativa pasiva: **TAP** físico, que no consume capacidad del conmutador |
| Flujo | Conjunto de paquetes con **misma clave**: IP y puerto de origen, IP y puerto de destino, y protocolo (**quíntupla**). **NetFlow v9** (RFC 3954) es de Cisco; **IPFIX** (RFC 7011) es su versión **normalizada** por el IETF; **sFlow** funciona por **muestreo** |
| Paquete frente a flujo | La **captura de paquetes** da el **contenido** completo pero es cara de almacenar y muy sensible en protección de datos; el **flujo** da **quién habló con quién, cuánto y cuándo**, sin contenido, y escala a toda la red |
| DSCP | **6 bits** del campo DS de la cabecera IP (**nivel 3**). **EF = DSCP 46** para voz; **AF41** para vídeo interactivo; **CS0/BE = 0** para mejor esfuerzo. En el **nivel 2** el equivalente es **PCP**, 3 bits de la etiqueta 802.1Q [RFC2474] [RFC4594] |
| Confianza del marcado | El marcado que llega del equipo de usuario **no es de fiar**: se **clasifica y remarca en el borde** de la red (nodo frontera DiffServ). El núcleo se limita a **encolar** según lo marcado [RFC2475] |
| Umbrales de voz | Valores de referencia habituales para voz sobre IP: **retardo unidireccional ≤ 150 ms**, **fluctuación (*jitter*) ≤ 30 ms** y **pérdida < 1 %**. Son objetivos de diseño, no cifras normativas |
| Syslog | Mensajes con **facility** y **severity 0-7** (0 *emergency* … 7 *debug*). UDP **514** en el uso clásico; **TCP 6514 sobre TLS** cuando se exige integridad y confidencialidad. Exige **NTP** para ser correlacionable [RFC5424] [RFC5905] |
| ENS y red | Medidas nucleares: **`mp.com.1`** perímetro seguro · **`mp.com.2`** confidencialidad · **`mp.com.3`** integridad y autenticidad · **`mp.com.4`** **separación de flujos de información en la red** · **`op.mon.1`** detección de intrusión · **`op.mon.2`** sistema de métricas · **`op.mon.3`** vigilancia · **`op.exp.8`** registro de la actividad [ENS] |
| Registros y RGPD | Una dirección IP asociada a un usuario es **dato personal**: el registro de tráfico exige **finalidad determinada**, **minimización**, **plazo de conservación** e **información previa** a la plantilla. Los arts. **87-90 LOPDGDD** limitan el control del uso de dispositivos [RGPD] [LOPDGDD] |

---

*Tiempo estimado de estudio: 13-15 horas*
*Extensión del contenido: ~21.400 palabras · 15 diagramas SVG embebidos*
