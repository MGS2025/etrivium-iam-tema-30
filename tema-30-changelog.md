# Tema 30 — Changelog

> **Título oficial**: Administración de redes de área local. Gestión de usuarios. Gestión de dispositivos. Monitorización y control de tráfico.

---

## v1.0 — 2026-08-27 — Primera versión

**Estado**: pendiente de validación por María y Ana, y de revisión técnica del IAM (Jesús Cuadrado).

**Motivo**: desarrollo del Tema 30, dentro de la serie de temas técnicos generados desde cero, replicando la estructura y el formato de los Temas 1, 11 y 17-29 ya consolidados. Con él, el **bloque técnico queda completo de T11 a T30 sin huecos**.

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | ~21.400 palabras · 4 secciones (fieles a las cuatro materias del enunciado oficial) con 8 subsecciones y 26 epígrafes numerados |
| Diagramas SVG inline | 15 (accesibles con `role`/`aria-label`, clases con sufijo único anti-colisión) |
| Banco de preguntas tipo test | 60 preguntas A/B/C con explicación y referencia, balanceadas **20/20/20** (verificado por el generador) |
| Casos prácticos | 3 (diseño y segmentación de una sede de distrito; gestión de usuarios y accesos tras una reorganización; incidente de saturación con dispositivo desconocido) · 10 puntos cada uno |
| Fuentes Tier 1 | 44 referencias canónicas (IEEE 802, IETF, ITU-T, NIST, ENS, CCN-STIC, RGPD, LOPDGDD, ENI, Ley 40/2015) |

### Decisiones de generación

1. **Sin material de cliente**: solo el esqueleto `Test_Prompting/temas agosto/30.md`. Desarrollado desde fuentes canónicas (normas IEEE 802, RFC del IETF, recomendación X.500, publicaciones del NIST y normativa española ENS y RGPD/LOPDGDD), todas referenciadas con identificador inline.

2. **Mapeo del esqueleto — decisión a validar**. El esqueleto oficial usa **cinco niveles de encabezado** (`##` a `#####`), con dos irregularidades: algunos `####` funcionan como contenedores de dos `#####` y otros no tienen hijos, y el `#### Servicios de Red Fundamentales para la Administración LAN` está titulado como si fuera de tercer nivel. Se ha mapeado a la numeración canónica de **tres niveles** (N / N.M / N.M.O) de la serie, promoviendo cada `#####` al rango de su `####` hermano y elevando ese contenedor mal titulado a subsección (§1.2). El resultado son **4 secciones, 8 subsecciones y 26 epígrafes**, con **cobertura íntegra** de los 24 encabezados del esqueleto y sin añadir secciones nuevas de primer nivel ni reordenar. Es la misma cuestión que planteó el esqueleto del **T27**, y conviene resolverla de forma uniforme para toda la serie: queda anotada en la validación.

3. **El tema, leído como cuatro preguntas encadenadas**. El enunciado oficial reúne cuatro materias que en la práctica son cuatro tareas del mismo puesto de trabajo: cómo está construida la red, quién entra en ella, de qué está hecha y qué circula por ella. Se ha presentado así desde las Convenciones y se cierra con una sección de síntesis que las recorre, porque la unión de las cuatro es deliberada en el temario y un opositor que estudie solo la primera —que es la más «de red»— se deja fuera tres cuartas partes del tema.

4. **Frontera con el Tema 37 tratada como decisión explícita**. Es la frontera más delicada de la serie técnica, porque el T37 («Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión») y este tema hablan de lo mismo. El criterio aplicado: el **T37 describe** la red local y este tema la **administra**. En consecuencia, aquí no se explican qué es un conmutador, un concentrador o un encaminador, ni los métodos de acceso al medio; se da esa materia por sabida. Queda anotado en la validación para confirmación del IAM.

5. **Sin fragmentos de código** (decisión coherente con T26, T28 y T29). El tema no compara lenguajes ni plataformas de desarrollo, sino protocolos, arquitecturas y procesos. Lo memorizable son **puertos, números de norma, valores de campo y matrices**, no sintaxis; y cualquier ejemplo de configuración de electrónica ataría el tema a un fabricante concreto. Se ha priorizado en su lugar la **densidad de tablas comparativas**, que son el formato natural del contenido.

6. **Estándar frente a propietario, citados por pares**. Es una de las confusiones más rentables del examen y se ha tratado sistemáticamente: **MVRP** frente a VTP, **LACP** frente a PAgP, **LLDP** frente a CDP, **VRRP** frente a HSRP y GLBP. En todos los casos se identifica cuál es el normalizado, que es lo que se pregunta.

7. **Puertos y normas como material de memorización directa**, concentrados además en el diagrama **D11** para permitir el repaso rápido: 22 (SSH), 23 (Telnet, obsoleto), 53 (DNS), 67/68 (DHCP), 88 (Kerberos), 123 (NTP), 161/162 (SNMP), 389/636 (LDAP y LDAPS), 443 (HTTPS de gestión), 514 y 6514 (syslog), 546/547 (DHCPv6), 830 (NETCONF), 853 (DNS sobre TLS), 1812/1813 (RADIUS), 2055 (NetFlow e IPFIX) y 6343 (sFlow). El segundo diagrama de memorización directa es **D13**, con los valores de DSCP.

8. **ENS verificado contra el PDF consolidado del BOE**, no contra fuentes secundarias. Se descargó el texto consolidado del **RD 311/2022** y se contrastó la denominación literal de cada medida citada. Dos correcciones que ese contraste evitó, porque las fuentes secundarias consultadas las daban mal: **`op.exp.10`** es **«Protección de claves criptográficas»** (en el RD 3/2010 anterior era «Protección de los registros de actividad») y **`mp.com.4`** es **«Separación de flujos de información en la red»** (varias fuentes lo citan como «Segregación de redes», que era su denominación anterior). Se verificó igualmente contra el BOE el **artículo 156 de la Ley 40/2015**, rubricado «Esquema Nacional de Interoperabilidad y Esquema Nacional de Seguridad», que es el fundamento legal de ambos esquemas y se cita en §4.2.4. Confirmados igualmente `op.acc.1-6` —con `op.acc.5` para usuarios externos y `op.acc.6` para usuarios de la organización— y el grupo `op.mon.1-3`, cuya medida **`op.mon.3` (vigilancia)** es una de las reforzadas en la actualización de 2022.

9. **El ENS presentado como traducción del tema, no como apéndice**. En lugar de una sección normativa desconectada, cada bloque de medidas se ancla al epígrafe técnico que lo materializa, y el diagrama **D15** recoge esa correspondencia sección a sección. El objetivo es que el opositor reconozca que `mp.com.4` es la segmentación en VLAN que ya ha estudiado, y no un código más que memorizar.

10. **Protección de datos tratada como límite operativo, no como advertencia genérica**. Los registros de red y las capturas de tráfico se presentan como tratamientos de datos personales con requisitos concretos —finalidad, minimización, plazo, información previa a la plantilla, registro de actividades— y con los **arts. 87-90 de la LOPDGDD** citados por su contenido. Es materia de caso práctico y aparece desarrollada en el Caso 3.

11. **Caso de referencia único para todo el tema**: la **red de área local de una sede de distrito** con Oficina de Atención a la Ciudadanía, telefonía IP, impresión compartida, videovigilancia de contrato ajeno, red inalámbrica corporativa y de visitantes, y red de gestión. Planteado como **supuesto simplificado**, no como descripción de una arquitectura real del Ayuntamiento. Concentra todas las decisiones del tema y permite que los tres casos prácticos sean tres miradas al mismo edificio.

12. **Distribución A/B/C fijada ANTES de redactar** (práctica consolidada desde T24). Se predefinió la secuencia completa de 60 letras con 20 de cada una y se redactó cada pregunta contra su letra asignada. `build_t30.py` confirma **20/20/20 a la primera**, sin necesidad de permutaciones correctoras.

13. **Cómputo de extensión medido, no estimado**: la cifra de ~21.400 palabras procede de `wc -w` sobre el `.md`. Medido con el mismo criterio, este tema queda **prácticamente empatado con el T29** (≈21.200) como el más extenso de la serie técnica, y por delante de T28 (≈18.900) y T26 (≈17.600). La causa es la misma que en T29: el enunciado oficial une **cuatro materias completas** que en otros temarios se tratan por separado.

14. **Anti-colisión de SVG**: las clases CSS de cada diagrama llevan **sufijo único** (`.t1`…`.t9`, `.ta`…`.tf`, y equivalentes para el resto de clases), evitando el fallo sistémico de estilos que se filtran de un SVG a otro al estar todos embebidos en la misma página (lección de T5). Los marcadores de flecha llevan también identificador único por diagrama (`a4`, `a6`, `a7`, `a9`, `a10`, `a12`, `a13`).

15. **Conversor md→HTML con el fix de negrita anidada ya aplicado**: `inline()` usa `\*\*(.+?)\*\*` en lugar de `\*\*([^*]+)\*\*`, de modo que la negrita con cursiva dentro se convierte correctamente y no deja asteriscos crudos a la vista. Es el bug detectado en T26 y T27 y reaparecido en T29; aquí se incorpora desde el primer build. **Sigue pendiente portarlo al builder base de la serie** para que no vuelva a aparecer.

### Pendientes para QA / próxima iteración

- Validación de profundidad y de equilibrio entre las cuatro materias por María, Ana y el IAM.
- **Confirmar el criterio de mapeo del esqueleto** (cinco niveles reducidos a tres) y aplicarlo de forma uniforme a toda la serie, incluido el T27.
- **Confirmar la frontera con el Tema 37**, que es la más delicada del tema.
- Confirmar si conviene incluir ejemplos de configuración de electrónica de red, asumiendo la dependencia de un fabricante.
- Sustituir por datos reales, si el IAM los facilita, los valores ilustrativos de calidad de servicio y el plan de direccionamiento del Caso 1.
- Verificación ortográfica con corrector es_ES (cuidado con falsos positivos por términos técnicos en inglés: *trunk*, *portfast*, *snooping*, *shaping*, *policing*, *jitter*, *bufferbloat*, *scavenging*, *golden image*, *thin client*, *service desk*).

### Origen

Generado el 2026-08-27 en el flujo de trabajo de eTrivium, replicando el patrón de los Temas 1 (v2.1), 11 (v3.2) y 17-29 (v1.0). `build_t30.py` y `_build_css.txt` persistidos en el repo.
