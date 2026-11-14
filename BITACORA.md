
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

---

## Sesión 6 — 14-11-2026

### Actividades realizadas
- Se elaboró el diagrama digital de la arquitectura de NATS JetStream en draw.io.
- Se representaron los tres nodos del clúster y sus puertos de comunicación.
- Se identificó el flujo PRUEBA_R3 y su replicación mediante Raft.
- Se documentó el cambio de líder observado durante el experimento.
- Se preparó el diagrama para incorporarlo al informe académico.

### Problemas encontrados
No se presentaron dificultades importantes.

### Soluciones aplicadas
No fue necesario aplicar correcciones.

### Tiempo dedicado
40 minutos.

---

## Sesión 7 — 14-11-2026

### Actividades realizadas
- Se desarrolló el análisis de transparencias de distribución, CAP, PACELC y modelos de comunicación de NATS JetStream.
- Se analizó la tolerancia a fallos mediante replicación, consenso Raft y elección del líder.
- Se revisó la coherencia entre las afirmaciones del informe, las fuentes bibliográficas y los resultados experimentales.
- Se incorporaron citas científicas para fortalecer la fundamentación del análisis.
- Se corrigieron las explicaciones sobre migración y reubicación de réplicas.
- Se integró el diagrama definitivo y se ajustaron las rutas de los anexos.
- Se corrigieron problemas de formato y se verificó la compilación del documento en LaTeX.

### Problemas encontrados
- Algunas afirmaciones necesitaban mayor respaldo bibliográfico.
- El diagrama no aparecía en el PDF por diferencias en las rutas de los archivos.
- Se identificaron imprecisiones conceptuales y problemas de formato en una tabla.

### Soluciones aplicadas
- Se contrastó el contenido con artículos científicos y documentación oficial.
- Se corrigieron las rutas de las imágenes y la presentación de la tabla.
- Se precisaron los conceptos técnicos y se comprobó nuevamente la compilación del informe.

### Tiempo dedicado
4 horas.


## Sesión 9 — 15-11-2026

### Actividades realizadas
- Se realizó la revisión final del informe académico en LaTeX.
- Se incorporaron los ejemplos personales de Jóvenes en Acción y WhatsApp.
- Se verificó la coherencia entre el análisis técnico, las referencias y las evidencias experimentales.
- Se corrigieron detalles de redacción y se comprobó la compilación del PDF.
- Se preparó y grabó el video de sustentación del experimento.
- Se actualizó el README con el enlace al video y las instrucciones de compilación.
- Se organizaron los archivos del repositorio para la entrega.

### Problemas encontrados
Se identificaron algunos textos pendientes y repeticiones en el informe que debían corregirse antes de la entrega.

### Soluciones aplicadas
Se completaron las secciones faltantes, se revisó el contenido y se verificó que el documento compilara correctamente.

### Tiempo dedicado
2 horas.

### Próxima actividad
Verificar el repositorio público, comprobar el historial de commits y entregar el PDF de identificación en el SGA.




