
# Bitácora de trabajo — TA-IND-01

**Tema:** Análisis de NATS JetStream y comparación con Apache Pulsar.

## Sesión 1 — 13-11-2026

### Actividades realizadas
- Se seleccionó NATS JetStream como sistema distribuido para el análisis.
- Se eligió Apache Pulsar como sistema de comparación.
- Se creó el repositorio de GitHub.
- Se inició la bitácora del proyecto.

### Problemas encontrados
Ninguno hasta el momento.

### Soluciones aplicadas
No fue necesario aplicar soluciones.

### Tiempo dedicado
30 minutos.

---

## Sesión 2 — 14-11-2026

### Actividades realizadas
- Se investigó el funcionamiento general de NATS JetStream.
- Se identificaron sus componentes principales: publicador, consumidor, servidores y clúster.
- Se revisó cómo funciona la replicación de mensajes entre los nodos.
- Se elaboró el esquema inicial de arquitectura a mano para el Anexo A.

### Problemas encontrados
Comprender cómo se relacionan los nodos y cómo se realiza la replicación de mensajes.

### Soluciones aplicadas
Se revisaron los conceptos de la arquitectura y se representó gráficamente la comunicación entre los componentes.

### Tiempo dedicado
1 hora.

---

## Sesión 3 — 14-11-2026

### Actividades realizadas
- Se instalaron NATS Server y NATS CLI en CachyOS.
- Se verificó el funcionamiento de JetStream mediante el almacenamiento de un mensaje.
- Se configuró un clúster local de tres nodos utilizando los puertos 4222, 4223 y 4224.
- Se creó el flujo PRUEBA_R3 con tres réplicas.
- Se comprobó que nodo3 asumió el liderazgo y que nodo1 y nodo2 estaban sincronizados.
- Se guardaron capturas de la instalación y las pruebas realizadas.
- Se corrigió el esquema inicial de NATS JetStream.
- Se añadieron los datos de identificación al dibujo.
- Se preparó la fotografía definitiva para el Anexo A.

### Problemas encontrados
- JetStream no iniciaba porque faltaban rutas de comunicación entre los nodos.
- El comando de monitoreo requería permisos de la cuenta SYS.

### Soluciones aplicadas
- Se configuraron las rutas para permitir la conexión entre los tres nodos.
- Se utilizó `nats stream info PRUEBA_R3` para verificar el estado de las réplicas.

### Tiempo dedicado
1 hora.

---

## Sesión 4 — 14-11-2026

### Actividades realizadas
- Se enviaron tres mensajes al flujo replicado PRUEBA_R3.
- Se verificó el almacenamiento y recuperación de los mensajes.
- Se simuló la caída del nodo líder (nodo3).
- Se comprobó que nodo1 asumió el liderazgo y el sistema continuó funcionando.
- Se envió un cuarto mensaje durante el fallo.
- Se reinició nodo3 y se verificó su sincronización.
- Se documentaron los comandos, resultados y evidencias del experimento.

### Problemas encontrados
No se presentaron errores durante la ejecución del experimento.

### Soluciones aplicadas
No fue necesario aplicar correcciones.

### Tiempo dedicado
1 hora.

---

## Sesión 5 — 14-11-2026

### Actividades realizadas
- Se buscaron y revisaron artículos científicos relacionados con NATS JetStream y Apache Pulsar.
- Se seleccionaron fuentes para fundamentar el análisis técnico y comparativo.
- Se identificaron y subrayaron fragmentos relevantes de tres artículos científicos.
- Se guardaron las tres capturas correspondientes al Anexo B.
- Se preparó el archivo referencias.bib con siete referencias bibliográficas.

### Problemas encontrados
Algunos artículos abordaban los sistemas de manera general y no explicaban directamente todos los conceptos de la Unidad 1.

### Soluciones aplicadas
Se complementaron las publicaciones científicas con documentación técnica oficial de NATS y Apache Pulsar.

### Tiempo dedicado
1 hora.

### Próxima actividad
Elaborar el diagrama definitivo de arquitectura de NATS JetStream en draw.io.


