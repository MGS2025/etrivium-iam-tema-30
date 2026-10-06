# Tema 30 — Checklist de Validación

> **Título oficial**: Administración de redes de área local. Gestión de usuarios. Gestión de dispositivos. Monitorización y control de tráfico.
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-27
> **Revisores**: María y Ana (eTrivium) · revisión técnica IAM (Jesús Cuadrado)
> **Instrucciones**: marcar cada ítem. Los cambios no se guardan en la web (imprimir o exportar a PDF si se desea fijarlos).

---

## 1. Cobertura del temario oficial

- [ ] **Fundamentos y arquitectura LAN**: modelo jerárquico de tres capas, núcleo colapsado, FCAPS, criterios de segmentación — §1.1.1
- [ ] **VLAN y troncales**: etiqueta 802.1Q campo a campo, puertos de acceso y troncales, VLAN nativa, VLAN de voz, encaminamiento entre VLAN — §1.1.2
- [ ] **Conmutación y redundancia**: STP, RSTP, MSTP, protecciones de borde, agregación de enlaces 802.1AX, VRRP — §1.1.3
- [ ] **DHCP**: ciclo DORA, puertos, concesiones y renovación, agente de retransmisión, opción 82, inspección DHCP — §1.2.1
- [ ] **DNS**: jerarquía y zonas, registros, resolución recursiva e iterativa, TTL, vista dividida, actualización dinámica, DNSSEC, DoT y DoH — §1.2.2
- [ ] **Servicios de directorio**: X.500 y LDAP, estructura lógica y física, sitios y controladores — §2.1.1
- [ ] **Dominios, árboles, bosques y unidades organizativas**: qué delimita cada pieza, confianzas, criterios de diseño de UO — §2.1.2
- [ ] **Objetos, cuentas, grupos y esquema**: identificador de seguridad, tipos de cuenta, ciclo de vida, ámbitos de grupo, AGDLP — §2.1.3
- [ ] **Autenticación en red**: AAA, Kerberos, LDAP bind, RADIUS, EAP, certificados, federación, multifactor, doctrina actual de contraseñas — §2.2.1
- [ ] **Directivas de grupo**: orden L-S-D-UO, herencia, bloqueo, forzada, filtrados, preferencias frente a directivas — §2.2.2
- [ ] **Directivas de seguridad y derechos**: líneas base, distinción permiso/derecho, denegación explícita, guías CCN-STIC — §2.2.3
- [ ] **RBAC y mínimo privilegio**: DAC, MAC, RBAC y ABAC; segregación de funciones, elevación temporal, recertificación — §2.2.4
- [ ] **Gestión centralizada de la electrónica**: inventario, normalización, control de versiones de configuración, automatización, ciclo de vida — §3.1.1
- [ ] **Interfaces de gestión**: CLI, web, SNMP, NETCONF, consola, puerto dedicado; dentro y fuera de banda — §3.1.2
- [ ] **Administración segura**: sustitución de protocolos en claro, cuentas nominativas, cuenta de emergencia, MACsec — §3.1.3
- [ ] **Ciclo de vida del puesto**: métodos de aprovisionamiento, PXE, inventario administrativo y técnico, conciliación — §3.2.1
- [ ] **Parches y firmware**: los seis pasos, priorización por exposición, despliegue por anillos, equipo no parcheable — §3.2.2
- [ ] **Control de admisión**: 802.1X y sus tres papeles, EAP, MAB, cuarentena, modo de supervisión, DevID, CoA — §3.2.3
- [ ] **Instrumentos de monitorización**: SNMP y MIB-II, ICMP, sondas sintéticas, syslog, telemetría, agentes — §4.1.1
- [ ] **Métricas**: disponibilidad y sus equivalencias, utilización y percentil 95, errores, MTBF/MTTR/MTTD — §4.1.2
- [ ] **Parámetros de calidad de servicio**: ancho de banda, retardo, fluctuación y pérdida; componentes del retardo; hinchazón de memorias intermedias — §4.1.3
- [ ] **Clasificación y marcado**: DiffServ, PCP frente a DSCP, valores de clase, cinco operaciones, frontera de confianza — §4.1.4
- [ ] **Captura de paquetes**: SPAN, RSPAN y TAP; filtros de captura y de visualización; método de análisis; límites — §4.2.1
- [ ] **Flujos**: quíntupla, NetFlow v9, IPFIX y sFlow; contraste con la captura; usos administrativos — §4.2.2
- [ ] **Registros y auditoría**: syslog y severidades, centralización, NTP, SIEM, conservación, dimensión de protección de datos — §4.2.3
- [ ] **ENS aplicado a la LAN**: dimensiones, niveles, categorías, medidas `op.acc`, `op.exp`, `op.mon`, `mp.com` y `mp.eq.4` — §4.2.4

## 2. Contenido teórico

- [ ] El nivel de profundidad (4 secciones, 8 subsecciones, 26 epígrafes, ~21.400 palabras) es adecuado para C1 (¿hay que ampliar o recortar alguna sección?)
- [ ] **Mapeo del esqueleto oficial**: el esqueleto de partida usa **cinco niveles de encabezado** (`##` a `#####`), y aquí se ha mapeado a **tres niveles numerados** (N / N.M / N.M.O) promoviendo cada `#####` al rango de su `####` hermano. **A validar por María/Jesús**: ¿es aceptable esa reducción, o se prefiere conservar los cinco niveles del esqueleto?
- [ ] El **equilibrio entre las cuatro materias del enunciado** (redes locales · usuarios · dispositivos · tráfico) es proporcionado, teniendo en cuenta que el enunciado oficial las enumera con el mismo rango
- [ ] Las **distinciones nucleares** quedan nítidas y sin ambigüedad: dominio de colisión / de difusión; puerto de acceso / troncal; VLAN nativa / etiquetada; STP / RSTP / MSTP; árbol de expansión / agregación de enlaces; estructura lógica / física del directorio; bosque / dominio / unidad organizativa; permiso / derecho; autenticación / autorización / contabilidad; dentro de banda / fuera de banda; PCP / DSCP; vigilancia / modelado; paquete / flujo; NetFlow / IPFIX / sFlow
- [ ] Los **puertos y números de norma** citados son correctos: 22, 23, 53, 67/68, 88, 123, 161/162, 389/636, 443, 514, 546/547, 830, 853, 1812/1813, 2055, 6343, 6514; y 802.1Q, 802.1D, 802.1w, 802.1s, 802.1AX, 802.1X, 802.1AB, 802.1AE, 802.1AR
- [ ] Los **datos del ENS (RD 311/2022)** son correctos: cinco dimensiones, tres niveles, tres categorías, tres bloques del Anexo II, auditoría bienal para media y alta y autoevaluación para básica. **Verificado contra el PDF consolidado del BOE**: `op.acc.1-6` (con `op.acc.5` usuarios externos y `op.acc.6` usuarios de la organización), `op.exp.8` registro de la actividad, `op.exp.10` **protección de claves criptográficas**, `op.mon.1-3` (detección de intrusión, sistema de métricas, vigilancia), `mp.com.4` **separación de flujos de información en la red** y `mp.eq.4` otros dispositivos conectados a la red
- [ ] Las referencias al **RGPD y a la LOPDGDD** son correctas: arts. 5, 6, 25, 30, 32 y 33-34 RGPD; arts. 87-90 LOPDGDD
- [ ] Los bloques añadidos más allá del enunciado literal del esqueleto (FCAPS, protecciones de borde del árbol de expansión, inspección DHCP y sus derivados, doctrina actual de contraseñas, hinchazón de memorias intermedias, equivalencias de disponibilidad, percentil 95) aportan valor y no desbordan el nivel C1
- [ ] La frontera con los Temas 11 y 12 (arquitectura y periféricos), 15 (bases de datos), 25 (puesto de usuario final), 28 (virtualización), 29 (control remoto y CAU), 31 (cloud), 32 (seguridad de sistemas), 33 (comunicaciones), 34 (TCP/IP), 35 (HTTP y TLS), 36 (seguridad perimetral y VPN), 37 (redes locales: tipología y dispositivos) y 39 (ENS/ENI) está clara y sin duplicidades innecesarias
- [ ] **Especialmente a validar**: la frontera con el **Tema 37** («Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión»). Este tema da esa materia por sabida y se ocupa de **administrarla**; conviene confirmar que el reparto es el que espera el IAM y que ningún contenido queda huérfano entre ambos
- [ ] Los ejemplos Ayto Madrid (sede de distrito con Oficina de Atención a la Ciudadanía, red corporativa, parque de dispositivos) son verosímiles y coherentes entre secciones, y están planteados como **supuesto simplificado** sin atribuir al Ayuntamiento ninguna arquitectura concreta

## 3. Fuentes

- [ ] Todas las afirmaciones técnicas están respaldadas por fuente Tier 1 (IEEE, IETF, ITU-T, NIST, ENS, RGPD)
- [ ] Las referencias inline se corresponden con `tema-30-fuentes.md`
- [ ] Los productos concretos citados (Cisco, Aruba, Zabbix, Wireshark, Active Directory, Intune, NetBox) figuran como **ejemplos ilustrativos** y el tema no depende de ninguna marca
- [ ] Los pares estándar/propietario están correctamente contrastados: MVRP/VTP, LACP/PAgP, LLDP/CDP, VRRP/HSRP y GLBP

## 4. Test (60 preguntas)

- [ ] Cada pregunta tiene una sola respuesta correcta e inequívoca
- [ ] Los distractores (A/B/C) son plausibles
- [ ] La distribución de la opción correcta entre A/B/C está equilibrada (**verificada 20/20/20** por el generador)
- [ ] Las explicaciones y referencias de cada respuesta son correctas
- [ ] El reparto por bloques (P1-P12 arquitectura, VLAN y redundancia; P13-P20 DHCP y DNS; P21-P32 directorio, autenticación, directivas y roles; P33-P44 gestión de dispositivos; P45-P60 monitorización, calidad, tráfico, registros y ENS) es proporcionado al peso de cada sección

## 5. Casos prácticos (3)

- [ ] Realistas y propios del Ayuntamiento (diseño y segmentación de una sede de distrito de nueva construcción; gestión de usuarios y accesos tras una reorganización administrativa; incidente de saturación con dispositivo desconocido en la red)
- [ ] Soluciones orientativas técnica y jurídicamente correctas
- [ ] La puntuación de cada caso suma 10 puntos
- [ ] El reparto de direccionamiento del Caso 1 es aritméticamente correcto y cabe en el bloque `10.42.0.0/20`

## 6. Diagramas (15 SVG)

- [ ] Cada diagrama es correcto y legible (también impreso en blanco y negro)
- [ ] Accesibilidad: todos tienen `role="img"` y `aria-label`, con tildes y eñes correctas dentro del atributo
- [ ] Sin desbordes de texto ni colisiones de estilo entre SVG (clases con sufijo único, QA de caja contenedora con render en navegador)
- [ ] **D11** (protocolos y puertos) y **D13** (marcado de calidad de servicio) son los dos diagramas de memorización directa: verificar cifra a cifra
- [ ] **D3** (etiqueta 802.1Q) refleja correctamente los tamaños de campo y el porqué de las 4094 VLAN utilizables

## 7. Referencias cruzadas a otros temas

- [ ] Validadas contra BOAM 10.032 — temas efectivamente citados en el contenido: **T5, T6, T7, T15, T25, T28, T29, T32, T33, T34, T36, T37 y T39**
- [ ] Ninguna referencia cruzada cita un enunciado de tema incorrecto

## 8. Calidad editorial

- [ ] Ortografía verificada (tildes y ñ) — sin diacríticos perdidos, también dentro de los `aria-label` de los SVG
- [ ] Coherencia de versión (v1.0) en title, badges, banner y footer del `index.html`
- [ ] El `index.html` abre, navega entre las 8 pestañas y el motor de test funciona
- [ ] Las listas anidadas del Contenido se muestran con sus niveles (sin aplanar)
- [ ] Las tablas comparativas se muestran correctamente y sin markdown crudo filtrado (comprobado el recuento de asteriscos residuales tras el build)

---

## Observaciones abiertas

_(Espacio para anotaciones de María, Ana y la revisión IAM.)_

- **Decisión a validar — mapeo del esqueleto**: el esqueleto oficial de este tema tiene cinco niveles de encabezado y se ha reducido a tres niveles numerados (ver §2 de esta lista). Es la misma cuestión que se planteó en el T27 y conviene resolverla de forma uniforme para toda la serie.
- **Frontera con el Tema 37**: es la más delicada de este tema, porque ambos hablan de redes locales. El criterio aplicado aquí es que el **T37 describe** (tipología, técnicas de transmisión, métodos de acceso, dispositivos de interconexión) y el **T30 administra**. Pendiente de confirmación por el IAM.
- **Sin fragmentos de código**: decisión de generación coherente con T26, T28 y T29. Este tema no compara lenguajes ni plataformas de desarrollo, sino protocolos, arquitecturas y procesos; lo memorizable son **puertos, números de norma, valores de campo y matrices**, no sintaxis. Se ha priorizado en su lugar la densidad de **tablas comparativas**. Pendiente confirmar si María o el IAM prefieren incluir algunos ejemplos de configuración de electrónica de red, con la advertencia de que atarían el tema a un fabricante.
- **Valores de referencia de calidad de servicio**: los umbrales de voz (150 ms de retardo, 30 ms de fluctuación, menos del 1 % de pérdida) se presentan expresamente como **objetivos de diseño ampliamente aceptados**, no como cifras normativas. Si el IAM dispone de los valores comprometidos en sus contratos de comunicaciones, conviene sustituirlos.
- **Direccionamiento del Caso 1**: el bloque `10.42.0.0/20` y su reparto son **ilustrativos**. Si el IAM facilita su plan real de direccionamiento por sede, el caso ganaría verosimilitud.
- **Sensibilidad a la obsolescencia**: la §3.2 (gestión moderna del puesto, plataformas UEM) y parte de la §4.1.1 (telemetría de flujo continuo) son las zonas más volátiles del tema; el resto es notablemente estable. Conviene revisarlas antes de cada convocatoria.
