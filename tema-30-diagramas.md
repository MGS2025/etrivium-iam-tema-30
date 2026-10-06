# Tema 30 — Catálogo de Diagramas

> **Título oficial**: Administración de redes de área local. Gestión de usuarios. Gestión de dispositivos. Monitorización y control de tráfico.
>
> **Versión**: v1.0
> **Fecha**: 2026-08-27
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)
> **Nota técnica**: las clases CSS de cada SVG llevan sufijo numérico único (`.t1`, `.h1`…) para evitar colisiones de estilos entre los 15 diagramas embebidos en la misma página.

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | El modelo jerárquico de tres capas y sus responsabilidades | §1.1.1 | Capas | 680×340 |
| D2 | Dominios de colisión y de difusión: qué reduce cada cosa | §1.1.1 | Comparativa | 680×320 |
| D3 | La etiqueta 802.1Q, campo a campo | §1.1.2 | Estructura de trama | 680×320 |
| D4 | Puerto de acceso frente a puerto troncal | §1.1.2 | Esquema de red | 680×340 |
| D5 | Redundancia sin bucles: STP, RSTP, MSTP y agregación | §1.1.3 | Comparativa | 680×362 |
| D6 | DHCP: el ciclo DORA y el agente de retransmisión | §1.2.1 | Flujo | 680×360 |
| D7 | DNS: jerarquía, resolución y tipos de registro | §1.2.2 | Árbol y flujo | 680×360 |
| D8 | Directorio: estructura lógica frente a estructura física | §2.1.1 | Comparativa | 680×360 |
| D9 | AGDLP y el orden de aplicación de directivas L-S-D-UO | §2.1.3, §2.2.2 | Flujo doble | 680×340 |
| D10 | Control de admisión 802.1X: los tres papeles | §3.2.3 | Flujo | 680×362 |
| D11 | Mapa de protocolos y puertos de administración y monitorización | §3.1.3, §4.1.1 | Tabla visual | 680×398 |
| D12 | Gestión dentro de banda frente a gestión fuera de banda | §3.1.2 | Comparativa | 680×310 |
| D13 | Marcado de calidad de servicio: PCP, DSCP y clases | §4.1.4 | Tabla visual | 680×384 |
| D14 | Paquetes frente a flujos: qué instrumento para qué pregunta | §4.2.1, §4.2.2 | Comparativa | 680×350 |
| D15 | El ENS aplicado a la red de área local | §4.2.4 | Mapa de medidas | 680×360 |

---

## D1 · El modelo jerárquico de tres capas y sus responsabilidades

**Sección**: §1.1.1 — Modelos de diseño jerárquico y segmentación de red
**Propósito**: Fijar qué hace y qué no debe hacer cada capa, y dónde se sitúa la frontera entre el nivel 2 y el nivel 3.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Modelo jerárquico de tres capas de una red de campus: capa de acceso que conecta a los usuarios, capa de distribución que agrega y aplica la política y encamina entre redes locales virtuales, y capa de núcleo que transporta a alta velocidad sin aplicar política; se indica qué hace y qué no debe hacer cada capa y dónde está la frontera entre el nivel 2 y el nivel 3">
  <style>.t1{font:700 12px system-ui,sans-serif;fill:#fff}.s1{font:9px system-ui,sans-serif;fill:#fff}.d1{font:9px system-ui,sans-serif;fill:#333}.h1{font:700 13px system-ui,sans-serif;fill:#0055a0}.k1{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n1{font:8.5px system-ui,sans-serif;fill:#666}.w1{font:9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h1">Modelo jerárquico de campus: tres capas, tres papeles</text>
  <text x="24" y="44" class="k1">CAPA</text><text x="200" y="44" class="k1">QUÉ HACE</text><text x="452" y="44" class="k1">QUÉ NO DEBE HACER</text>
  <rect x="20" y="52" width="160" height="50" rx="5" fill="#0055a0"/><text x="100" y="72" text-anchor="middle" class="t1">NÚCLEO</text><text x="100" y="88" text-anchor="middle" class="s1">transporte puro</text>
  <rect x="192" y="52" width="248" height="50" rx="4" fill="#eef3f8"/><text x="316" y="70" text-anchor="middle" class="d1">Conmutación de alta capacidad entre</text><text x="316" y="86" text-anchor="middle" class="d1">bloques y hacia el centro de datos</text>
  <rect x="452" y="52" width="208" height="50" rx="4" fill="#fbeaea"/><text x="556" y="78" text-anchor="middle" class="w1">Filtrados complejos que retarden</text>
  <rect x="20" y="112" width="160" height="50" rx="5" fill="#2d8659"/><text x="100" y="132" text-anchor="middle" class="t1">DISTRIBUCIÓN</text><text x="100" y="148" text-anchor="middle" class="s1">agrega y aplica política</text>
  <rect x="192" y="112" width="248" height="50" rx="4" fill="#eef3f8"/><text x="316" y="130" text-anchor="middle" class="d1">Encaminamiento entre VLAN, listas de</text><text x="316" y="146" text-anchor="middle" class="d1">control de acceso, agregación de enlaces</text>
  <rect x="452" y="112" width="208" height="50" rx="4" fill="#fbeaea"/><text x="556" y="138" text-anchor="middle" class="w1">Conectar equipos de usuario</text>
  <rect x="20" y="172" width="160" height="50" rx="5" fill="#e89822"/><text x="100" y="192" text-anchor="middle" class="t1">ACCESO</text><text x="100" y="208" text-anchor="middle" class="s1">conecta a los usuarios</text>
  <rect x="192" y="172" width="248" height="50" rx="4" fill="#eef3f8"/><text x="316" y="190" text-anchor="middle" class="d1">VLAN de acceso, PoE, 802.1X, marcado</text><text x="316" y="206" text-anchor="middle" class="d1">de calidad de servicio, guarda de BPDU</text>
  <rect x="452" y="172" width="208" height="50" rx="4" fill="#fbeaea"/><text x="556" y="198" text-anchor="middle" class="w1">Encaminar tráfico de tránsito</text>
  <line x1="20" y1="168" x2="660" y2="168" stroke="#0055a0" stroke-width="2" stroke-dasharray="6,3"/>
  <rect x="20" y="236" width="315" height="44" rx="4" fill="#f5f5f5" stroke="#0055a0" stroke-width="1"/>
  <text x="177" y="254" text-anchor="middle" class="k1">FRONTERA NIVEL 2 / NIVEL 3</text><text x="177" y="270" text-anchor="middle" class="d1">Normalmente en la capa de DISTRIBUCIÓN</text>
  <rect x="345" y="236" width="315" height="44" rx="4" fill="#f5f5f5" stroke="#2d8659" stroke-width="1"/>
  <text x="502" y="254" text-anchor="middle" class="k1">VARIANTE DE DOS CAPAS</text><text x="502" y="270" text-anchor="middle" class="d1">Núcleo colapsado: distribución y núcleo fundidos</text>
  <rect x="90" y="292" width="500" height="22" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="307" text-anchor="middle" class="k1">Regla de oro: la política se aplica en la distribución; el núcleo solo transporta</text>
  <text x="670" y="333" text-anchor="end" class="n1">[Fuente: SWITCH-VENDORS]</text>
</svg>
```

---

## D2 · Dominios de colisión y de difusión: qué reduce cada cosa

**Sección**: §1.1.1 — Modelos de diseño jerárquico y segmentación de red
**Propósito**: Deshacer la confusión más repetida del temario: qué delimita un dominio de colisión, qué delimita uno de difusión y qué efecto tiene realmente segmentar en VLAN.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Comparación entre dominio de colisión y dominio de difusión: el dominio de colisión coincide con cada puerto de conmutador y lo eliminó la conmutación, mientras que el dominio de difusión coincide con cada red local virtual o interfaz de encaminador; segmentar en VLAN reduce el dominio de difusión pero no el de colisión">
  <style>.t2{font:700 11px system-ui,sans-serif;fill:#fff}.s2{font:9px system-ui,sans-serif;fill:#fff}.d2{font:9px system-ui,sans-serif;fill:#333}.h2{font:700 13px system-ui,sans-serif;fill:#0055a0}.k2{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n2{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h2">Dominio de colisión frente a dominio de difusión</text>
  <rect x="20" y="34" width="316" height="30" rx="5" fill="#0055a0"/><text x="178" y="54" text-anchor="middle" class="t2">DOMINIO DE COLISIÓN</text>
  <rect x="344" y="34" width="316" height="30" rx="5" fill="#2d8659"/><text x="502" y="54" text-anchor="middle" class="t2">DOMINIO DE DIFUSIÓN</text>
  <text x="24" y="82" class="k2">¿QUÉ LO DELIMITA?</text>
  <rect x="20" y="88" width="316" height="30" rx="4" fill="#eef3f8"/><text x="178" y="107" text-anchor="middle" class="d2">Cada PUERTO de conmutador</text>
  <rect x="344" y="88" width="316" height="30" rx="4" fill="#eef3f8"/><text x="502" y="107" text-anchor="middle" class="d2">Cada VLAN, o cada interfaz de encaminador</text>
  <text x="24" y="136" class="k2">¿QUÉ TRÁFICO LO SATURA?</text>
  <rect x="20" y="142" width="316" height="30" rx="4" fill="#f5f5f5"/><text x="178" y="161" text-anchor="middle" class="d2">Transmisiones simultáneas en el medio</text>
  <rect x="344" y="142" width="316" height="30" rx="4" fill="#f5f5f5"/><text x="502" y="161" text-anchor="middle" class="d2">ARP, DHCP Discover, anuncios de servicios</text>
  <text x="24" y="190" class="k2">¿CÓMO SE REDUJO O SE REDUCE?</text>
  <rect x="20" y="196" width="316" height="34" rx="4" fill="#eef3f8"/><text x="178" y="211" text-anchor="middle" class="d2">Con la CONMUTACIÓN: en la práctica</text><text x="178" y="225" text-anchor="middle" class="d2">ya está eliminado en redes modernas</text>
  <rect x="344" y="196" width="316" height="34" rx="4" fill="#e8f4ee"/><text x="502" y="211" text-anchor="middle" class="d2">SEGMENTANDO en VLAN: es lo único</text><text x="502" y="225" text-anchor="middle" class="d2">que reduce el dominio de difusión</text>
  <rect x="20" y="242" width="640" height="26" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="259" text-anchor="middle" class="d2">Error clásico: «segmentar en VLAN reduce las colisiones». NO: reduce la DIFUSIÓN</text>
  <rect x="20" y="276" width="640" height="26" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="293" text-anchor="middle" class="k2">Dos VLAN nunca se comunican en nivel 2: hace falta encaminar (nivel 3)</text>
  <text x="670" y="315" text-anchor="end" class="n2">[Fuente: IEEE8023; IEEE8021Q]</text>
</svg>
```

---

## D3 · La etiqueta 802.1Q, campo a campo

**Sección**: §1.1.2 — Redes de área local virtuales (VLAN) y enlace de troncales
**Propósito**: Memorizar la estructura exacta de la etiqueta VLAN, sus tamaños de campo y el porqué de las 4094 VLAN utilizables. Diagrama de memorización directa.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Estructura de la etiqueta 802.1Q insertada en la trama Ethernet: identificador de protocolo de etiqueta de 16 bits con valor hexadecimal 8100, punto de código de prioridad de 3 bits, indicador de elegibilidad de descarte de 1 bit e identificador de red local virtual de 12 bits; la etiqueta añade 4 bytes a la trama y permite 4094 redes virtuales utilizables">
  <style>.t3{font:700 10px system-ui,sans-serif;fill:#fff}.s3{font:8.5px system-ui,sans-serif;fill:#fff}.d3{font:9px system-ui,sans-serif;fill:#333}.h3{font:700 13px system-ui,sans-serif;fill:#0055a0}.k3{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n3{font:8.5px system-ui,sans-serif;fill:#666}.b3{font:700 10px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h3">La etiqueta 802.1Q dentro de la trama Ethernet</text>
  <text x="24" y="42" class="k3">TRAMA SIN ETIQUETAR</text>
  <rect x="20" y="48" width="120" height="28" rx="3" fill="#888"/><text x="80" y="66" text-anchor="middle" class="t3">MAC destino</text>
  <rect x="144" y="48" width="120" height="28" rx="3" fill="#888"/><text x="204" y="66" text-anchor="middle" class="t3">MAC origen</text>
  <rect x="268" y="48" width="90" height="28" rx="3" fill="#aaa"/><text x="313" y="66" text-anchor="middle" class="t3">EtherType</text>
  <rect x="362" y="48" width="220" height="28" rx="3" fill="#ccc"/><text x="472" y="66" text-anchor="middle" style="font:700 10px system-ui;fill:#333">Datos</text>
  <rect x="586" y="48" width="74" height="28" rx="3" fill="#aaa"/><text x="623" y="66" text-anchor="middle" class="t3">FCS</text>
  <text x="24" y="104" class="k3">TRAMA ETIQUETADA — se insertan 4 BYTES tras la MAC de origen</text>
  <rect x="20" y="110" width="100" height="28" rx="3" fill="#888"/><text x="70" y="128" text-anchor="middle" class="t3">MAC destino</text>
  <rect x="124" y="110" width="100" height="28" rx="3" fill="#888"/><text x="174" y="128" text-anchor="middle" class="t3">MAC origen</text>
  <rect x="228" y="110" width="256" height="28" rx="3" fill="#0055a0" stroke="#e89822" stroke-width="2"/><text x="356" y="128" text-anchor="middle" class="t3">ETIQUETA 802.1Q — 4 bytes</text>
  <rect x="488" y="110" width="70" height="28" rx="3" fill="#aaa"/><text x="523" y="128" text-anchor="middle" class="t3">EtherType</text>
  <rect x="562" y="110" width="98" height="28" rx="3" fill="#ccc"/><text x="611" y="128" text-anchor="middle" style="font:700 10px system-ui;fill:#333">Datos + FCS</text>
  <line x1="228" y1="140" x2="140" y2="164" stroke="#e89822" stroke-width="1.5"/><line x1="484" y1="140" x2="660" y2="164" stroke="#e89822" stroke-width="1.5"/>
  <rect x="136" y="166" width="140" height="52" rx="4" fill="#0055a0"/><text x="206" y="184" text-anchor="middle" class="t3">TPID</text><text x="206" y="198" text-anchor="middle" class="s3">16 bits</text><text x="206" y="212" text-anchor="middle" class="s3">valor fijo 0x8100</text>
  <rect x="280" y="166" width="110" height="52" rx="4" fill="#2d8659"/><text x="335" y="184" text-anchor="middle" class="t3">PCP</text><text x="335" y="198" text-anchor="middle" class="s3">3 bits</text><text x="335" y="212" text-anchor="middle" class="s3">prioridad 0-7</text>
  <rect x="394" y="166" width="80" height="52" rx="4" fill="#e89822"/><text x="434" y="184" text-anchor="middle" class="t3">DEI</text><text x="434" y="198" text-anchor="middle" class="s3">1 bit</text><text x="434" y="212" text-anchor="middle" class="s3">descartable</text>
  <rect x="478" y="166" width="182" height="52" rx="4" fill="#d13c3c"/><text x="569" y="184" text-anchor="middle" class="t3">VID</text><text x="569" y="198" text-anchor="middle" class="s3">12 bits</text><text x="569" y="212" text-anchor="middle" class="s3">identificador de VLAN</text>
  <rect x="20" y="232" width="316" height="42" rx="4" fill="#eef3f8"/>
  <text x="178" y="249" text-anchor="middle" class="b3">12 bits = 4096 valores</text><text x="178" y="265" text-anchor="middle" class="d3">0 y 4095 reservados → 1-4094 utilizables</text>
  <rect x="344" y="232" width="316" height="42" rx="4" fill="#fbeaea"/>
  <text x="502" y="249" text-anchor="middle" class="b3">La VLAN 1 es la predeterminada</text><text x="502" y="265" text-anchor="middle" class="d3">No usarla ni para datos, ni gestión, ni nativa</text>
  <rect x="90" y="282" width="500" height="22" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="297" text-anchor="middle" class="k3">La trama etiquetada mide 4 bytes más: los troncales deben admitirlo</text>
  <text x="670" y="316" text-anchor="end" class="n3">[Fuente: IEEE8021Q]</text>
</svg>
```

---

## D4 · Puerto de acceso frente a puerto troncal

**Sección**: §1.1.2 — Redes de área local virtuales (VLAN) y enlace de troncales
**Propósito**: Distinguir los dos modos de puerto, situar la VLAN nativa y mostrar el caso especial del teléfono IP con ordenador conectado detrás.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Esquema de red que compara el puerto de acceso, que pertenece a una sola red local virtual y entrega tramas sin etiqueta al equipo final, con el puerto troncal, que transporta varias redes virtuales etiquetadas más una VLAN nativa sin etiquetar entre conmutadores; se muestra también el caso del teléfono con ordenador conectado detrás y la necesidad de encaminar para comunicar dos VLAN">
  <style>.t4{font:700 10px system-ui,sans-serif;fill:#fff}.s4{font:8.5px system-ui,sans-serif;fill:#fff}.d4{font:9px system-ui,sans-serif;fill:#333}.h4{font:700 13px system-ui,sans-serif;fill:#0055a0}.k4{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n4{font:8.5px system-ui,sans-serif;fill:#666}.l4{font:8.5px system-ui,sans-serif;fill:#0055a0}</style>
  <defs><marker id="a4" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h4">Puerto de acceso y puerto troncal</text>
  <rect x="20" y="36" width="96" height="34" rx="4" fill="#2d8659"/><text x="68" y="52" text-anchor="middle" class="t4">PC oficina</text><text x="68" y="64" text-anchor="middle" class="s4">VLAN 10</text>
  <rect x="20" y="82" width="96" height="34" rx="4" fill="#e89822"/><text x="68" y="98" text-anchor="middle" class="t4">Impresora</text><text x="68" y="110" text-anchor="middle" class="s4">VLAN 30</text>
  <rect x="20" y="128" width="96" height="48" rx="4" fill="#0055a0"/><text x="68" y="144" text-anchor="middle" class="t4">Teléfono IP</text><text x="68" y="156" text-anchor="middle" class="s4">voz: VLAN 20</text><text x="68" y="168" text-anchor="middle" class="s4">+ PC: VLAN 10</text>
  <line x1="118" y1="53" x2="182" y2="70" stroke="#0055a0" stroke-width="1.5" marker-end="url(#a4)"/>
  <line x1="118" y1="99" x2="182" y2="90" stroke="#0055a0" stroke-width="1.5" marker-end="url(#a4)"/>
  <line x1="118" y1="150" x2="182" y2="112" stroke="#0055a0" stroke-width="1.5" marker-end="url(#a4)"/>
  <text x="122" y="46" class="l4">sin etiqueta</text>
  <rect x="186" y="60" width="130" height="76" rx="5" fill="#0055a0"/><text x="251" y="82" text-anchor="middle" class="t4">CONMUTADOR</text><text x="251" y="96" text-anchor="middle" class="s4">de acceso</text><text x="251" y="114" text-anchor="middle" class="s4">puertos de ACCESO</text><text x="251" y="128" text-anchor="middle" class="s4">1 VLAN cada uno</text>
  <line x1="318" y1="98" x2="392" y2="98" stroke="#d13c3c" stroke-width="3" marker-end="url(#a4)"/>
  <text x="355" y="88" text-anchor="middle" style="font:700 9px system-ui;fill:#d13c3c">TRONCAL</text>
  <text x="355" y="114" text-anchor="middle" class="l4">VLAN 10, 20, 30</text><text x="355" y="126" text-anchor="middle" class="l4">etiquetadas</text>
  <rect x="396" y="60" width="130" height="76" rx="5" fill="#2d8659"/><text x="461" y="82" text-anchor="middle" class="t4">CONMUTADOR</text><text x="461" y="96" text-anchor="middle" class="s4">de distribución</text><text x="461" y="114" text-anchor="middle" class="s4">SVI por VLAN</text><text x="461" y="128" text-anchor="middle" class="s4">= nivel 3</text>
  <line x1="528" y1="98" x2="586" y2="98" stroke="#0055a0" stroke-width="1.5" marker-end="url(#a4)"/>
  <rect x="590" y="74" width="70" height="48" rx="4" fill="#888"/><text x="625" y="94" text-anchor="middle" class="t4">Núcleo</text><text x="625" y="110" text-anchor="middle" class="s4">y CPD</text>
  <rect x="20" y="192" width="316" height="66" rx="4" fill="#eef3f8"/>
  <text x="178" y="209" text-anchor="middle" class="k4">PUERTO DE ACCESO</text>
  <text x="178" y="225" text-anchor="middle" class="d4">Una sola VLAN · tramas SIN etiqueta</text>
  <text x="178" y="239" text-anchor="middle" class="d4">El equipo final ignora que existen VLAN</text>
  <text x="178" y="253" text-anchor="middle" class="d4">Excepción: teléfono IP + PC (voz etiquetada)</text>
  <rect x="344" y="192" width="316" height="66" rx="4" fill="#e8f4ee"/>
  <text x="502" y="209" text-anchor="middle" class="k4">PUERTO TRONCAL</text>
  <text x="502" y="225" text-anchor="middle" class="d4">Varias VLAN · tramas ETIQUETADAS</text>
  <text x="502" y="239" text-anchor="middle" class="d4">Salvo la VLAN NATIVA, que va sin etiqueta</text>
  <text x="502" y="253" text-anchor="middle" class="d4">Entre conmutadores, a hipervisores y a puntos de acceso</text>
  <rect x="20" y="266" width="640" height="26" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="283" text-anchor="middle" class="d4">Riesgo: VLAN nativas distintas en cada extremo, y salto de VLAN por doble etiquetado</text>
  <rect x="90" y="300" width="500" height="22" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="315" text-anchor="middle" class="k4">Buena práctica: VLAN nativa sin uso y sin salida; nunca la VLAN 1</text>
  <text x="670" y="336" text-anchor="end" class="n4">[Fuente: IEEE8021Q; IEEE8021AB]</text>
</svg>
```

---

## D5 · Redundancia sin bucles: STP, RSTP, MSTP y agregación

**Sección**: §1.1.3 — Protocolos de conmutación y redundancia en el nivel de enlace
**Propósito**: Ordenar las tres generaciones del árbol de expansión con su norma y su tiempo de convergencia, y contrastarlas con la agregación de enlaces, que resuelve el mismo problema sin bloquear.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 362" role="img" aria-label="Comparativa de los mecanismos de redundancia en el nivel de enlace: protocolo de árbol de expansión 802.1D, su versión rápida 802.1w incorporada en 2004, el árbol de expansión múltiple 802.1s integrado en 802.1Q, y la agregación de enlaces 802.1AX con el protocolo LACP, indicando norma, convergencia y comportamiento de los enlaces redundantes">
  <style>.t5{font:700 11px system-ui,sans-serif;fill:#fff}.s5{font:8.5px system-ui,sans-serif;fill:#fff}.d5{font:9px system-ui,sans-serif;fill:#333}.h5{font:700 13px system-ui,sans-serif;fill:#0055a0}.k5{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n5{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h5">Enlaces redundantes sin bucles: cuatro respuestas</text>
  <rect x="20" y="34" width="155" height="36" rx="5" fill="#888"/><text x="97" y="50" text-anchor="middle" class="t5">STP</text><text x="97" y="63" text-anchor="middle" class="s5">IEEE 802.1D</text>
  <rect x="182" y="34" width="155" height="36" rx="5" fill="#0055a0"/><text x="259" y="50" text-anchor="middle" class="t5">RSTP</text><text x="259" y="63" text-anchor="middle" class="s5">802.1w → en 802.1D-2004</text>
  <rect x="344" y="34" width="155" height="36" rx="5" fill="#e89822"/><text x="421" y="50" text-anchor="middle" class="t5">MSTP</text><text x="421" y="63" text-anchor="middle" class="s5">802.1s → en 802.1Q</text>
  <rect x="506" y="34" width="154" height="36" rx="5" fill="#2d8659"/><text x="583" y="50" text-anchor="middle" class="t5">AGREGACIÓN</text><text x="583" y="63" text-anchor="middle" class="s5">802.1AX (antes 802.3ad)</text>
  <text x="24" y="88" class="k5">CONVERGENCIA TRAS UN FALLO</text>
  <rect x="20" y="94" width="155" height="30" rx="4" fill="#fbeaea"/><text x="97" y="113" text-anchor="middle" class="d5">30-50 segundos</text>
  <rect x="182" y="94" width="155" height="30" rx="4" fill="#eef3f8"/><text x="259" y="113" text-anchor="middle" class="d5">Pocos segundos</text>
  <rect x="344" y="94" width="155" height="30" rx="4" fill="#eef3f8"/><text x="421" y="113" text-anchor="middle" class="d5">Como RSTP, por instancia</text>
  <rect x="506" y="94" width="154" height="30" rx="4" fill="#e8f4ee"/><text x="583" y="113" text-anchor="middle" class="d5">Inmediata (subsegundo)</text>
  <text x="24" y="142" class="k5">¿QUÉ HACE CON EL ENLACE REDUNDANTE?</text>
  <rect x="20" y="148" width="317" height="44" rx="4" fill="#f5f5f5"/>
  <text x="178" y="166" text-anchor="middle" class="d5">Lo BLOQUEA: existe, pero no transporta nada.</text><text x="178" y="182" text-anchor="middle" class="d5">La capacidad instalada se desperdicia</text>
  <rect x="344" y="148" width="155" height="44" rx="4" fill="#fdf3e3"/>
  <text x="421" y="166" text-anchor="middle" class="d5">Bloquea, pero reparte</text><text x="421" y="182" text-anchor="middle" class="d5">VLAN entre instancias</text>
  <rect x="506" y="148" width="154" height="44" rx="4" fill="#e8f4ee"/>
  <text x="583" y="166" text-anchor="middle" class="d5">Lo USA: los enlaces son</text><text x="583" y="182" text-anchor="middle" class="d5">uno solo; STP no bloquea</text>
  <text x="24" y="210" class="k5">CÓMO SE ELIGE EL PUENTE RAÍZ (STP / RSTP / MSTP)</text>
  <rect x="20" y="216" width="480" height="30" rx="4" fill="#eef3f8"/>
  <text x="260" y="235" text-anchor="middle" class="d5">Menor IDENTIFICADOR DE PUENTE = prioridad configurable + MAC → fíjalo por configuración</text>
  <rect x="506" y="216" width="154" height="30" rx="4" fill="#e8f4ee"/><text x="583" y="235" text-anchor="middle" class="d5">LACP negocia el grupo</text>
  <rect x="20" y="256" width="640" height="26" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="273" text-anchor="middle" class="d5">La agregación reparte POR FLUJO: 4×1 Gbit/s = 4 Gbit/s agregados, pero 1 Gbit/s por conversación</text>
  <rect x="20" y="290" width="640" height="26" rx="4" fill="#e8f4ee" stroke="#2d8659" stroke-width="1.2"/>
  <text x="340" y="307" text-anchor="middle" class="d5">En el puerto de acceso: PUERTO DE BORDE + GUARDA DE BPDU (+ guarda de raíz y control de tormentas)</text>
  <rect x="90" y="324" width="500" height="20" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="338" text-anchor="middle" class="k5">Puerta de enlace redundante: VRRP (estándar) · HSRP y GLBP (propietarios)</text>
  <text x="670" y="358" text-anchor="end" class="n5">[Fuente: IEEE8021D; IEEE8021Q; IEEE8021AX]</text>
</svg>
```

---

## D6 · DHCP: el ciclo DORA y el agente de retransmisión

**Sección**: §1.2.1 — Configuración y gestión dinámica de direccionamiento (DHCP)
**Propósito**: Fijar los cuatro mensajes, sus puertos y quién difunde, y explicar por qué un servidor central puede atender muchas VLAN gracias al agente de retransmisión.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Flujo del protocolo DHCP: el cliente envía Discover en difusión, el servidor responde con Offer, el cliente envía Request también en difusión y el servidor confirma con Ack, usando los puertos UDP 68 en el cliente y 67 en el servidor; se muestra el agente de retransmisión que convierte la difusión en unidifusión hacia un servidor central y la opción 82 que añade el conmutador y el puerto de origen">
  <style>.t6{font:700 10px system-ui,sans-serif;fill:#fff}.s6{font:8.5px system-ui,sans-serif;fill:#fff}.d6{font:9px system-ui,sans-serif;fill:#333}.h6{font:700 13px system-ui,sans-serif;fill:#0055a0}.k6{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n6{font:8.5px system-ui,sans-serif;fill:#666}.m6{font:700 9px system-ui,sans-serif;fill:#0055a0}</style>
  <defs><marker id="a6" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker>
  <marker id="b6" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#2d8659"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h6">DHCP: ciclo DORA, retransmisión y opción 82</text>
  <rect x="20" y="36" width="110" height="34" rx="4" fill="#0055a0"/><text x="75" y="52" text-anchor="middle" class="t6">CLIENTE</text><text x="75" y="64" text-anchor="middle" class="s6">UDP 68</text>
  <rect x="550" y="36" width="110" height="34" rx="4" fill="#2d8659"/><text x="605" y="52" text-anchor="middle" class="t6">SERVIDOR</text><text x="605" y="64" text-anchor="middle" class="s6">UDP 67</text>
  <line x1="75" y1="76" x2="75" y2="234" stroke="#999" stroke-width="1" stroke-dasharray="3,3"/>
  <line x1="605" y1="76" x2="605" y2="234" stroke="#999" stroke-width="1" stroke-dasharray="3,3"/>
  <line x1="80" y1="96" x2="598" y2="96" stroke="#0055a0" stroke-width="2" marker-end="url(#a6)"/>
  <text x="340" y="90" text-anchor="middle" class="m6">1 · DISCOVER — DIFUSIÓN («¿hay algún servidor?»)</text>
  <line x1="598" y1="130" x2="82" y2="130" stroke="#2d8659" stroke-width="2" marker-end="url(#b6)"/>
  <text x="340" y="124" text-anchor="middle" style="font:700 9px system-ui;fill:#2d8659">2 · OFFER — te ofrezco esta dirección</text>
  <line x1="80" y1="164" x2="598" y2="164" stroke="#0055a0" stroke-width="2" marker-end="url(#a6)"/>
  <text x="340" y="158" text-anchor="middle" class="m6">3 · REQUEST — DIFUSIÓN (acepto esa; los demás, liberad la vuestra)</text>
  <line x1="598" y1="198" x2="82" y2="198" stroke="#2d8659" stroke-width="2" marker-end="url(#b6)"/>
  <text x="340" y="192" text-anchor="middle" style="font:700 9px system-ui;fill:#2d8659">4 · ACK — confirmada, con tiempo de concesión</text>
  <rect x="140" y="210" width="400" height="26" rx="4" fill="#fdf3e3"/>
  <text x="340" y="227" text-anchor="middle" class="d6">Entrega además: máscara · puerta de enlace (3) · DNS (6) · dominio (15) · NTP (42)</text>
  <rect x="20" y="248" width="316" height="60" rx="4" fill="#eef3f8"/>
  <text x="178" y="265" text-anchor="middle" class="k6">RENOVACIÓN DE LA CONCESIÓN</text>
  <text x="178" y="281" text-anchor="middle" class="d6">T1 al 50 % → unidifusión al mismo servidor</text>
  <text x="178" y="295" text-anchor="middle" class="d6">T2 al 87,5 % → difusión a cualquiera</text>
  <rect x="344" y="248" width="316" height="60" rx="4" fill="#e8f4ee"/>
  <text x="502" y="265" text-anchor="middle" class="k6">AGENTE DE RETRANSMISIÓN (relay)</text>
  <text x="502" y="281" text-anchor="middle" class="d6">Convierte la DIFUSIÓN en UNIDIFUSIÓN</text>
  <text x="502" y="295" text-anchor="middle" class="d6">→ un servidor central para muchas VLAN</text>
  <rect x="20" y="316" width="640" height="24" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="332" text-anchor="middle" class="d6">Opción 82: añade conmutador y PUERTO de origen · Inspección DHCP: bloquea servidores no autorizados</text>
  <text x="670" y="355" text-anchor="end" class="n6">[Fuente: RFC2131; RFC3046]</text>
</svg>
```

---

## D7 · DNS: jerarquía, resolución y tipos de registro

**Sección**: §1.2.2 — Servicio de resolución de nombres de dominio (DNS)
**Propósito**: Mostrar a la vez la jerarquía del espacio de nombres, la diferencia entre consulta recursiva e iterativa y la tabla de registros que hay que reconocer.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Funcionamiento del sistema de nombres de dominio: el cliente formula una consulta recursiva a su resolutor y este realiza consultas iterativas a la raíz, al dominio de primer nivel y al servidor autoritativo, guardando la respuesta en memoria caché durante el tiempo de vida indicado; se acompaña de la tabla de tipos de registro A, AAAA, PTR, CNAME, MX, NS, SOA, SRV y TXT">
  <style>.t7{font:700 10px system-ui,sans-serif;fill:#fff}.s7{font:8.5px system-ui,sans-serif;fill:#fff}.d7{font:9px system-ui,sans-serif;fill:#333}.h7{font:700 13px system-ui,sans-serif;fill:#0055a0}.k7{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n7{font:8.5px system-ui,sans-serif;fill:#666}.c7{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <defs><marker id="a7" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h7">DNS: quién pregunta a quién, y qué se pregunta</text>
  <rect x="20" y="36" width="104" height="40" rx="4" fill="#0055a0"/><text x="72" y="54" text-anchor="middle" class="t7">CLIENTE</text><text x="72" y="68" text-anchor="middle" class="s7">equipo del usuario</text>
  <line x1="126" y1="56" x2="184" y2="56" stroke="#0055a0" stroke-width="2" marker-end="url(#a7)"/>
  <text x="155" y="48" text-anchor="middle" class="c7">RECURSIVA</text>
  <rect x="188" y="36" width="116" height="40" rx="4" fill="#2d8659"/><text x="246" y="54" text-anchor="middle" class="t7">RESOLUTOR</text><text x="246" y="68" text-anchor="middle" class="s7">recursivo + caché</text>
  <line x1="306" y1="48" x2="392" y2="48" stroke="#0055a0" stroke-width="1.5" marker-end="url(#a7)"/>
  <text x="349" y="40" text-anchor="middle" class="c7">ITERATIVAS</text>
  <rect x="396" y="34" width="80" height="26" rx="4" fill="#888"/><text x="436" y="51" text-anchor="middle" class="t7">RAÍZ « . »</text>
  <rect x="486" y="34" width="80" height="26" rx="4" fill="#888"/><text x="526" y="51" text-anchor="middle" class="t7">TLD « .es »</text>
  <rect x="576" y="34" width="84" height="26" rx="4" fill="#e89822"/><text x="618" y="51" text-anchor="middle" class="t7">AUTORITATIVO</text>
  <line x1="478" y1="47" x2="484" y2="47" stroke="#0055a0" stroke-width="1.5"/><line x1="568" y1="47" x2="574" y2="47" stroke="#0055a0" stroke-width="1.5"/>
  <text x="528" y="74" text-anchor="middle" class="d7">cada uno responde «pregunta a este otro»</text>
  <rect x="188" y="86" width="116" height="24" rx="4" fill="#fdf3e3"/><text x="246" y="102" text-anchor="middle" class="d7">Guarda en caché el TTL</text>
  <text x="24" y="132" class="k7">TIPOS DE REGISTRO QUE HAY QUE RECONOCER</text>
  <rect x="20" y="138" width="156" height="30" rx="4" fill="#0055a0"/><text x="98" y="151" text-anchor="middle" class="t7">A / AAAA</text><text x="98" y="164" text-anchor="middle" class="s7">nombre → IPv4 / IPv6</text>
  <rect x="182" y="138" width="156" height="30" rx="4" fill="#2d8659"/><text x="260" y="151" text-anchor="middle" class="t7">PTR</text><text x="260" y="164" text-anchor="middle" class="s7">IP → nombre (in-addr.arpa)</text>
  <rect x="344" y="138" width="156" height="30" rx="4" fill="#888"/><text x="422" y="151" text-anchor="middle" class="t7">CNAME</text><text x="422" y="164" text-anchor="middle" class="s7">alias de otro nombre</text>
  <rect x="506" y="138" width="154" height="30" rx="4" fill="#888"/><text x="583" y="151" text-anchor="middle" class="t7">MX</text><text x="583" y="164" text-anchor="middle" class="s7">servidor de correo</text>
  <rect x="20" y="174" width="156" height="30" rx="4" fill="#888"/><text x="98" y="187" text-anchor="middle" class="t7">NS</text><text x="98" y="200" text-anchor="middle" class="s7">servidores de la zona</text>
  <rect x="182" y="174" width="156" height="30" rx="4" fill="#888"/><text x="260" y="187" text-anchor="middle" class="t7">SOA</text><text x="260" y="200" text-anchor="middle" class="s7">inicio de autoridad</text>
  <rect x="344" y="174" width="156" height="30" rx="4" fill="#d13c3c"/><text x="422" y="187" text-anchor="middle" class="t7">SRV</text><text x="422" y="200" text-anchor="middle" class="s7">localiza un SERVICIO</text>
  <rect x="506" y="174" width="154" height="30" rx="4" fill="#888"/><text x="583" y="187" text-anchor="middle" class="t7">TXT</text><text x="583" y="200" text-anchor="middle" class="s7">texto libre</text>
  <rect x="20" y="212" width="640" height="26" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="229" text-anchor="middle" class="d7">Los registros SRV localizan los CONTROLADORES DE DOMINIO: sin ellos, «no puedo iniciar sesión pero navego bien»</text>
  <rect x="20" y="248" width="316" height="56" rx="4" fill="#eef3f8"/>
  <text x="178" y="265" text-anchor="middle" class="k7">DNSSEC (RFC 4033-4035)</text>
  <text x="178" y="281" text-anchor="middle" class="d7">Firma las zonas: AUTENTICIDAD e INTEGRIDAD</text>
  <text x="178" y="295" text-anchor="middle" class="d7">NO aporta confidencialidad</text>
  <rect x="344" y="248" width="316" height="56" rx="4" fill="#e8f4ee"/>
  <text x="502" y="265" text-anchor="middle" class="k7">DoT (853) y DoH (443)</text>
  <text x="502" y="281" text-anchor="middle" class="d7">Cifran el canal: CONFIDENCIALIDAD</text>
  <text x="502" y="295" text-anchor="middle" class="d7">Riesgo: el navegador elude el resolutor corporativo</text>
  <rect x="90" y="312" width="500" height="24" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="328" text-anchor="middle" class="k7">DNS = puerto 53 · UDP para consultas · TCP para respuestas grandes y transferencias de zona</text>
  <text x="670" y="356" text-anchor="end" class="n7">[Fuente: RFC1034; RFC4033; RFC7858; MS-DNS]</text>
</svg>
```

---

## D8 · Directorio: estructura lógica frente a estructura física

**Sección**: §2.1.1 — Estructura lógica y física de servicios de directorio
**Propósito**: Separar las dos estructuras superpuestas del directorio y fijar qué delimita cada pieza.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Comparación entre la estructura lógica de un servicio de directorio, formada por bosque, árbol, dominio y unidad organizativa, y su estructura física, formada por controladores de dominio, sitios y enlaces de sitio; se indica qué delimita cada pieza: el bosque es el límite de seguridad y de esquema, el dominio el de replicación y política de cuentas, y la unidad organizativa no es un límite de seguridad">
  <style>.t8{font:700 10.5px system-ui,sans-serif;fill:#fff}.s8{font:8.5px system-ui,sans-serif;fill:#fff}.d8{font:9px system-ui,sans-serif;fill:#333}.h8{font:700 13px system-ui,sans-serif;fill:#0055a0}.k8{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n8{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h8">Dos estructuras superpuestas e independientes</text>
  <rect x="20" y="32" width="316" height="28" rx="5" fill="#0055a0"/><text x="178" y="51" text-anchor="middle" class="t8">ESTRUCTURA LÓGICA — organiza la información</text>
  <rect x="344" y="32" width="316" height="28" rx="5" fill="#2d8659"/><text x="502" y="51" text-anchor="middle" class="t8">ESTRUCTURA FÍSICA — organiza las copias</text>
  <rect x="26" y="70" width="304" height="146" rx="5" fill="#eef3f8" stroke="#0055a0" stroke-width="1.5"/>
  <text x="178" y="87" text-anchor="middle" class="k8">BOSQUE — límite de SEGURIDAD y de ESQUEMA</text>
  <rect x="38" y="94" width="280" height="112" rx="4" fill="#dce8f2"/>
  <text x="178" y="110" text-anchor="middle" class="k8">ÁRBOL — nombre DNS contiguo</text>
  <rect x="50" y="118" width="256" height="80" rx="4" fill="#c7dcee"/>
  <text x="178" y="134" text-anchor="middle" class="k8">DOMINIO — límite de REPLICACIÓN y de CUENTAS</text>
  <rect x="62" y="142" width="232" height="48" rx="4" fill="#0055a0"/>
  <text x="178" y="160" text-anchor="middle" class="t8">UNIDAD ORGANIZATIVA</text>
  <text x="178" y="175" text-anchor="middle" class="s8">delegación de administración + aplicación de GPO</text>
  <text x="178" y="187" text-anchor="middle" class="s8">NO es un límite de seguridad</text>
  <rect x="350" y="70" width="304" height="146" rx="5" fill="#e8f4ee" stroke="#2d8659" stroke-width="1.5"/>
  <text x="502" y="88" text-anchor="middle" class="k8">SITIO — subredes IP bien conectadas</text>
  <rect x="362" y="96" width="138" height="50" rx="4" fill="#2d8659"/><text x="431" y="114" text-anchor="middle" class="t8">Sitio «Sede A»</text><text x="431" y="128" text-anchor="middle" class="s8">2 controladores</text><text x="431" y="140" text-anchor="middle" class="s8">replicación inmediata</text>
  <rect x="506" y="96" width="138" height="50" rx="4" fill="#2d8659"/><text x="575" y="114" text-anchor="middle" class="t8">Sitio «Sede B»</text><text x="575" y="128" text-anchor="middle" class="s8">1 controlador</text><text x="575" y="140" text-anchor="middle" class="s8">solo lectura</text>
  <line x1="500" y1="121" x2="506" y2="121" stroke="#0055a0" stroke-width="2"/>
  <rect x="362" y="152" width="282" height="24" rx="4" fill="#c9e5d7"/><text x="503" y="168" text-anchor="middle" class="d8">ENLACE DE SITIO: replicación programada y comprimida</text>
  <rect x="362" y="180" width="282" height="26" rx="4" fill="#fdf3e3"/><text x="503" y="197" text-anchor="middle" class="d8">Determina a QUÉ CONTROLADOR se autentica cada equipo</text>
  <rect x="20" y="226" width="640" height="26" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="243" text-anchor="middle" class="d8">Un dominio puede abarcar muchos sitios, y un sitio puede alojar controladores de varios dominios: son independientes</text>
  <text x="24" y="270" class="k8">LOS CUATRO PILARES DE UN DOMINIO DE DIRECTORIO</text>
  <rect x="20" y="276" width="156" height="34" rx="4" fill="#0055a0"/><text x="98" y="290" text-anchor="middle" class="t8">LDAP</text><text x="98" y="303" text-anchor="middle" class="s8">consulta · 389 / 636</text>
  <rect x="182" y="276" width="156" height="34" rx="4" fill="#2d8659"/><text x="260" y="290" text-anchor="middle" class="t8">KERBEROS</text><text x="260" y="303" text-anchor="middle" class="s8">autenticación · 88</text>
  <rect x="344" y="276" width="156" height="34" rx="4" fill="#d13c3c"/><text x="422" y="290" text-anchor="middle" class="t8">DNS</text><text x="422" y="303" text-anchor="middle" class="s8">localización · SRV</text>
  <rect x="506" y="276" width="154" height="34" rx="4" fill="#e89822"/><text x="583" y="290" text-anchor="middle" class="t8">GPO</text><text x="583" y="303" text-anchor="middle" class="s8">directivas</text>
  <rect x="90" y="318" width="500" height="22" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="333" text-anchor="middle" class="k8">Si falla el DNS, falla el inicio de sesión aunque el directorio esté sano</text>
  <text x="670" y="356" text-anchor="end" class="n8">[Fuente: MS-AD; RFC4511; RFC4120]</text>
</svg>
```

---

## D9 · AGDLP y el orden de aplicación de directivas L-S-D-UO

**Sección**: §2.1.3 y §2.2.2 — Objetos y grupos · Directivas de grupo
**Propósito**: Reunir en un solo diagrama las dos reglas clave de la gestión de usuarios: cómo se encadenan los grupos para conceder permisos y en qué orden ganan las directivas.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Doble esquema: en la parte superior, el anidamiento AGDLP en el que las cuentas se meten en grupos globales, estos en grupos locales de dominio y a estos se les conceden los permisos sobre el recurso; en la parte inferior, el orden de aplicación de las directivas de grupo local, sitio, dominio y unidad organizativa, en el que gana la última aplicada salvo que una superior esté marcada como forzada">
  <style>.t9{font:700 10px system-ui,sans-serif;fill:#fff}.s9{font:8.5px system-ui,sans-serif;fill:#fff}.d9{font:9px system-ui,sans-serif;fill:#333}.h9{font:700 13px system-ui,sans-serif;fill:#0055a0}.k9{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n9{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <defs><marker id="a9" markerWidth="9" markerHeight="9" refX="8" refY="3.5" orient="auto"><path d="M0,0 L8,3.5 L0,7 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h9">Las dos reglas clave de la gestión de usuarios</text>
  <text x="24" y="42" class="k9">1 · ANIDAMIENTO DE GRUPOS — AGDLP</text>
  <rect x="20" y="48" width="140" height="42" rx="4" fill="#0055a0"/><text x="90" y="64" text-anchor="middle" class="t9">A · CUENTA</text><text x="90" y="78" text-anchor="middle" class="s9">Ana Torres</text>
  <line x1="164" y1="69" x2="192" y2="69" stroke="#0055a0" stroke-width="2" marker-end="url(#a9)"/>
  <rect x="196" y="48" width="150" height="42" rx="4" fill="#2d8659"/><text x="271" y="64" text-anchor="middle" class="t9">G · GRUPO GLOBAL</text><text x="271" y="78" text-anchor="middle" class="s9">«quién es»: Tramitación-Centro</text>
  <line x1="350" y1="69" x2="378" y2="69" stroke="#0055a0" stroke-width="2" marker-end="url(#a9)"/>
  <rect x="382" y="48" width="150" height="42" rx="4" fill="#e89822"/><text x="457" y="64" text-anchor="middle" class="t9">DL · GRUPO LOCAL</text><text x="457" y="78" text-anchor="middle" class="s9">«a qué da derecho»</text>
  <line x1="536" y1="69" x2="558" y2="69" stroke="#0055a0" stroke-width="2" marker-end="url(#a9)"/>
  <rect x="562" y="48" width="98" height="42" rx="4" fill="#d13c3c"/><text x="611" y="64" text-anchor="middle" class="t9">P · PERMISO</text><text x="611" y="78" text-anchor="middle" class="s9">sobre el recurso</text>
  <rect x="20" y="98" width="640" height="24" rx="4" fill="#e8f4ee" stroke="#2d8659" stroke-width="1.2"/>
  <text x="340" y="114" text-anchor="middle" class="d9">Un traslado de servicio = quitar de un grupo global y añadir a otro. Los permisos NUNCA se dan a la cuenta</text>
  <text x="24" y="146" class="k9">2 · ORDEN DE APLICACIÓN DE LAS DIRECTIVAS DE GRUPO</text>
  <rect x="20" y="152" width="150" height="40" rx="4" fill="#888"/><text x="95" y="168" text-anchor="middle" class="t9">L · LOCAL</text><text x="95" y="182" text-anchor="middle" class="s9">del propio equipo</text>
  <line x1="174" y1="172" x2="196" y2="172" stroke="#0055a0" stroke-width="2" marker-end="url(#a9)"/>
  <rect x="200" y="152" width="150" height="40" rx="4" fill="#0055a0"/><text x="275" y="168" text-anchor="middle" class="t9">S · SITIO</text><text x="275" y="182" text-anchor="middle" class="s9">estructura física</text>
  <line x1="354" y1="172" x2="376" y2="172" stroke="#0055a0" stroke-width="2" marker-end="url(#a9)"/>
  <rect x="380" y="152" width="130" height="40" rx="4" fill="#2d8659"/><text x="445" y="168" text-anchor="middle" class="t9">D · DOMINIO</text><text x="445" y="182" text-anchor="middle" class="s9">toda la organización</text>
  <line x1="514" y1="172" x2="536" y2="172" stroke="#0055a0" stroke-width="2" marker-end="url(#a9)"/>
  <rect x="540" y="152" width="120" height="40" rx="4" fill="#d13c3c"/><text x="600" y="168" text-anchor="middle" class="t9">UO</text><text x="600" y="182" text-anchor="middle" class="s9">de fuera a dentro</text>
  <rect x="20" y="200" width="640" height="24" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="216" text-anchor="middle" class="d9">GANA LA ÚLTIMA EN APLICARSE = la más próxima al objeto. Es decir, normalmente la de la unidad organizativa</text>
  <text x="24" y="246" class="k9">EXCEPCIONES Y MODULADORES</text>
  <rect x="20" y="252" width="156" height="46" rx="4" fill="#eef3f8"/><text x="98" y="268" text-anchor="middle" class="k9">FORZADA (enforced)</text><text x="98" y="282" text-anchor="middle" class="d9">Prevalece sobre las</text><text x="98" y="294" text-anchor="middle" class="d9">posteriores Y sobre el bloqueo</text>
  <rect x="182" y="252" width="156" height="46" rx="4" fill="#eef3f8"/><text x="260" y="268" text-anchor="middle" class="k9">BLOQUEO DE HERENCIA</text><text x="260" y="282" text-anchor="middle" class="d9">Corta lo que viene de arriba</text><text x="260" y="294" text-anchor="middle" class="d9">salvo lo forzado</text>
  <rect x="344" y="252" width="156" height="46" rx="4" fill="#eef3f8"/><text x="422" y="268" text-anchor="middle" class="k9">FILTRADO</text><text x="422" y="282" text-anchor="middle" class="d9">Por seguridad (grupo)</text><text x="422" y="294" text-anchor="middle" class="d9">o por consulta WMI</text>
  <rect x="506" y="252" width="154" height="46" rx="4" fill="#fdf3e3"/><text x="583" y="268" text-anchor="middle" class="k9">DIRECTIVA / PREFERENCIA</text><text x="583" y="282" text-anchor="middle" class="d9">La directiva impone y bloquea</text><text x="583" y="294" text-anchor="middle" class="d9">La preferencia solo inicializa</text>
  <rect x="90" y="306" width="500" height="22" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="321" text-anchor="middle" class="k9">Varias GPO en el mismo contenedor: gana la de orden de vínculo 1</text>
  <text x="670" y="337" text-anchor="end" class="n9">[Fuente: MS-AD; MS-GPO; NIST-RBAC]</text>
</svg>
```

---

## D10 · Control de admisión 802.1X: los tres papeles

**Sección**: §3.2.3 — Control de admisión a la red y autenticación de dispositivos
**Propósito**: Fijar el triángulo suplicante-autenticador-servidor, qué circula antes de autenticarse y qué destinos posibles tiene un dispositivo según el resultado.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 362" role="img" aria-label="Esquema del control de admisión a la red basado en el estándar 802.1X: el suplicante que es el equipo, el autenticador que es el conmutador o punto de acceso, y el servidor de autenticación RADIUS que consulta el directorio; antes de autenticarse por el puerto solo circula EAPOL, y según el resultado el dispositivo se coloca en la VLAN corporativa, en la de invitados, en cuarentena o queda rechazado">
  <style>.ta{font:700 10.5px system-ui,sans-serif;fill:#fff}.sa{font:8.5px system-ui,sans-serif;fill:#fff}.da{font:9px system-ui,sans-serif;fill:#333}.ha{font:700 13px system-ui,sans-serif;fill:#0055a0}.ka{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.na{font:8.5px system-ui,sans-serif;fill:#666}.ca{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <defs><marker id="a10" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="ha">802.1X: control de acceso a la red basado en puerto</text>
  <rect x="20" y="40" width="150" height="52" rx="5" fill="#0055a0"/><text x="95" y="58" text-anchor="middle" class="ta">SUPLICANTE</text><text x="95" y="73" text-anchor="middle" class="sa">el equipo que quiere entrar</text><text x="95" y="86" text-anchor="middle" class="sa">presenta certificado o credencial</text>
  <line x1="174" y1="66" x2="256" y2="66" stroke="#0055a0" stroke-width="2" marker-end="url(#a10)"/>
  <text x="215" y="58" text-anchor="middle" class="ca">EAPOL</text>
  <rect x="260" y="40" width="160" height="52" rx="5" fill="#2d8659"/><text x="340" y="58" text-anchor="middle" class="ta">AUTENTICADOR</text><text x="340" y="73" text-anchor="middle" class="sa">conmutador o punto de acceso</text><text x="340" y="86" text-anchor="middle" class="sa">mantiene el puerto cerrado</text>
  <line x1="424" y1="66" x2="506" y2="66" stroke="#0055a0" stroke-width="2" marker-end="url(#a10)"/>
  <text x="465" y="58" text-anchor="middle" class="ca">RADIUS</text>
  <rect x="510" y="40" width="150" height="52" rx="5" fill="#e89822"/><text x="585" y="58" text-anchor="middle" class="ta">SERVIDOR AAA</text><text x="585" y="73" text-anchor="middle" class="sa">RADIUS · UDP 1812/1813</text><text x="585" y="86" text-anchor="middle" class="sa">consulta el directorio</text>
  <rect x="20" y="102" width="640" height="26" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="119" text-anchor="middle" class="da">Antes de autenticarse, por el puerto SOLO circula EAPOL: ni DHCP, ni DNS, ni nada más</text>
  <text x="24" y="152" class="ka">EL SERVIDOR NO SOLO DICE SÍ O NO: DEVUELVE ATRIBUTOS QUE COLOCAN AL DISPOSITIVO</text>
  <rect x="20" y="158" width="156" height="56" rx="4" fill="#2d8659"/><text x="98" y="176" text-anchor="middle" class="ta">VLAN CORPORATIVA</text><text x="98" y="192" text-anchor="middle" class="sa">Autenticado y conforme</text><text x="98" y="205" text-anchor="middle" class="sa">EAP-TLS, PEAP, EAP-TTLS</text>
  <rect x="182" y="158" width="156" height="56" rx="4" fill="#e89822"/><text x="260" y="176" text-anchor="middle" class="ta">CUARENTENA</text><text x="260" y="192" text-anchor="middle" class="sa">Autenticado, NO conforme</text><text x="260" y="205" text-anchor="middle" class="sa">solo acceso a remediación</text>
  <rect x="344" y="158" width="156" height="56" rx="4" fill="#888"/><text x="422" y="176" text-anchor="middle" class="ta">VLAN DE INVITADOS</text><text x="422" y="192" text-anchor="middle" class="sa">No se autentica</text><text x="422" y="205" text-anchor="middle" class="sa">solo salida a internet</text>
  <rect x="506" y="158" width="154" height="56" rx="4" fill="#d13c3c"/><text x="583" y="176" text-anchor="middle" class="ta">RECHAZADO</text><text x="583" y="192" text-anchor="middle" class="sa">Puerto cerrado</text><text x="583" y="205" text-anchor="middle" class="sa">y evento registrado</text>
  <text x="24" y="238" class="ka">MECANISMOS DE RESPALDO Y REFUERZO</text>
  <rect x="20" y="244" width="212" height="44" rx="4" fill="#eef3f8"/><text x="126" y="260" text-anchor="middle" class="ka">MAB — autenticación por MAC</text><text x="126" y="275" text-anchor="middle" class="da">Para lo que no habla 802.1X.</text><text x="126" y="286" text-anchor="middle" class="da">Débil: una MAC se falsifica</text>
  <rect x="238" y="244" width="212" height="44" rx="4" fill="#eef3f8"/><text x="344" y="260" text-anchor="middle" class="ka">MODO DE SUPERVISIÓN</text><text x="344" y="275" text-anchor="middle" class="da">Evalúa y registra, pero NO aplica.</text><text x="344" y="286" text-anchor="middle" class="da">Fase obligada antes de cortar</text>
  <rect x="456" y="244" width="204" height="44" rx="4" fill="#e8f4ee"/><text x="558" y="260" text-anchor="middle" class="ka">RADIUS CoA — RFC 5176</text><text x="558" y="275" text-anchor="middle" class="da">Cambia o corta una sesión YA activa:</text><text x="558" y="286" text-anchor="middle" class="da">control continuo, no puntual</text>
  <rect x="20" y="296" width="640" height="24" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="312" text-anchor="middle" class="da">Riesgo operativo: si cae el servidor RADIUS, la sede se queda sin red. Redunda y define el comportamiento de contingencia</text>
  <rect x="90" y="326" width="500" height="20" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="340" text-anchor="middle" class="ka">Refuerzos de nivel 2: seguridad de puerto · inspección DHCP · inspección ARP dinámica</text>
  <text x="670" y="358" text-anchor="end" class="na">[Fuente: IEEE8021X; RFC2865; RFC3748]</text>
</svg>
```

---

## D11 · Mapa de protocolos y puertos de administración y monitorización

**Sección**: §3.1.3 y §4.1.1 — Protocolos de administración segura · Instrumentos de monitorización
**Propósito**: Reunir en una sola tabla visual todos los puertos y números de norma memorizables del tema. Diagrama de memorización directa.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 398" role="img" aria-label="Tabla visual con los protocolos de administración y monitorización de una red de área local y sus puertos: SSH 22, Telnet 23 obsoleto, HTTPS 443, DNS 53, DHCP 67 y 68, Kerberos 88, NTP 123, SNMP 161 y 162, LDAP 389 y 636, syslog 514 y 6514 sobre TLS, RADIUS 1812 y 1813, NETCONF 830, NetFlow e IPFIX 2055, sFlow 6343 y DNS sobre TLS 853, señalando cuáles son inseguros y por qué protocolo deben sustituirse">
  <style>.tb{font:700 9.5px system-ui,sans-serif;fill:#fff}.sb{font:8.5px system-ui,sans-serif;fill:#fff}.db{font:9px system-ui,sans-serif;fill:#333}.hb{font:700 13px system-ui,sans-serif;fill:#0055a0}.kb{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.nb{font:8.5px system-ui,sans-serif;fill:#666}.pb{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="hb">Puertos y normas: todo lo memorizable del tema, en un sitio</text>
  <text x="24" y="42" class="kb">SERVICIOS QUE HACEN UTILIZABLE LA RED</text>
  <rect x="20" y="48" width="156" height="34" rx="4" fill="#0055a0"/><text x="98" y="63" text-anchor="middle" class="tb">DNS</text><text x="98" y="76" text-anchor="middle" class="sb">53 UDP y TCP · RFC 1034/35</text>
  <rect x="182" y="48" width="156" height="34" rx="4" fill="#0055a0"/><text x="260" y="63" text-anchor="middle" class="tb">DHCP</text><text x="260" y="76" text-anchor="middle" class="sb">67 servidor / 68 cliente · RFC 2131</text>
  <rect x="344" y="48" width="156" height="34" rx="4" fill="#0055a0"/><text x="422" y="63" text-anchor="middle" class="tb">DHCPv6</text><text x="422" y="76" text-anchor="middle" class="sb">546 / 547 · RFC 8415</text>
  <rect x="506" y="48" width="154" height="34" rx="4" fill="#0055a0"/><text x="583" y="63" text-anchor="middle" class="tb">NTP</text><text x="583" y="76" text-anchor="middle" class="sb">123 UDP · RFC 5905</text>
  <text x="24" y="102" class="kb">IDENTIDAD Y CONTROL DE ACCESO</text>
  <rect x="20" y="108" width="156" height="34" rx="4" fill="#2d8659"/><text x="98" y="123" text-anchor="middle" class="tb">KERBEROS</text><text x="98" y="136" text-anchor="middle" class="sb">88 · RFC 4120</text>
  <rect x="182" y="108" width="156" height="34" rx="4" fill="#2d8659"/><text x="260" y="123" text-anchor="middle" class="tb">LDAP / LDAPS</text><text x="260" y="136" text-anchor="middle" class="sb">389 / 636 · RFC 4511</text>
  <rect x="344" y="108" width="156" height="34" rx="4" fill="#2d8659"/><text x="422" y="123" text-anchor="middle" class="tb">RADIUS</text><text x="422" y="136" text-anchor="middle" class="sb">1812 auth / 1813 cuentas</text>
  <rect x="506" y="108" width="154" height="34" rx="4" fill="#2d8659"/><text x="583" y="123" text-anchor="middle" class="tb">802.1X</text><text x="583" y="136" text-anchor="middle" class="sb">EAPOL · sin puerto IP</text>
  <text x="24" y="162" class="kb">ADMINISTRACIÓN DE LOS DISPOSITIVOS</text>
  <rect x="20" y="168" width="156" height="34" rx="4" fill="#e89822"/><text x="98" y="183" text-anchor="middle" class="tb">SSH</text><text x="98" y="196" text-anchor="middle" class="sb">22 TCP</text>
  <rect x="182" y="168" width="156" height="34" rx="4" fill="#e89822"/><text x="260" y="183" text-anchor="middle" class="tb">HTTPS de gestión</text><text x="260" y="196" text-anchor="middle" class="sb">443 TCP</text>
  <rect x="344" y="168" width="156" height="34" rx="4" fill="#e89822"/><text x="422" y="183" text-anchor="middle" class="tb">NETCONF</text><text x="422" y="196" text-anchor="middle" class="sb">830 sobre SSH · RFC 6241</text>
  <rect x="506" y="168" width="154" height="34" rx="4" fill="#e89822"/><text x="583" y="183" text-anchor="middle" class="tb">SNMP</text><text x="583" y="196" text-anchor="middle" class="sb">161 consulta / 162 trap</text>
  <text x="24" y="222" class="kb">MONITORIZACIÓN, FLUJOS Y REGISTRO</text>
  <rect x="20" y="228" width="156" height="34" rx="4" fill="#0055a0"/><text x="98" y="243" text-anchor="middle" class="tb">SYSLOG</text><text x="98" y="256" text-anchor="middle" class="sb">514 UDP · 6514 TLS · RFC 5424</text>
  <rect x="182" y="228" width="156" height="34" rx="4" fill="#0055a0"/><text x="260" y="243" text-anchor="middle" class="tb">NETFLOW v9</text><text x="260" y="256" text-anchor="middle" class="sb">2055 UDP · RFC 3954</text>
  <rect x="344" y="228" width="156" height="34" rx="4" fill="#0055a0"/><text x="422" y="243" text-anchor="middle" class="tb">IPFIX</text><text x="422" y="256" text-anchor="middle" class="sb">2055 UDP · RFC 7011</text>
  <rect x="506" y="228" width="154" height="34" rx="4" fill="#0055a0"/><text x="583" y="243" text-anchor="middle" class="tb">sFLOW</text><text x="583" y="256" text-anchor="middle" class="sb">6343 UDP · RFC 3176</text>
  <text x="24" y="282" class="kb">SUSTITUCIONES OBLIGADAS: FUERA LO QUE VIAJA EN CLARO</text>
  <rect x="20" y="288" width="200" height="30" rx="4" fill="#d13c3c"/><text x="120" y="307" text-anchor="middle" class="pb">TELNET 23  ✕</text>
  <text x="228" y="307" class="db">→</text>
  <rect x="244" y="288" width="200" height="30" rx="4" fill="#2d8659"/><text x="344" y="307" text-anchor="middle" class="pb">SSH 22  ✓</text>
  <rect x="460" y="288" width="200" height="30" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/><text x="560" y="307" text-anchor="middle" class="db">FTP/TFTP → SCP/SFTP</text>
  <rect x="20" y="324" width="200" height="30" rx="4" fill="#d13c3c"/><text x="120" y="343" text-anchor="middle" class="pb">SNMP v1 / v2c  ✕</text>
  <text x="228" y="343" class="db">→</text>
  <rect x="244" y="324" width="200" height="30" rx="4" fill="#2d8659"/><text x="344" y="343" text-anchor="middle" class="pb">SNMPv3  ✓</text>
  <rect x="460" y="324" width="200" height="30" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/><text x="560" y="343" text-anchor="middle" class="db">LDAP 389 → LDAPS 636</text>
  <rect x="20" y="360" width="640" height="20" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="374" text-anchor="middle" class="kb">v1 y v2c usan CADENA DE COMUNIDAD en claro · solo v3 autentica (authNoPriv) y cifra (authPriv)</text>
  <text x="670" y="394" text-anchor="end" class="nb">[Fuente: RFC3411; RFC5424; RFC7011; RFC2865]</text>
</svg>
```

---

## D12 · Gestión dentro de banda frente a gestión fuera de banda

**Sección**: §3.1.2 — Interfaces de gestión en banda y fuera de banda
**Propósito**: Fijar la distinción y su consecuencia práctica: la vía por la que se administra no debe depender de aquello que se administra.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 310" role="img" aria-label="Comparación entre gestión dentro de banda, que administra los dispositivos por la misma red que transporta los datos de usuario y se pierde si la red cae, y gestión fuera de banda, que utiliza una vía independiente como el puerto de consola, una red de gestión separada o un acceso por red móvil y sobrevive a la caída del plano de datos">
  <style>.tc{font:700 11px system-ui,sans-serif;fill:#fff}.sc{font:8.5px system-ui,sans-serif;fill:#fff}.dc{font:9px system-ui,sans-serif;fill:#333}.hc{font:700 13px system-ui,sans-serif;fill:#0055a0}.kc{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.nc{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <defs><marker id="a12" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="hc">Dentro de banda y fuera de banda</text>
  <rect x="20" y="34" width="316" height="30" rx="5" fill="#e89822"/><text x="178" y="54" text-anchor="middle" class="tc">DENTRO DE BANDA (in-band)</text>
  <rect x="344" y="34" width="316" height="30" rx="5" fill="#2d8659"/><text x="502" y="54" text-anchor="middle" class="tc">FUERA DE BANDA (out-of-band)</text>
  <rect x="30" y="76" width="80" height="34" rx="4" fill="#0055a0"/><text x="70" y="97" text-anchor="middle" class="tc">Técnico</text>
  <line x1="114" y1="93" x2="160" y2="93" stroke="#0055a0" stroke-width="2" marker-end="url(#a12)"/>
  <rect x="164" y="76" width="76" height="34" rx="4" fill="#888"/><text x="202" y="91" text-anchor="middle" class="sc">RED DE</text><text x="202" y="104" text-anchor="middle" class="sc">DATOS</text>
  <line x1="244" y1="93" x2="284" y2="93" stroke="#0055a0" stroke-width="2" marker-end="url(#a12)"/>
  <rect x="288" y="76" width="42" height="34" rx="4" fill="#0055a0"/><text x="309" y="97" text-anchor="middle" class="sc">SW</text>
  <rect x="354" y="76" width="80" height="34" rx="4" fill="#0055a0"/><text x="394" y="97" text-anchor="middle" class="tc">Técnico</text>
  <line x1="438" y1="86" x2="484" y2="86" stroke="#2d8659" stroke-width="2" marker-end="url(#a12)"/>
  <line x1="438" y1="102" x2="484" y2="102" stroke="#888" stroke-width="1.5" stroke-dasharray="3,3"/>
  <rect x="488" y="70" width="86" height="22" rx="4" fill="#2d8659"/><text x="531" y="85" text-anchor="middle" class="sc">RED DE GESTIÓN</text>
  <rect x="488" y="96" width="86" height="22" rx="4" fill="#ccc"/><text x="531" y="111" text-anchor="middle" style="font:8.5px system-ui;fill:#333">red de datos</text>
  <line x1="578" y1="86" x2="608" y2="93" stroke="#2d8659" stroke-width="2" marker-end="url(#a12)"/>
  <rect x="612" y="76" width="42" height="34" rx="4" fill="#0055a0"/><text x="633" y="97" text-anchor="middle" class="sc">SW</text>
  <text x="24" y="136" class="kc">SI LA RED DE DATOS CAE…</text>
  <rect x="20" y="142" width="316" height="34" rx="4" fill="#fbeaea"/>
  <text x="178" y="158" text-anchor="middle" class="dc">Se pierde TAMBIÉN la capacidad de gestionarla:</text><text x="178" y="171" text-anchor="middle" class="dc">hay que desplazar a alguien con un cable de consola</text>
  <rect x="344" y="142" width="316" height="34" rx="4" fill="#e8f4ee"/>
  <text x="502" y="158" text-anchor="middle" class="dc">La vía de gestión SOBREVIVE: el técnico entra</text><text x="502" y="171" text-anchor="middle" class="dc">por la otra puerta y recupera el equipo en minutos</text>
  <text x="24" y="198" class="kc">VÍAS FUERA DE BANDA HABITUALES</text>
  <rect x="20" y="204" width="156" height="30" rx="4" fill="#2d8659"/><text x="98" y="217" text-anchor="middle" class="tc">Puerto de consola</text><text x="98" y="229" text-anchor="middle" class="sc">exige presencia física</text>
  <rect x="182" y="204" width="156" height="30" rx="4" fill="#2d8659"/><text x="260" y="217" text-anchor="middle" class="tc">Servidor de consolas</text><text x="260" y="229" text-anchor="middle" class="sc">consolas accesibles en remoto</text>
  <rect x="344" y="204" width="156" height="30" rx="4" fill="#2d8659"/><text x="422" y="217" text-anchor="middle" class="tc">Puerto de gestión</text><text x="422" y="229" text-anchor="middle" class="sc">interfaz separada del dato</text>
  <rect x="506" y="204" width="154" height="30" rx="4" fill="#2d8659"/><text x="583" y="217" text-anchor="middle" class="tc">Acceso por red móvil</text><text x="583" y="229" text-anchor="middle" class="sc">independiente del operador fijo</text>
  <rect x="20" y="242" width="640" height="24" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="340" y="258" text-anchor="middle" class="dc">Escenario típico: aplicas una regla en remoto y pierdes la sesión que te permitía deshacerla</text>
  <rect x="90" y="272" width="500" height="20" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="286" text-anchor="middle" class="kc">ENS: red de gestión separada (mp.com.4) y accesible solo desde puestos autorizados (op.acc.2)</text>
  <text x="670" y="306" text-anchor="end" class="nc">[Fuente: ENS; SWITCH-VENDORS]</text>
</svg>
```

---

## D13 · Marcado de calidad de servicio: PCP, DSCP y clases

**Sección**: §4.1.4 — Mecanismos de clasificación, marcado y priorización de tráfico
**Propósito**: Distinguir el marcado de nivel 2 del de nivel 3, memorizar los valores de DSCP y ordenar las cinco operaciones de la calidad de servicio. Diagrama de memorización directa.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 384" role="img" aria-label="Esquema del marcado de calidad de servicio: el punto de código de prioridad de 3 bits vive en la etiqueta 802.1Q del nivel 2 y se pierde al encaminar, mientras que el punto de código de servicios diferenciados de 6 bits vive en la cabecera IP del nivel 3 y sobrevive extremo a extremo; se incluyen los valores de las clases voz 46, vídeo 34, señalización 24, transaccional 18 y mejor esfuerzo 0, y las cinco operaciones de clasificación, marcado, vigilancia, modelado y encolamiento">
  <style>.td{font:700 10px system-ui,sans-serif;fill:#fff}.sd{font:8.5px system-ui,sans-serif;fill:#fff}.dd{font:9px system-ui,sans-serif;fill:#333}.hd{font:700 13px system-ui,sans-serif;fill:#0055a0}.kd{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.nd{font:8.5px system-ui,sans-serif;fill:#666}.vd{font:700 13px system-ui,sans-serif;fill:#fff}</style>
  <defs><marker id="a13" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="hd">Calidad de servicio: dónde se marca y con qué valor</text>
  <rect x="20" y="34" width="316" height="76" rx="5" fill="#e89822"/>
  <text x="178" y="52" text-anchor="middle" class="td">NIVEL 2 — PCP (también llamado CoS)</text>
  <text x="178" y="70" text-anchor="middle" class="sd">3 bits · valores 0-7 · dentro de la etiqueta 802.1Q</text>
  <text x="178" y="86" text-anchor="middle" class="sd">Solo existe en tramas ETIQUETADAS</text>
  <text x="178" y="102" text-anchor="middle" class="sd">SE PIERDE al cruzar un encaminador</text>
  <rect x="344" y="34" width="316" height="76" rx="5" fill="#0055a0"/>
  <text x="502" y="52" text-anchor="middle" class="td">NIVEL 3 — DSCP</text>
  <text x="502" y="70" text-anchor="middle" class="sd">6 bits · valores 0-63 · campo DS de la cabecera IP</text>
  <text x="502" y="86" text-anchor="middle" class="sd">Viaja en TODO paquete IP</text>
  <text x="502" y="102" text-anchor="middle" class="sd">SOBREVIVE de extremo a extremo</text>
  <text x="24" y="132" class="kd">VALORES DE DSCP QUE HAY QUE RECONOCER</text>
  <rect x="20" y="138" width="124" height="44" rx="4" fill="#d13c3c"/><text x="82" y="155" text-anchor="middle" class="vd">EF = 46</text><text x="82" y="169" text-anchor="middle" class="sd">VOZ</text><text x="82" y="179" text-anchor="middle" class="sd">cola de prioridad</text>
  <rect x="150" y="138" width="124" height="44" rx="4" fill="#0055a0"/><text x="212" y="155" text-anchor="middle" class="vd">AF41 = 34</text><text x="212" y="169" text-anchor="middle" class="sd">VÍDEO INTERACTIVO</text><text x="212" y="179" text-anchor="middle" class="sd">clase garantizada</text>
  <rect x="280" y="138" width="124" height="44" rx="4" fill="#2d8659"/><text x="342" y="155" text-anchor="middle" class="vd">CS3 = 24</text><text x="342" y="169" text-anchor="middle" class="sd">SEÑALIZACIÓN</text><text x="342" y="179" text-anchor="middle" class="sd">poco caudal, crítica</text>
  <rect x="410" y="138" width="124" height="44" rx="4" fill="#e89822"/><text x="472" y="155" text-anchor="middle" class="vd">AF21 = 18</text><text x="472" y="169" text-anchor="middle" class="sd">TRANSACCIONAL</text><text x="472" y="179" text-anchor="middle" class="sd">aplicaciones de gestión</text>
  <rect x="540" y="138" width="120" height="44" rx="4" fill="#888"/><text x="600" y="155" text-anchor="middle" class="vd">BE = 0</text><text x="600" y="169" text-anchor="middle" class="sd">MEJOR ESFUERZO</text><text x="600" y="179" text-anchor="middle" class="sd">copias, actualizaciones</text>
  <rect x="20" y="190" width="640" height="24" rx="4" fill="#eef3f8"/>
  <text x="340" y="206" text-anchor="middle" class="dd">Clases AFxy: x = clase (1 a 4) · y = precedencia de descarte (1 a 3; a mayor y, antes se descarta)</text>
  <text x="24" y="236" class="kd">LAS CINCO OPERACIONES, EN ORDEN</text>
  <rect x="20" y="242" width="118" height="40" rx="4" fill="#0055a0"/><text x="79" y="258" text-anchor="middle" class="td">1 CLASIFICAR</text><text x="79" y="273" text-anchor="middle" class="sd">¿a qué clase pertenece?</text>
  <line x1="142" y1="262" x2="152" y2="262" stroke="#0055a0" stroke-width="2" marker-end="url(#a13)"/>
  <rect x="156" y="242" width="118" height="40" rx="4" fill="#0055a0"/><text x="215" y="258" text-anchor="middle" class="td">2 MARCAR</text><text x="215" y="273" text-anchor="middle" class="sd">escribir DSCP o PCP</text>
  <line x1="278" y1="262" x2="288" y2="262" stroke="#0055a0" stroke-width="2" marker-end="url(#a13)"/>
  <rect x="292" y="242" width="118" height="40" rx="4" fill="#d13c3c"/><text x="351" y="258" text-anchor="middle" class="td">3 VIGILAR</text><text x="351" y="273" text-anchor="middle" class="sd">descarta o remarca</text>
  <line x1="414" y1="262" x2="424" y2="262" stroke="#0055a0" stroke-width="2" marker-end="url(#a13)"/>
  <rect x="428" y="242" width="112" height="40" rx="4" fill="#e89822"/><text x="484" y="258" text-anchor="middle" class="td">4 MODELAR</text><text x="484" y="273" text-anchor="middle" class="sd">almacena y retrasa</text>
  <line x1="544" y1="262" x2="554" y2="262" stroke="#0055a0" stroke-width="2" marker-end="url(#a13)"/>
  <rect x="558" y="242" width="102" height="40" rx="4" fill="#2d8659"/><text x="609" y="258" text-anchor="middle" class="td">5 ENCOLAR</text><text x="609" y="273" text-anchor="middle" class="sd">reparte la salida</text>
  <rect x="20" y="290" width="316" height="26" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="178" y="307" text-anchor="middle" class="dd">VIGILAR: descarta, NO retrasa · MODELAR: retrasa, NO descarta</text>
  <rect x="344" y="290" width="316" height="26" rx="4" fill="#e8f4ee" stroke="#2d8659" stroke-width="1.2"/>
  <text x="502" y="307" text-anchor="middle" class="dd">Se vigila en la ENTRADA · se modela en la SALIDA</text>
  <rect x="20" y="324" width="640" height="24" rx="4" fill="#fdf3e3" stroke="#e89822" stroke-width="1.2"/>
  <text x="340" y="340" text-anchor="middle" class="dd">FRONTERA DE CONFIANZA: el marcado del equipo de usuario NO es de fiar. Se clasifica y remarca en el BORDE; el núcleo solo encola</text>
  <rect x="90" y="352" width="500" height="18" rx="3" fill="none" stroke="#0055a0" stroke-width="1.2"/>
  <text x="340" y="364" text-anchor="middle" style="font:700 8.5px system-ui;fill:#0055a0">La calidad de servicio NO crea capacidad: solo decide quién sufre la congestión</text>
  <text x="670" y="380" text-anchor="end" class="nd">[Fuente: RFC2474; RFC2597; RFC4594]</text>
</svg>
```

---

## D14 · Paquetes frente a flujos: qué instrumento para qué pregunta

**Sección**: §4.2.1 y §4.2.2 — Captura de paquetes · Monitorización por flujos
**Propósito**: Elegir el instrumento correcto según la pregunta, y distinguir SPAN de TAP y NetFlow de IPFIX y de sFlow.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 350" role="img" aria-label="Comparación entre la captura de paquetes, que obtiene el contenido completo pero genera un volumen enorme y es muy sensible en protección de datos, y los registros de flujo, que obtienen metadatos sobre quién habla con quién cuánto y cuándo, con volumen reducido y cobertura de toda la red; se distinguen además el espejo de puertos SPAN de la derivación física TAP, y NetFlow v9 de IPFIX y de sFlow">
  <style>.te{font:700 11px system-ui,sans-serif;fill:#fff}.se{font:8.5px system-ui,sans-serif;fill:#fff}.de{font:9px system-ui,sans-serif;fill:#333}.he{font:700 13px system-ui,sans-serif;fill:#0055a0}.ke{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.ne{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="he">Dos instrumentos, dos preguntas distintas</text>
  <rect x="20" y="34" width="316" height="30" rx="5" fill="#d13c3c"/><text x="178" y="54" text-anchor="middle" class="te">CAPTURA DE PAQUETES — «¿qué se dijeron?»</text>
  <rect x="344" y="34" width="316" height="30" rx="5" fill="#2d8659"/><text x="502" y="54" text-anchor="middle" class="te">REGISTROS DE FLUJO — «¿quién habló con quién?»</text>
  <text x="24" y="82" class="ke">QUÉ OBTIENE</text>
  <rect x="20" y="88" width="316" height="28" rx="4" fill="#fbeaea"/><text x="178" y="106" text-anchor="middle" class="de">El CONTENIDO completo de la conversación</text>
  <rect x="344" y="88" width="316" height="28" rx="4" fill="#e8f4ee"/><text x="502" y="106" text-anchor="middle" class="de">METADATOS: origen, destino, volumen, momento</text>
  <text x="24" y="134" class="ke">VOLUMEN Y COBERTURA</text>
  <rect x="20" y="140" width="316" height="28" rx="4" fill="#fbeaea"/><text x="178" y="158" text-anchor="middle" class="de">Enorme (terabytes) · un solo punto de la red</text>
  <rect x="344" y="140" width="316" height="28" rx="4" fill="#e8f4ee"/><text x="502" y="158" text-anchor="middle" class="de">Muy reducido · TODA la red, de forma continua</text>
  <text x="24" y="186" class="ke">USO NATURAL Y PROTECCIÓN DE DATOS</text>
  <rect x="20" y="192" width="316" height="42" rx="4" fill="#fbeaea"/>
  <text x="178" y="209" text-anchor="middle" class="de">Diagnóstico PUNTUAL y dirigido</text><text x="178" y="225" text-anchor="middle" class="de">Muy sensible: contiene comunicaciones de personas</text>
  <rect x="344" y="192" width="316" height="42" rx="4" fill="#e8f4ee"/>
  <text x="502" y="209" text-anchor="middle" class="de">Vigilancia CONTINUA e investigación retrospectiva</text><text x="502" y="225" text-anchor="middle" class="de">Sensible, pero SIN contenido</text>
  <text x="24" y="256" class="ke">CÓMO SE CAPTURA</text>
  <rect x="20" y="262" width="156" height="42" rx="4" fill="#0055a0"/><text x="98" y="278" text-anchor="middle" class="te">SPAN</text><text x="98" y="292" text-anchor="middle" class="se">espejo por configuración</text><text x="98" y="302" text-anchor="middle" class="se">descarta si se satura</text>
  <rect x="182" y="262" width="156" height="42" rx="4" fill="#2d8659"/><text x="260" y="278" text-anchor="middle" class="te">TAP</text><text x="260" y="292" text-anchor="middle" class="se">derivación física pasiva</text><text x="260" y="302" text-anchor="middle" class="se">fiel al 100 %</text>
  <text x="348" y="256" class="ke">CÓMO SE EXPORTAN LOS FLUJOS</text>
  <rect x="344" y="262" width="102" height="42" rx="4" fill="#e89822"/><text x="395" y="278" text-anchor="middle" class="te">NetFlow v9</text><text x="395" y="292" text-anchor="middle" class="se">Cisco · RFC 3954</text><text x="395" y="302" text-anchor="middle" class="se">flujo completo</text>
  <rect x="452" y="262" width="102" height="42" rx="4" fill="#0055a0"/><text x="503" y="278" text-anchor="middle" class="te">IPFIX</text><text x="503" y="292" text-anchor="middle" class="se">IETF · RFC 7011</text><text x="503" y="302" text-anchor="middle" class="se">la norma abierta</text>
  <rect x="560" y="262" width="100" height="42" rx="4" fill="#2d8659"/><text x="610" y="278" text-anchor="middle" class="te">sFlow</text><text x="610" y="292" text-anchor="middle" class="se">RFC 3176</text><text x="610" y="302" text-anchor="middle" class="se">por MUESTREO</text>
  <rect x="20" y="312" width="640" height="24" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="328" text-anchor="middle" class="ke">Flujo = quíntupla: IP y puerto de origen + IP y puerto de destino + protocolo</text>
  <text x="670" y="347" text-anchor="end" class="ne">[Fuente: RFC3954; RFC7011; SFLOW; WIRESHARK]</text>
</svg>
```

---

## D15 · El ENS aplicado a la red de área local

**Sección**: §4.2.4 — Cumplimiento del Esquema Nacional de Seguridad en la administración LAN
**Propósito**: Cerrar el tema traduciendo cada sección a la medida del Anexo II del RD 311/2022 que la respalda, y fijar dimensiones, niveles y categorías.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Mapa que relaciona cada parte del tema con la medida del Anexo II del Esquema Nacional de Seguridad que la respalda: la segmentación con la medida de separación de flujos de información en la red, la gestión de usuarios con las medidas de control de acceso, el inventario y el parcheo con las de explotación, y la monitorización con las de detección de intrusión, sistema de métricas y vigilancia; se recogen además las cinco dimensiones de seguridad y las tres categorías de sistema">
  <style>.tf{font:700 10px system-ui,sans-serif;fill:#fff}.sf{font:8.5px system-ui,sans-serif;fill:#fff}.df{font:9px system-ui,sans-serif;fill:#333}.hf{font:700 13px system-ui,sans-serif;fill:#0055a0}.kf{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.nf{font:8.5px system-ui,sans-serif;fill:#666}.cf{font:700 9.5px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="hf">Cada sección del tema tiene su medida en el Anexo II del ENS</text>
  <text x="24" y="42" class="kf">CINCO DIMENSIONES DE SEGURIDAD — RD 311/2022</text>
  <rect x="20" y="48" width="124" height="26" rx="4" fill="#0055a0"/><text x="82" y="65" text-anchor="middle" class="cf">Disponibilidad</text>
  <rect x="150" y="48" width="124" height="26" rx="4" fill="#0055a0"/><text x="212" y="65" text-anchor="middle" class="cf">Autenticidad</text>
  <rect x="280" y="48" width="124" height="26" rx="4" fill="#0055a0"/><text x="342" y="65" text-anchor="middle" class="cf">Integridad</text>
  <rect x="410" y="48" width="124" height="26" rx="4" fill="#0055a0"/><text x="472" y="65" text-anchor="middle" class="cf">Confidencialidad</text>
  <rect x="540" y="48" width="120" height="26" rx="4" fill="#0055a0"/><text x="600" y="65" text-anchor="middle" class="cf">Trazabilidad</text>
  <rect x="20" y="80" width="316" height="24" rx="4" fill="#eef3f8"/><text x="178" y="96" text-anchor="middle" class="df">Tres NIVELES por dimensión: bajo · medio · alto</text>
  <rect x="344" y="80" width="316" height="24" rx="4" fill="#eef3f8"/><text x="502" y="96" text-anchor="middle" class="df">Tres CATEGORÍAS de sistema: BÁSICA · MEDIA · ALTA</text>
  <text x="24" y="126" class="kf">DE CADA SECCIÓN DEL TEMA A SU MEDIDA</text>
  <rect x="20" y="132" width="200" height="30" rx="4" fill="#e89822"/><text x="120" y="145" text-anchor="middle" class="tf">§1 · Segmentación en VLAN</text><text x="120" y="157" text-anchor="middle" class="sf">y red de gestión separada</text>
  <text x="228" y="152" class="df">→</text>
  <rect x="244" y="132" width="416" height="30" rx="4" fill="#fdf3e3" stroke="#e89822" stroke-width="1.2"/>
  <text x="452" y="152" text-anchor="middle" class="df">mp.com.4 separación de flujos · mp.com.1 perímetro seguro · mp.com.2 y mp.com.3</text>
  <rect x="20" y="168" width="200" height="30" rx="4" fill="#2d8659"/><text x="120" y="181" text-anchor="middle" class="tf">§2 · Gestión de usuarios</text><text x="120" y="193" text-anchor="middle" class="sf">directorio, GPO, RBAC</text>
  <text x="228" y="188" class="df">→</text>
  <rect x="244" y="168" width="416" height="30" rx="4" fill="#e8f4ee" stroke="#2d8659" stroke-width="1.2"/>
  <text x="452" y="188" text-anchor="middle" class="df">op.acc.1 a op.acc.6 · op.acc.3 segregación de funciones · op.exp.2 y op.exp.3 configuración</text>
  <rect x="20" y="204" width="200" height="30" rx="4" fill="#0055a0"/><text x="120" y="217" text-anchor="middle" class="tf">§3 · Gestión de dispositivos</text><text x="120" y="229" text-anchor="middle" class="sf">inventario, parches, admisión</text>
  <text x="228" y="224" class="df">→</text>
  <rect x="244" y="204" width="416" height="30" rx="4" fill="#eef3f8" stroke="#0055a0" stroke-width="1.2"/>
  <text x="452" y="224" text-anchor="middle" class="df">op.exp.1 inventario · op.exp.4 actualizaciones · mp.eq.4 otros dispositivos conectados</text>
  <rect x="20" y="240" width="200" height="30" rx="4" fill="#d13c3c"/><text x="120" y="253" text-anchor="middle" class="tf">§4 · Monitorización y tráfico</text><text x="120" y="265" text-anchor="middle" class="sf">métricas, flujos, registros</text>
  <text x="228" y="260" class="df">→</text>
  <rect x="244" y="240" width="416" height="30" rx="4" fill="#fbeaea" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="452" y="260" text-anchor="middle" class="df">op.mon.1 detección de intrusión · op.mon.2 métricas · op.mon.3 vigilancia · op.exp.8 registro</text>
  <rect x="20" y="280" width="640" height="24" rx="4" fill="#fdf3e3" stroke="#e89822" stroke-width="1.2"/>
  <text x="340" y="296" text-anchor="middle" class="df">Categoría MEDIA y ALTA: auditoría al menos BIENAL · Categoría BÁSICA: autoevaluación</text>
  <rect x="20" y="312" width="640" height="24" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="328" text-anchor="middle" class="kf">Lo no inventariado no se protege · lo no segmentado no se contiene · lo no registrado no se demuestra</text>
  <text x="670" y="352" text-anchor="end" class="nf">[Fuente: ENS; CCN-STIC]</text>
</svg>
```
