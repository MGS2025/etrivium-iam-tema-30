# Tema 30 — Fuentes

> **Título oficial**: Administración de redes de área local. Gestión de usuarios. Gestión de dispositivos. Monitorización y control de tráfico.
>
> **Criterio**: todo dato del contenido cita un **ID** inline (p. ej. `[IEEE8021Q]`). Tier 1 = estándares de organismos de normalización (IEEE 802, IETF, ITU-T, NIST) y normativa española directamente aplicable (ENS, RGPD/LOPDGDD, guías CCN-STIC). Tier 2 = documentación de productos, implementaciones y herramientas concretas, citada para ilustrar sin atar el tema a un único fabricante. Tier 3 = marco administrativo y organizativo de contexto.

---

## Tier 1 — Estándares y normativa

| ID | Referencia |
|---|---|
| `[IEEE8021Q]` | IEEE Std **802.1Q-2022**. *Bridges and Bridged Networks*. Norma consolidada de puentes y redes puenteadas: etiquetado **VLAN** (campo VID de **12 bits**, valores útiles **1-4094**; 0 y 4095 reservados), enlaces troncales, prioridad **PCP** y, desde la edición de 2005, el **protocolo de árbol de expansión múltiple (MSTP)**, publicado antes como 802.1s. |
| `[IEEE8021D]` | IEEE Std **802.1D-2004**. *Media Access Control (MAC) Bridges*. Puenteado transparente, aprendizaje de direcciones MAC y **protocolo de árbol de expansión**. La edición de 2004 **incorporó el RSTP** publicado como 802.1w-2001. |
| `[IEEE8021AX]` | IEEE Std **802.1AX-2020**. *Link Aggregation*. **Agregación de enlaces** y protocolo de control **LACP**. Publicada originalmente como **802.3ad** y trasladada al grupo 802.1 en 2008. |
| `[IEEE8021X]` | IEEE Std **802.1X-2020**. *Port-Based Network Access Control*. Control de admisión a la red basado en puerto: triángulo **suplicante — autenticador — servidor de autenticación** y encapsulado **EAPOL** (EAP sobre LAN). |
| `[IEEE8021AB]` | IEEE Std **802.1AB**. *Station and Media Access Control Connectivity Discovery* (**LLDP**). Descubrimiento de vecinos en el nivel de enlace; base del inventario automático de la topología, con la extensión **LLDP-MED** para telefonía IP. |
| `[IEEE8021AE]` | IEEE Std **802.1AE**. *MAC Security* (**MACsec**). Confidencialidad, integridad y autenticidad del origen **salto a salto** en el nivel 2. |
| `[IEEE8021AR]` | IEEE Std **802.1AR**. *Secure Device Identity* (**DevID**). Identificador de dispositivo ligado criptográficamente al equipo: **IDevID** de fábrica y **LDevID** local. |
| `[IEEE8023]` | IEEE Std **802.3**. *Ethernet*. Formato de trama, direccionamiento MAC, dominios de colisión y de difusión, y **PoE** (802.3af/at/bt) para alimentar teléfonos, puntos de acceso y cámaras por el propio cable de datos. |
| `[RFC2131]` | IETF. *RFC 2131: Dynamic Host Configuration Protocol* y *RFC 2132 (opciones)*. Ciclo **DORA**, concesiones (*leases*), puertos UDP **67** (servidor) y **68** (cliente). |
| `[RFC3046]` | IETF. *RFC 3046: DHCP Relay Agent Information Option* (**opción 82**). Inserción por el agente de retransmisión del puerto y el conmutador de origen; base de la trazabilidad de la concesión. |
| `[RFC8415]` | IETF. *RFC 8415: Dynamic Host Configuration Protocol for IPv6 (DHCPv6)*. Puertos UDP **546/547**, modos con estado y sin estado. |
| `[RFC1034]` | IETF. *RFC 1034 y RFC 1035: Domain Names — Concepts and Facilities / Implementation and Specification*. Espacio de nombres jerárquico, **zonas**, delegación, tipos de registro y transporte UDP/TCP **53**. |
| `[RFC2136]` | IETF. *RFC 2136: Dynamic Updates in the Domain Name System (DNS UPDATE)*. Actualización dinámica del DNS, típicamente desde el servidor DHCP o desde el propio cliente. |
| `[RFC4033]` | IETF. *RFC 4033-4035: DNS Security Introduction and Requirements* (**DNSSEC**). Firma de zonas y cadena de confianza: aporta autenticidad e integridad, **no confidencialidad**. |
| `[RFC7858]` | IETF. *RFC 7858 (DNS over TLS, puerto 853)* y *RFC 8484 (DNS over HTTPS)*. Confidencialidad del canal de consulta; relevantes en este tema por el problema de gestión que plantean dentro de una red corporativa. |
| `[RFC1918]` | IETF. *RFC 1918: Address Allocation for Private Internets*. Rangos privados 10/8, 172.16/12 y 192.168/16, base del direccionamiento de una LAN corporativa. |
| `[RFC4632]` | IETF. *RFC 4632: Classless Inter-Domain Routing (CIDR)* y *RFC 950 (subredes)*. Máscaras de longitud variable y agregación de rutas. |
| `[RFC3411]` | IETF. *RFC 3411-3418: An Architecture for Describing SNMP Management Frameworks* (**SNMPv3**). Gestor, agente, **MIB** y OID; puertos UDP **161** (consultas) y **162** (notificaciones); modelo de seguridad basado en usuario (**USM**), con autenticación y cifrado. |
| `[RFC1213]` | IETF. *RFC 1213: Management Information Base for Network Management of TCP/IP-based internets: MIB-II*. Grupos `system`, `interfaces`, `ip`; los contadores de interfaz sostienen la mayor parte de la monitorización clásica. |
| `[RFC6241]` | IETF. *RFC 6241: Network Configuration Protocol (NETCONF)* y *RFC 6020 (YANG)*. Configuración remota programática sobre SSH (**puerto 830**), con almacenes de configuración y transacciones. Complemento moderno: **RESTCONF** (RFC 8040). |
| `[RFC5424]` | IETF. *RFC 5424: The Syslog Protocol*, con *RFC 5425* (sobre TLS) y *RFC 5426* (sobre UDP). Formato del registro, **facility** y **severity** (0-7), puerto UDP **514** en el uso clásico y TCP **6514** sobre TLS. |
| `[RFC5905]` | IETF. *RFC 5905: Network Time Protocol Version 4* (**NTP**). Sincronización horaria, estratos y puerto UDP **123**: sin ella ningún registro de eventos es correlacionable. |
| `[RFC3954]` | IETF. *RFC 3954: Cisco Systems NetFlow Services Export Version 9*. Exportación de **flujos** con plantillas; puerto de recolección convencional UDP 2055. |
| `[RFC7011]` | IETF. *RFC 7011-7015: Specification of the IP Flow Information Export (IPFIX) Protocol*. Norma **abierta** de exportación de flujos, evolución de NetFlow v9 y modelo de referencia del análisis de tráfico por flujos. |
| `[SFLOW]` | sFlow.org / IETF. *RFC 3176: InMon Corporation's sFlow*. Monitorización por **muestreo** de paquetes y contadores, embebida en el circuito integrado del conmutador; puerto de recolección convencional UDP 6343. |
| `[RFC2474]` | IETF. *RFC 2474: Definition of the Differentiated Services Field (DS Field)*. Campo **DSCP** de 6 bits en la cabecera IP, base de la calidad de servicio por clases. |
| `[RFC2475]` | IETF. *RFC 2475: An Architecture for Differentiated Services*. Arquitectura **DiffServ**: dominio, nodos frontera y nodos interiores, y acondicionamiento del tráfico en el borde. |
| `[RFC2597]` | IETF. *RFC 2597: Assured Forwarding PHB Group* y *RFC 3246: An Expedited Forwarding PHB*. Comportamientos por salto AF11-AF43 y **EF** (DSCP **46**), este último reservado a la voz. |
| `[RFC4594]` | IETF. *RFC 4594: Configuration Guidelines for DiffServ Service Classes*. Recomendaciones de marcado por tipo de tráfico: voz, vídeo interactivo, señalización, transaccional y mejor esfuerzo. |
| `[RFC2328]` | IETF. *RFC 2328 (OSPFv2)*, *RFC 5340 (OSPFv3)* y *RFC 5798 (VRRP v3)*. Encaminamiento dinámico entre sedes y redundancia de la puerta de enlace predeterminada. |
| `[RFC4120]` | IETF. *RFC 4120: The Kerberos Network Authentication Service (V5)*. Autenticación por **tiques** (TGT y tique de servicio), con sello de tiempo; puerto 88. Base de la autenticación en dominios de directorio. |
| `[RFC4511]` | IETF. *RFC 4510-4519: Lightweight Directory Access Protocol (LDAP)*. Protocolo, modelo de información, nombres distinguidos (**DN**), filtros de búsqueda y esquema. Puertos **389** y **636** (sobre TLS). |
| `[X500]` | ITU-T. *Recomendación X.500* — modelo de servicio de directorio (DIT, DSA, DUA), del que LDAP es la simplificación sobre TCP/IP. |
| `[RFC2865]` | IETF. *RFC 2865 (RADIUS Authentication)*, *RFC 2866 (Accounting)* y *RFC 5176 (Dynamic Authorization Extensions, **CoA**)*. Modelo **AAA** y capacidad de cambiar o cortar una sesión ya autorizada. |
| `[RFC3748]` | IETF. *RFC 3748: Extensible Authentication Protocol (EAP)* y *RFC 5216 (EAP-TLS)*. Métodos de autenticación transportados por 802.1X: EAP-TLS, PEAP y EAP-TTLS. |
| `[RFC6749]` | IETF. *RFC 6749 (OAuth 2.0)*, *RFC 7519 (JSON Web Token)* y **SAML 2.0** de OASIS. Federación de identidad e inicio de sesión único, cada vez más presentes junto al directorio clásico. |
| `[NIST-RBAC]` | NIST / ANSI INCITS 359. *Role-Based Access Control*. Modelo **RBAC** con usuarios, roles, permisos y sesiones; jerarquía de roles y restricciones de segregación de funciones. |
| `[NIST-ZT]` | NIST SP **800-207**: *Zero Trust Architecture*. Verificación explícita, mínimo privilegio y presunción de compromiso; marco de referencia de la microsegmentación. |
| `[ENS]` | Real Decreto **311/2022, de 3 de mayo**, por el que se regula el **Esquema Nacional de Seguridad**. Dimensiones, categorías y medidas del Anexo II; en este tema, especialmente `op.acc.1-6` (control de acceso), `op.exp.1-10` (explotación), `op.mon.1-3` (**detección de intrusión, sistema de métricas y vigilancia**), `mp.com.1-4` (**perímetro seguro; protección de la confidencialidad; protección de la integridad y de la autenticidad; separación de flujos de información en la red**) y `mp.eq.4` (otros dispositivos conectados a la red). |
| `[CCN-STIC]` | Centro Criptológico Nacional. *Guías CCN-STIC serie 800* — **803** (valoración de sistemas), **804** (medidas de implantación del ENS) y **817** (gestión de ciberincidentes), junto con las guías de configuración segura de electrónica de red. |
| `[RGPD]` | Reglamento (UE) **2016/679**. Arts. 5 (minimización y limitación de la finalidad), 6 (licitud), 25 (protección desde el diseño y por defecto), 30 (registro de actividades de tratamiento), 32 (seguridad del tratamiento) y 33-34 (notificación de brechas). Aplicable a los registros de red que permiten identificar a personas. |
| `[LOPDGDD]` | Ley Orgánica **3/2018**, de 5 de diciembre. Deber de confidencialidad y **derechos digitales en el ámbito laboral**: art. **87** (intimidad frente al uso de dispositivos digitales), art. **88** (desconexión digital), art. **89** (videovigilancia) y art. **90** (geolocalización). |
| `[L40-2015]` | Ley **40/2015**, de 1 de octubre, de Régimen Jurídico del Sector Público. Título preliminar, capítulo V: funcionamiento electrónico del sector público. Y, sobre todo, **artículo 156**, rubricado *«Esquema Nacional de Interoperabilidad y Esquema Nacional de Seguridad»*, cuyo apartado 1 define el **ENI** y cuyo apartado 2 establece que el **ENS** tiene por objeto fijar la política de seguridad en el uso de medios electrónicos, con sus principios básicos y requisitos mínimos (verificado contra el texto consolidado del BOE). |
| `[ENI]` | Real Decreto **4/2010**, de 8 de enero, por el que se regula el **Esquema Nacional de Interoperabilidad**, y sus Normas Técnicas de Interoperabilidad. |

## Tier 2 — Implementaciones, productos y herramientas

| ID | Referencia |
|---|---|
| `[MS-AD]` | Microsoft. *Active Directory Domain Services* — estructura lógica (bosque, árbol, dominio, unidad organizativa), estructura física (sitios y controladores de dominio), esquema, catálogo global y replicación multimaestro. |
| `[MS-GPO]` | Microsoft. *Group Policy* — objetos de directiva de grupo, orden de aplicación **L-S-D-UO**, herencia, bloqueo, aplicación forzada, filtrado por seguridad y por WMI, plantillas administrativas. |
| `[MS-DNS]` | Microsoft. *DNS Server* y *DHCP Server* en Windows Server — zonas integradas en el directorio, registros **SRV** de localización de servicios y actualización dinámica segura. |
| `[MS-ENTRA]` | Microsoft. *Entra ID* (antes Azure AD) e *Intune* — identidad en la nube, unión híbrida del dispositivo, acceso condicional y gestión moderna del puesto. Citados como ejemplo de la evolución del directorio clásico. |
| `[OPENLDAP]` | The OpenLDAP Project. *OpenLDAP Software Administrator's Guide*, junto con los proyectos **FreeIPA** y **Samba AD**. Implementaciones libres de directorio y de dominio. |
| `[FREERADIUS]` | The FreeRADIUS Project y *PacketFence*. Servidor RADIUS y control de admisión a la red de código abierto. |
| `[SWITCH-VENDORS]` | Documentación de electrónica de red de campus (Cisco IOS/NX-OS, Juniper Junos, Aruba/HPE, Extreme, MikroTik). Citada para ilustrar conmutación, VLAN, agregación, QoS y espejo de puertos sin atar el tema a un fabricante. |
| `[NETMGMT-TOOLS]` | Plataformas de monitorización y gestión: **Zabbix**, **Nagios**, **Icinga**, **LibreNMS**, **PRTG**, **Prometheus** con `snmp_exporter`, **Grafana**, **NetBox** (fuente de verdad de la infraestructura) y **Oxidized/RANCID** (respaldo de configuraciones). |
| `[FLOW-TOOLS]` | Colectores y analizadores de flujos: **nfdump/NfSen**, **pmacct**, **ElastiFlow**, **Akvorado** y colectores comerciales. |
| `[WIRESHARK]` | The Wireshark Foundation. *Wireshark User's Guide*, junto con `tcpdump` y `libpcap`. Captura y análisis de paquetes, filtros de captura (BPF) y de visualización. |
| `[SIEM]` | Plataformas de correlación y registro: **Elastic Stack**, **Graylog**, **Wazuh**, **Splunk**, **OpenSearch**; y **Suricata** y **Zeek** como sondas de detección. |
| `[ANSIBLE]` | Red Hat. *Ansible* y sus colecciones de red; alternativas **NAPALM**, **Nornir** y **Terraform**. Automatización y configuración como código de la electrónica de red. |
| `[UEM]` | Plataformas de gestión unificada de dispositivos e inventario: **Intune**, **Jamf**, **GLPI** con **FusionInventory**, **OCS Inventory**, **Ivanti**. |
| `[WSUS]` | Microsoft. *Windows Server Update Services*; en Linux, réplicas locales de repositorios (`apt-mirror`, `dnf reposync`) y **Uyuni**/**Landscape**. Distribución controlada de actualizaciones. |
| `[PXE]` | Especificación *Preboot Execution Environment* y **UEFI HTTP Boot**; herramientas de despliegue por red (**FOG**, **MDT**, **Clonezilla**, **Autopilot**). |
| `[IPAM]` | Herramientas de gestión de direccionamiento (**IPAM**) e inventario de red: **phpIPAM**, **NetBox**, **NIPAP**. |
| `[PROPIETARIOS]` | Protocolos propietarios y su equivalente abierto, citados por pares para evitar la confusión más habitual: **VTP** frente a **MVRP**; **PAgP** frente a **LACP**; **CDP** frente a **LLDP**; **HSRP/GLBP** frente a **VRRP**; tecnologías de apilado y de chasis virtual frente a la agregación normalizada. |

## Tier 3 — Marco administrativo y organizativo (contexto)

| ID | Referencia |
|---|---|
| `[IAM-MAD]` | Organismo Autónomo **Informática del Ayuntamiento de Madrid (IAM)** — responsable de los sistemas de información, de la red corporativa y del puesto de trabajo municipal. Contexto institucional de los ejemplos del tema. |
| `[ROGA]` | Reglamento Orgánico del Gobierno y de la Administración del Ayuntamiento de Madrid, de 31 de mayo de 2004. Áreas de Gobierno y **21 Distritos**: estructura sobre la que se distribuye la red corporativa y el parque de dispositivos. Ver Temas 3 y 4. |
| `[TRANSP-MAD]` | Portal de Transparencia y sede electrónica del Ayuntamiento de Madrid. Servicios electrónicos municipales que dependen de la red de área local de cada sede. |
| `[BOAM10032]` | BOAM 10.032 (23-dic-2025). Bases específicas TIC C1 Ayto. Madrid — temario oficial y estructura del ejercicio. |

---

*Las referencias Tier 1 fijan el fundamento del tema en dos familias de estándares. La primera es la del **IEEE 802**, que gobierna cuanto ocurre en el nivel de enlace de una red de área local: etiquetado de VLAN y troncales (802.1Q), árbol de expansión (802.1D y su evolución RSTP/MSTP), agregación de enlaces (802.1AX), control de admisión por puerto (802.1X), descubrimiento de vecinos (802.1AB) y cifrado de nivel 2 (802.1AE). La segunda es la del **IETF**, que aporta los servicios y los protocolos de gestión: DHCP y DNS como servicios que hacen utilizable la red; SNMP y NETCONF como interfaces de administración; syslog y NTP como cimiento del registro de eventos; NetFlow/IPFIX y sFlow como instrumentos de análisis de tráfico; y DiffServ como marco de la calidad de servicio. A ellas se suman los estándares de identidad —X.500 y LDAP, Kerberos, RADIUS y EAP, y el RBAC del NIST— sobre los que descansa la gestión de usuarios, y la normativa española que condiciona cualquier administración de red en el sector público: el ENS, con sus grupos de medidas `op.acc`, `op.exp`, `op.mon` y `mp.com`, y el RGPD junto con la LOPDGDD, que convierten los registros de red y de tráfico en tratamientos de datos personales sujetos a límites. Tier 2 documenta implementaciones y herramientas concretas citadas como ejemplo: el opositor debe reconocer el mecanismo, no memorizar una marca. Tier 3 sitúa el supuesto municipal.*
