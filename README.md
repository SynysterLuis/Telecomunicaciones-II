# Telecomunicaciones II — Laboratorios con RIOT OS

Repositorio de prácticas de Telecomunicaciones II de la carrera de
Ingeniería Electrónica de la Universidad Católica
"Nuestra Señora de la Asunción", Paraguay.

## Plataforma utilizada

- Sistema operativo: RIOT OS 2026.04
- Hardware: TelosB (MSP430F1611 y CC2420)
- Entorno de desarrollo: Ubuntu sobre WSL2
- Compilador: MSP430 GCC
- Comunicación: IEEE 802.15.4
- Programación: GoodFET BSL
- Comunicación serie: UART a 9600 baudios

## Laboratorios

### Laboratorio 1 — Hello World y LED temporizados

Introducción al desarrollo de aplicaciones para TelosB utilizando RIOT OS.

- Compilación y programación del microcontrolador.
- Ejecución de Hello World mediante UART.
- Control secuencial de tres LED con temporizadores.
- Implementación de una shell con comandos `help` e `info`.
- Intervalo de conmutación de LED: 500 ms.

### Laboratorio 2 — Comunicación punto a punto

Implementación y evaluación de comunicación inalámbrica entre dos TelosB.

- Transmisión y recepción de tramas IEEE 802.15.4.
- Configuración de nodos transmisor (TX) y receptor (RX).
- Estudio experimental de RSSI, LQI y PRR.
- Comparación con CSMA/CCA activado y desactivado.
- Pruebas con distintas distancias y obstáculos.
- Registros experimentales, resultados CSV y gráficas.

La carpeta `Codigo/Modulo_RIOT` contiene una versión del módulo
utilizado durante las pruebas. Debe revisarse su integración con
RIOT antes de reutilizarlo.

### Laboratorio 3 — Comunicación multisalto

Implementación de una red de tres nodos con ruta fija:

SENSOR (1) → RELAY (2) → SINK (3)

- Comunicación de dos saltos IEEE 802.15.4.
- Reenvío de mensajes mediante un nodo intermedio.
- Seguimiento de secuencias, HOPS y TTL.
- Estadísticas de recepción y pérdidas.
- Comparación experimental con CSMA/CCA activado y desactivado.

Resultados observados:

| Indicador | CSMA/CCA OFF | CSMA/CCA ON |
|---|---:|---:|
| PRR primer salto | 95,0 % | 98,3 % |
| PRR estimado en SINK | 91,8 % | 91,8 % |

Los PRR corresponden a estimaciones de las ventanas experimentales
y no constituyen una medición independiente de todas las tramas
efectivamente transmitidas.

## Compilación

Los proyectos requieren RIOT OS 2026.04 y la toolchain MSP430 GCC.

Ejemplo general:

```bash
make BOARD=telosb clean all
make BOARD=telosb PORT=/dev/ttyUSB0 flash
make BOARD=telosb PORT=/dev/ttyUSB0 BAUD=9600 term



```
Verificar siempre el puerto y la identidad física del dispositivo antes de programarlo.

## Contenido

Cada laboratorio incluye, según corresponda:
- Código fuente y archivos Makefile.
- Capturas de las pruebas.
- Registros experimentales.
- Archivos CSV y gráficas.
- Resultados y observaciones.

## Observaciones

Los experimentos fueron realizados con placas TelosB y RIOT OS.
El Laboratorio 3 utiliza una ruta fija y no implementa IPv6, UDP ni descubrimiento dinámico de rutas.

Material académico de prácticas de Telecomunicaciones II.
