# Tema 30 — Casos Prácticos

> **Título oficial**: Administración de redes de área local. Gestión de usuarios. Gestión de dispositivos. Monitorización y control de tráfico.
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos recorren el supuesto de referencia del tema (ver tema-30-contenido.md, «Convenciones»): la **red de área local de una sede de distrito** que alberga una Oficina de Atención a la Ciudadanía. El **Caso 1** trabaja el **diseño de la red y su segmentación**; el **Caso 2**, la **gestión de usuarios y de accesos** tras una reorganización administrativa; y el **Caso 3**, la **monitorización, el análisis del tráfico y el control de admisión** ante un incidente real.

---

## Caso 1 — Diseño y segmentación de la red de una sede de distrito

### Enunciado

El Ayuntamiento va a poner en servicio una **sede de distrito** de nueva construcción, con tres plantas y el siguiente equipamiento previsto:

- **180 puestos administrativos** de tramitación en las plantas primera y segunda.
- Una **Oficina de Atención a la Ciudadanía** en planta baja, con **14 puestos de mostrador** que atienden público y manejan documentación de terceros.
- **Telefonía IP** en todos los puestos (unos 200 terminales), alimentada por PoE.
- **6 impresoras multifunción** y **4 escáneres de mostrador** compartidos.
- **22 cámaras de videovigilancia** de un contrato de seguridad ajeno al departamento de sistemas.
- Una **sala de reuniones** con equipo de videoconferencia.
- **Red inalámbrica** con dos usos: personal municipal con portátil, y visitantes en la zona de espera de la planta baja.
- Un **armario de comunicaciones por planta**, más el principal en planta baja.

Se dispone del bloque de direccionamiento privado **10.42.0.0/20** para la sede.

### Cuestiones

**Cuestión 1 — Segmentación (3 puntos).** Proponga el esquema de **VLAN** de la sede, indicando para cada una su **propósito** y la **razón** por la que se separa. Justifique expresamente el tratamiento de las cámaras y de la red de visitantes.

**Cuestión 2 — Arquitectura y redundancia (3 puntos).** Describa la **arquitectura física y lógica** de la sede: capas, tipo de puerto en cada tramo y mecanismos de redundancia. Indique **qué protecciones** deben activarse en los puertos de acceso y por qué.

**Cuestión 3 — Direccionamiento y servicios (2 puntos).** Reparta el bloque `10.42.0.0/20` entre las VLAN propuestas, dimensionando la de datos de tramitación con margen de crecimiento. Indique **cómo** se entregará la configuración a los equipos y **qué mecanismo** permite tener un único servidor DHCP central.

**Cuestión 4 — Calidad de servicio (2 puntos).** Defina el esquema de **calidad de servicio** de la sede: dónde se sitúa la frontera de confianza, qué clases se definen y dónde está el punto real de congestión.

### Solución orientativa

- **C1**: (§1.1.1, §1.1.2) Ocho VLAN, cada una con una justificación distinta:

| VLAN | Propósito | Razón de la separación |
|---|---|---|
| **Datos de tramitación** | 180 puestos administrativos | Contención del dominio de difusión y política homogénea de puesto |
| **Oficina de Atención a la Ciudadanía** | 14 puestos de mostrador | Puestos **expuestos al público** que manejan datos de terceros: exigen directivas más estrictas y filtrado propio |
| **Voz** | 200 teléfonos IP | Calidad de servicio y direccionamiento propios; el terminal la descubre por LLDP-MED |
| **Impresión** | Impresoras y escáneres | Dispositivos que **no deben iniciar conexiones** hacia ningún sitio: se les permite recibir, no salir |
| **Videovigilancia** | 22 cámaras | Contrato ajeno, firmware fuera del control del departamento, sin agente posible: **confinamiento** |
| **Inalámbrica corporativa** | Portátiles del personal | Acceso equivalente al cableado, pero con autenticación propia |
| **Invitados** | Visitantes en zona de espera | Solo salida a internet y **ningún** acceso a la red interna |
| **Gestión** | Direcciones de administración de la electrónica | Separada del plano de datos y accesible solo desde puestos de administración |

  El tratamiento de las **cámaras** merece justificación expresa: son dispositivos que nadie considera informática, llegan por un contrato ajeno, rara vez admiten agente y casi nunca se actualizan. El ENS los contempla en la medida **`mp.eq.4` (otros dispositivos conectados a la red)**, y la respuesta correcta es confinarlas en una VLAN sin capacidad de iniciar conexiones hacia el resto y con su firmware bajo seguimiento en el inventario. La **red de visitantes** exige separación en tres niveles simultáneos: **nivel 2** (VLAN propia), **nivel 3** (encaminamiento que solo permite salida a internet) y **política** (portal con condiciones de uso). Quitar cualquiera de los tres deja un agujero. Todo el diseño se ampara en la medida **`mp.com.4` — separación de flujos de información en la red** [ENS].

- **C2**: (§1.1.1, §1.1.3) Arquitectura de **dos capas** (núcleo colapsado), que es la adecuada a una sede de este tamaño: un **conmutador de acceso por planta** —o pila de conmutadores, según densidad de puertos— y una **pareja de conmutadores de distribución** en el armario principal, que asume también la función de núcleo local y la frontera de nivel 3 mediante **interfaces virtuales de VLAN (SVI)**, una por segmento, que actúan como puerta de enlace predeterminada. Tipos de puerto: **acceso** hacia los equipos finales —con la excepción del puerto del teléfono IP, que además transporta la VLAN de voz etiquetada— y **troncal** entre conmutadores, hacia los puntos de acceso inalámbricos y hacia cualquier servidor de virtualización local.

  Redundancia en tres planos: **agregación de enlaces (802.1AX con LACP)** entre cada conmutador de planta y la distribución, que suma capacidad y evita que el árbol de expansión bloquee; **árbol de expansión** activo como red de seguridad, con el **puente raíz fijado por configuración** en uno de los conmutadores de distribución y el secundario en el otro; y **VRRP** entre ambos para la puerta de enlace de cada VLAN, de modo que la avería de un conmutador de distribución sea transparente para el mostrador.

  Protecciones obligadas en los **puertos de acceso**: **puerto de borde** —para que el usuario obtenga dirección sin esperar la convergencia—, **guarda de BPDU** —que deshabilita el puerto si alguien conecta un conmutador—, **guarda de raíz**, **control de tormentas** de difusión, **seguridad de puerto** limitando las MAC aprendidas, e **inspección DHCP** con los puertos declarados no confiables salvo el que lleva al servidor legítimo, sobre la que se apoyan a su vez la **inspección ARP dinámica** y la **guarda de origen IP**.

- **C3**: (§1.2.1) El bloque `10.42.0.0/20` ofrece 4096 direcciones, más que suficiente. Reparto razonable:

| VLAN | Subred | Direcciones útiles | Comentario |
|---|---|---|---|
| Datos de tramitación | `10.42.0.0/23` | 510 | 180 puestos + portátiles + margen del 20 % a tres años |
| Oficina de Atención a la Ciudadanía | `10.42.2.0/24` | 254 | 14 puestos, holgado |
| Voz | `10.42.4.0/23` | 510 | 200 teléfonos con margen |
| Impresión | `10.42.6.0/24` | 254 | Todas con **reserva** DHCP, no con dirección fija |
| Videovigilancia | `10.42.7.0/24` | 254 | 22 cámaras |
| Inalámbrica corporativa | `10.42.8.0/23` | 510 | Concesiones cortas |
| Invitados | `10.42.10.0/23` | 510 | Concesiones muy cortas: los visitantes se van |
| Gestión | `10.42.15.0/24` | 254 | Electrónica de red |

  La configuración se entrega por **DHCP** (máscara, puerta de enlace, servidores DNS internos, sufijo de dominio y servidores NTP). El mecanismo que permite un **único servidor central** para las ocho VLAN es el **agente de retransmisión** configurado en cada interfaz virtual del conmutador de distribución, que convierte la difusión del cliente en unidifusión hacia el servidor e indica de qué subred procede. Conviene además activar la **opción 82**, que añade conmutador y puerto de origen y convierte el registro de concesiones en una traza que dice desde qué roseta se pidió cada dirección. Criterio de administración: **reservar, no fijar** —una dirección configurada a mano en el equipo queda fuera del control del administrador—, salvo en la propia electrónica de red.

- **C4**: (§4.1.3, §4.1.4) **Frontera de confianza** en el puerto de acceso: se confía en el marcado del **teléfono IP**, identificado por LLDP-MED, y **no** en el del ordenador conectado tras él, cuyo tráfico se remarca salvo el de las aplicaciones corporativas identificadas. **Clases**: voz **EF (DSCP 46)** en cola de prioridad estricta **con límite máximo**; vídeo de la sala de reuniones **AF41 (34)**; señalización de telefonía **CS3 (24)** —poco caudal pero crítica: sin señalización no hay llamada aunque la voz tenga prioridad—; aplicaciones de tramitación **AF21 (18)**; y copias de seguridad y actualizaciones en **mejor esfuerzo (0)**, con modelado en horario laboral. **Punto real de congestión**: dentro del edificio sobra capacidad; el cuello de botella es el **enlace hacia el centro de proceso de datos**, y es ahí donde el encolamiento tiene efecto. El marcado se hace en el acceso; el encolamiento, en la distribución y en ese enlace. Verificación con **sondas sintéticas** que midan retardo, fluctuación y pérdida antes y después: una configuración de calidad de servicio que no se mide es una creencia.

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Esquema de VLAN completo con justificación por segmento, y tratamiento razonado de cámaras e invitados | 3 |
| Arquitectura, tipos de puerto, tres planos de redundancia y protecciones de borde correctas | 3 |
| Reparto de direccionamiento coherente con margen, y agente de retransmisión correctamente justificado | 2 |
| Frontera de confianza, clases con sus valores y localización correcta del punto de congestión | 2 |

---

## Caso 2 — Gestión de usuarios y accesos tras una reorganización administrativa

### Enunciado

Una reorganización traslada a **60 empleados** entre distritos y crea un nuevo **servicio de tramitación electrónica** con 12 personas procedentes de cuatro unidades distintas. En la revisión previa al traslado, una auditoría interna detecta lo siguiente en el directorio corporativo:

- Existen **340 cuentas habilitadas** de personas que causaron baja hace más de un año.
- **Los permisos sobre carpetas compartidas están concedidos, en su mayoría, a cuentas individuales**, no a grupos.
- Varias personas conservan acceso a la documentación de **dos y tres destinos anteriores**.
- El personal técnico de los distritos utiliza **su cuenta ordinaria** para tareas administrativas, y esa misma cuenta tiene correo y navegación.
- Existen **cinco cuentas genéricas** de mostrador, compartidas por los turnos de la Oficina de Atención a la Ciudadanía, cuya contraseña conocen unas veinte personas.

### Cuestiones

**Cuestión 1 — Diagnóstico normativo (2 puntos).** Clasifique los cinco hallazgos e indique, para cada uno, **qué medida del ENS** resulta incumplida o comprometida.

**Cuestión 2 — Modelo de permisos (3 puntos).** Explique cómo debe rediseñarse la concesión de permisos y **cuánto simplifica** eso el traslado de los 60 empleados. Ilustre con el caso de una persona que pasa del Distrito A al Distrito B.

**Cuestión 3 — Estructura y directivas (3 puntos).** Proponga la **estructura de unidades organizativas** y el uso de **directivas de grupo** para dar tratamiento diferenciado a los puestos de mostrador. Explique qué ocurre si una directiva del dominio está marcada como forzada y la unidad organizativa tiene el bloqueo de herencia activado.

**Cuestión 4 — Cuentas privilegiadas y genéricas (2 puntos).** Indique cómo deben tratarse las cuentas del personal técnico y las cinco cuentas genéricas de mostrador.

### Solución orientativa

- **C1**: (§2.1.3, §2.2.4) Diagnóstico y encaje normativo:

| Hallazgo | Naturaleza | Medida del ENS comprometida |
|---|---|---|
| 340 cuentas de personas de baja | Cuentas **huérfanas**: superficie de ataque y trazabilidad falseada | **`op.acc.4`** proceso de gestión de derechos de acceso |
| Permisos concedidos a cuentas individuales | Modelo insostenible: imposible auditar y mantener | **`op.acc.2`** requisitos de acceso; contraviene el modelo RBAC |
| Acceso a destinos anteriores | **Acumulación de privilegios**: incumple el mínimo privilegio | **`op.acc.4`**, mediante la revisión periódica de accesos |
| Cuenta ordinaria usada para administrar | Correo y navegación —los dos vectores de compromiso habituales— bajo identidad privilegiada | **`op.acc.3`** segregación de funciones y tareas; **`op.acc.6`** mecanismo de autenticación |
| Cuentas genéricas compartidas | Destruye la **trazabilidad**, que es una de las cinco dimensiones del ENS | **`op.acc.1`** identificación; **`op.exp.8`** registro de la actividad |

- **C2**: (§2.1.3, §2.2.4) El rediseño consiste en aplicar el anidamiento **AGDLP**: las **cuentas (A)** se incluyen en **grupos globales (G)** que representan **quién es alguien** —perfil, servicio, distrito—; esos grupos globales se incluyen en **grupos locales de dominio (DL)** que representan **a qué da derecho algo** —lectura de una carpeta, uso de una impresora, acceso a una aplicación—; y es al grupo local de dominio al que se concede el **permiso (P)** sobre el recurso. Los permisos **nunca** se conceden a cuentas ni directamente a grupos globales.

  El efecto sobre el traslado es la clave de la respuesta. Con el modelo actual, mover a una persona del Distrito A al Distrito B exige **localizar uno a uno** todos los recursos donde aparece su cuenta —carpetas, impresoras, aplicaciones, buzones compartidos— y modificarlos, con la certeza estadística de olvidar alguno; multiplicado por 60 personas, es un trabajo de semanas cuyo resultado previsible son los accesos residuales que la propia auditoría acaba de detectar. Con **AGDLP**, la operación completa para esa persona consiste en **quitarla del grupo global `Tramitacion-Distrito-A` y añadirla al grupo global `Tramitacion-Distrito-B`**: dos operaciones, efecto inmediato y simultáneo sobre todos los recursos, y un registro claro de quién hizo el cambio y cuándo. Los 60 traslados pasan de semanas a una tarde. El nuevo **servicio de tramitación electrónica** se resuelve creando un grupo global propio y añadiendo a las 12 personas, con independencia de sus unidades de procedencia. Es la traducción operativa del modelo **RBAC** [NIST-RBAC].

- **C3**: (§2.1.2, §2.2.2, §2.2.3) **Estructura**: un **único dominio** —multiplicar dominios multiplica el coste de administración sin aportar seguridad, ya que el límite real de seguridad es el **bosque**—, con un primer nivel de **unidades organizativas** por ámbito territorial o funcional (los Distritos y las Áreas de Gobierno) y un segundo nivel por **tipo de objeto** (usuarios, equipos, cuentas de servicio, grupos). Principio de diseño: la estructura de unidades organizativas debe responder a **cómo se administra** la organización, no a su organigrama, que cambia con cada legislatura. Sobre ella se **delega** a los técnicos de cada distrito la capacidad de restablecer contraseñas y desbloquear cuentas **de su ámbito**, sin ser administradores de nada más: es la aplicación de **`op.acc.3`**.

  **Directivas**: una unidad organizativa propia para los **equipos de la Oficina de Atención a la Ciudadanía**, con una GPO que fije **bloqueo automático de pantalla por inactividad breve**, deshabilite el almacenamiento extraíble y configure la impresora del mostrador. La justificación es que son puestos **de cara al público**, con documentación de terceros en pantalla y personas al otro lado del mostrador; a un despacho cerrado se le aplicará un tiempo de bloqueo más laxo. Se corresponde con las medidas **`mp.eq.1`** (puesto de trabajo despejado) y **`mp.eq.2`** (bloqueo de puesto de trabajo) [ENS].

  Sobre la pregunta de precedencia: si la directiva del **dominio está marcada como forzada**, **se aplica igualmente** pese al bloqueo de herencia de la unidad organizativa. La marca de forzada prevalece tanto sobre las directivas que se aplican después como sobre el bloqueo de herencia; es precisamente el mecanismo con el que la organización garantiza que sus ajustes mínimos alcanzan a todo el parque, incluidos los ámbitos que han bloqueado la herencia.

- **C4**: (§2.2.4) **Personal técnico**: cada técnico debe disponer de **dos cuentas**, una ordinaria para su trabajo diario —con correo y navegación— y otra **administrativa separada**, sin correo ni navegación, protegida con **segundo factor** y utilizada solo desde puestos de administración. El motivo es directo: el correo y la navegación son los dos vectores habituales de compromiso, y no deben ocurrir nunca bajo una identidad privilegiada. Cuando sea viable, sustituir la pertenencia permanente a grupos de administradores por **elevación temporal** acotada a una tarea y a un plazo.

  **Cuentas genéricas de mostrador**: son el hallazgo más grave en términos de trazabilidad, porque hacen imposible atribuir una consulta a un expediente a una persona concreta. La solución correcta es **suprimirlas y sustituirlas por cuentas nominativas**, apoyadas si es preciso en un mecanismo de inicio de sesión rápido —tarjeta criptográfica del empleado— que haga el cambio de turno ágil y no penalice la atención al público. Si, por una razón operativa acreditada, alguna resultara inevitable, debe quedar **documentada y justificada**, con **ámbito mínimo**, contraseña rotada, **prohibición expresa** de usarla para acceder a datos personales de ciudadanos, y compensada con otros registros que permitan reconstruir quién estaba en el mostrador en cada franja. En paralelo, las **340 cuentas de personas de baja** deben deshabilitarse de inmediato —no borrarse, para conservar la trazabilidad histórica y no perder los identificadores de seguridad asociados a los permisos— y someterse después al procedimiento de baja definitiva.

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Los cinco hallazgos clasificados y correctamente asociados a medidas del ENS | 2 |
| AGDLP explicado con precisión y efecto sobre el traslado bien argumentado con el ejemplo | 3 |
| Estructura de unidades organizativas justificada, uso de GPO diferenciado y regla de la directiva forzada correcta | 3 |
| Separación de la cuenta administrativa y tratamiento razonado de las cuentas genéricas | 2 |

---

## Caso 3 — Un incidente en la red: saturación, dispositivo desconocido y respuesta

### Enunciado

Durante tres semanas, los usuarios de la sede de distrito se quejan de **lentitud generalizada entre las 9:00 y las 9:45**, y en dos ocasiones se ha cortado una videoconferencia de la sala de reuniones. El sistema de monitorización muestra que el **enlace hacia el centro de proceso de datos alcanza el 100 % de utilización** en esa franja, pero no indica qué lo consume.

Al revisar el asunto, además, se detecta un **equipo con dirección de la VLAN de datos que no consta en el inventario** y que mantiene comunicación continua con una dirección externa.

La sede es un sistema de **categoría MEDIA** conforme al ENS.

### Cuestiones

**Cuestión 1 — Instrumento de análisis (2 puntos).** Indique **qué instrumento** permite averiguar quién consume el enlace y **por qué no sirven** ni SNMP ni una captura completa de paquetes. Describa el resultado esperable y las soluciones posibles ordenadas por coste.

**Cuestión 2 — El dispositivo desconocido (3 puntos).** Describa cómo **localizarlo físicamente** y qué **medidas de contención** aplicar. Indique qué mecanismos habrían impedido que un equipo no inventariado obtuviera acceso.

**Cuestión 3 — Registros y protección de datos (3 puntos).** Enumere los **registros** que deben existir para poder investigar el incidente, y explique los **límites jurídicos** que condicionan tanto el registro del tráfico como una eventual captura de paquetes.

**Cuestión 4 — Cierre y mejora (2 puntos).** Indique qué debe quedar tras el incidente y qué **medidas del ENS** resultan implicadas, considerando que la sede es de categoría MEDIA.

### Solución orientativa

- **C1**: (§4.2.2) El instrumento adecuado son los **registros de flujo** —**NetFlow v9**, **IPFIX** o **sFlow**— exportados desde el conmutador de distribución hacia un colector. **SNMP no sirve** porque ya responde a la pregunta del *cuánto* —la interfaz está al 100 %— y sondearlo con más frecuencia no añade el *quién*: los contadores de la MIB-II son agregados por interfaz y no distinguen conversaciones. Una **captura completa de paquetes no es el instrumento correcto** por tres motivos acumulados: generaría un volumen inmanejable durante tres semanas, la mayor parte del tráfico viaja cifrado —de modo que se obtendrían metadatos que el flujo ya da mucho más barato—, y recogería el contenido de comunicaciones de empleados y de ciudadanos sin necesidad, lo que sería **desproporcionado** [RGPD].

  **Resultado esperable**: los flujos de esa franja, ordenados por volumen, mostrarán un patrón de muchos orígenes de la VLAN de datos hacia un mismo destino externo por el puerto 443, coincidiendo con el encendido simultáneo de los equipos: el servicio de **actualizaciones del sistema operativo**. **Soluciones ordenadas de menor a mayor coste**: **(1)** desplazar la ventana de actualización a horario nocturno mediante directiva; **(2)** desplegar un **servidor de actualizaciones local o una caché** en la sede, de modo que la descarga se haga una vez y no doscientas [WSUS]; **(3)** limitar el caudal de esa clase con **calidad de servicio**, marcándola como mejor esfuerzo con modelado en horario laboral, lo que además impide que vuelva a cortarse la videoconferencia; y **(4)** solo en último término, **ampliar el enlace**. La lección de método es que la ampliación de capacidad es la solución más cara y con frecuencia la menos necesaria: sin datos de flujo habría sido la primera propuesta y no habría resuelto la causa.

- **C2**: (§1.2.1, §3.2.1, §3.2.3) **Localización física** en cuatro pasos: **(1)** obtener la **dirección MAC** asociada a esa IP en la tabla ARP del conmutador de distribución; **(2)** seguir esa MAC en la **tabla de direcciones** de los conmutadores hasta el puerto de acceso concreto en el que se aprende; **(3)** contrastar con el registro de **concesiones DHCP**, cuya **opción 82** indica directamente el conmutador y el puerto de origen —esto convierte una investigación de horas en una consulta de segundos—; y **(4)** identificar la roseta correspondiente en la documentación de cableado y acudir físicamente.

  **Contención inmediata**, antes de desplazarse: deshabilitar el puerto de acceso o moverlo a una **VLAN de cuarentena** sin salida; si el control de admisión está desplegado, basta con un **cambio de autorización (CoA)** de RADIUS para mover la sesión a cuarentena en caliente, sin esperar a que el equipo se desconecte. En paralelo, **preservar la evidencia**: registros de flujo del equipo, concesiones DHCP, registros de autenticación y una captura acotada si procede, todo ello con la debida cadena de custodia. Solo después conviene desconectar, porque desconectar primero destruye información.

  **Qué lo habría impedido**: el **control de admisión 802.1X**, que no habría dejado pasar más que EAPOL hasta autenticar el equipo contra el directorio; en su defecto, para dispositivos sin suplicante, **MAB** con la MAC dada de alta en el inventario, sabiendo que es un mecanismo débil que funciona como inventario aplicado y no como credencial; la **seguridad de puerto**, limitando las MAC aprendidas; y la conciliación periódica del **inventario administrativo con el técnico**, que es lo que revela precisamente el caso más preocupante: un equipo que comunica con la red y no consta en ningún sitio [ENS `op.exp.1`].

- **C3**: (§4.2.3) **Registros necesarios** para poder investigar, todos ellos centralizados en un servidor externo a los dispositivos que los generan y con **NTP** común, sin el cual los tiempos de distintos equipos no son comparables y la correlación es imposible:

  - **Concesiones DHCP** con opción 82: qué equipo tuvo qué dirección, cuándo y desde qué roseta.
  - **Registros de flujo** conservados: con quién habló ese equipo, cuánto y en qué momento, incluidas las tres semanas anteriores.
  - **Autenticaciones** contra el directorio y contra el servidor RADIUS, correctas y fallidas.
  - **Cambios de configuración** de la electrónica, con autor y contenido.
  - **Eventos de las protecciones de borde**: puertos deshabilitados por guarda de BPDU, violaciones de seguridad de puerto, cambios de estado de enlaces.
  - **Registros del propio sistema de gestión**, incluido quién consultó los registros.

  **Límites jurídicos**: una dirección IP asociada a un usuario identificado o identificable es **dato personal**, de modo que el registro de tráfico es un tratamiento sujeto al RGPD. Exige **finalidad determinada** —la seguridad del sistema y el cumplimiento del ENS la sostienen; la curiosidad o el control laboral encubierto, no—, **minimización**, **plazo de conservación definido y aplicado**, **inclusión en el registro de actividades de tratamiento** del art. 30, **acceso restringido y trazado**, e **información previa a la plantilla y a la representación de los trabajadores** sobre qué se registra y con qué fin, requisito reforzado por los **arts. 87 a 90 de la LOPDGDD** en materia de intimidad frente al uso de dispositivos digitales, videovigilancia y geolocalización. Para una eventual **captura de paquetes** los límites se intensifican, porque contiene el **contenido** de las comunicaciones: debe estar **autorizada**, **acotada** al tráfico estrictamente necesario —filtro de captura por dirección y puerto, y a ser posible solo cabeceras—, **custodiada** con acceso restringido y **borrada** cuando deja de ser necesaria. Capturar todo el tráfico del puesto para diagnosticar un problema de una aplicación concreta no es proporcionado [RGPD] [LOPDGDD].

- **C4**: (§4.2.4) **Qué debe quedar tras el incidente**: la **causa raíz corregida** —ventana de actualización desplazada y caché local desplegada—; la **calidad de servicio configurada y verificada** con sondas sintéticas que midan retardo, fluctuación y pérdida en la sala de reuniones; el **equipo desconocido identificado**, dado de alta o retirado, y su procedencia esclarecida; un **umbral de aviso** sobre la utilización del enlace que dispare antes de llegar al 100 %, para que la próxima vez la organización se entere por su monitorización y no por los usuarios tres semanas después; la **conciliación del inventario** ejecutada y convertida en tarea periódica; y un **plan de despliegue del control de admisión** en modo de supervisión, con redundancia del servidor RADIUS y comportamiento de contingencia definido, porque un control de seguridad que deja sin red al mostrador es en la práctica un incidente de disponibilidad.

  **Medidas del ENS implicadas**: **`op.exp.1`** (inventario de activos), incumplida de raíz por el equipo desconocido; **`op.mon.1`** (detección de intrusión) y **`op.mon.3`** (vigilancia), que es la que falla cuando una anomalía de tres semanas la detectan los usuarios; **`op.mon.2`** (sistema de métricas), en cuanto a umbrales que no avisaron; **`op.exp.8`** (registro de la actividad); **`mp.com.4`** (separación de flujos de información en la red) y **`mp.com.1`** (perímetro seguro), en cuanto a la contención; y **`op.exp.7`** (gestión de incidentes), en cuanto al tratamiento del propio incidente y su eventual notificación conforme a la guía **CCN-STIC 817**. Al tratarse de un sistema de **categoría MEDIA**, la sede está sujeta a **auditoría al menos bienal** —no a mera autoevaluación, que corresponde a la categoría básica—, de modo que los hallazgos y su corrección deberán poder acreditarse documentalmente ante el auditor [ENS] [CCN-STIC].

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Elección correcta del instrumento, descarte razonado de SNMP y de la captura, y soluciones ordenadas por coste | 2 |
| Localización física paso a paso, contención con preservación de evidencia y mecanismos preventivos correctos | 3 |
| Registros necesarios completos y límites jurídicos del RGPD y de la LOPDGDD bien expuestos | 3 |
| Cierre con causa raíz, mejora de la vigilancia y medidas del ENS correctamente citadas, incluida la auditoría bienal | 2 |
