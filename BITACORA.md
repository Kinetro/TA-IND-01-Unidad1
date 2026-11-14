
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

### Próxima actividad
Enviar mensajes al flujo replicado y realizar una prueba de tolerancia a fallos mediante la caída y recuperación de un nodo.
