
# Experimento de tolerancia a fallos — NATS JetStream

## 1. Objetivo
Comprobar cómo responde NATS JetStream ante la interrupción de un nodo líder y verificar si mantiene la disponibilidad de los mensajes mediante replicación.

## 2. Entorno de pruebas
- Sistema operativo: CachyOS Linux.
- NATS Server: 2.15.3.
- NATS CLI: 0.5.1.
- Clúster: laboratorio.
- Nodos: nodo1 (4222), nodo2 (4223) y nodo3 (4224).
- Flujo: PRUEBA_R3.
- Factor de replicación: 3.
- Fecha: 14-11-2026.

## 3. Procedimiento

### Prueba 1. Almacenamiento de mensajes
Se enviaron tres mensajes al flujo replicado.

Comando utilizado:

```bash
nats --server nats://127.0.0.1:4222 pub replica.mensaje "Mensaje 1 - Antes del fallo"
```

Se repitió el comando para los mensajes 2 y 3.

Resultado: el flujo almacenó tres mensajes y permitió recuperar el primero mediante:

```bash
nats --server nats://127.0.0.1:4222 stream get PRUEBA_R3 1
```

### Prueba 2. Interrupción del líder
Se detuvo manualmente nodo3 mediante Ctrl + C.

Se consultó el estado del flujo:

```bash
nats --server nats://127.0.0.1:4222 stream info PRUEBA_R3
```

Resultados observados:
- nodo1 asumió el liderazgo.
- nodo2 permaneció sincronizado.
- nodo3 apareció como OFFLINE.
- Se publicó un cuarto mensaje durante la interrupción.
- El flujo registró cuatro mensajes almacenados.

### Prueba 3. Recuperación del nodo
Se reinició nodo3 utilizando su configuración y almacenamiento originales.

Se consultó nuevamente el estado del flujo.

Resultados observados:
- nodo1 permaneció como líder.
- nodo2 y nodo3 aparecieron como current.
- Se conservaron los cuatro mensajes.
- Se verificó la recuperación del cuarto mensaje mediante el puerto 4224.

## 4. Interpretación
El experimento permitió observar que NATS JetStream mantiene la disponibilidad del flujo replicado cuando uno de sus tres nodos deja de funcionar.

Al interrumpirse el líder, otro nodo asumió su función. Los dos servidores restantes mantuvieron el quórum necesario para continuar almacenando mensajes.

Cuando el nodo detenido volvió a iniciarse, se sincronizó nuevamente con el clúster.

La prueba representa una interrupción controlada mediante Ctrl + C, no una falla abrupta del proceso.

## 5. Evidencias
- 03_cluster_replicado.png
- 04_mensajes_antes_fallo.png
- 05_caida_nodo_lider.png
- 06_recuperacion_nodo.png


## 6. Comandos para reproducir el experimento

### Preparar los directorios
```bash
mkdir -p experimentos/datos/{nodo1,nodo2,nodo3}
```

### Iniciar el clúster

Ejecutar cada comando en una terminal diferente.

**Nodo 1**
```bash
nats-server -js -n nodo1 \
-sd ./experimentos/datos/nodo1 \
-a 127.0.0.1 -p 4222 \
-cluster nats://127.0.0.1:6222 \
-routes nats://127.0.0.1:6223 \
--cluster_name laboratorio
```

**Nodo 2**
```bash
nats-server -js -n nodo2 \
-sd ./experimentos/datos/nodo2 \
-a 127.0.0.1 -p 4223 \
-cluster nats://127.0.0.1:6223 \
-routes nats://127.0.0.1:6222 \
--cluster_name laboratorio
```

**Nodo 3**
```bash
nats-server -js -n nodo3 \
-sd ./experimentos/datos/nodo3 \
-a 127.0.0.1 -p 4224 \
-cluster nats://127.0.0.1:6224 \
-routes nats://127.0.0.1:6222 \
--cluster_name laboratorio
```

### Crear el flujo replicado
```bash
nats --server nats://127.0.0.1:4222 stream add PRUEBA_R3 \
--subjects "replica.>" \
--storage file \
--retention limits \
--replicas 3 \
--defaults
```

Este comando se utiliza en una instalación nueva, cuando el flujo todavía no existe.

### Simular la caída
Detener el nodo líder con Ctrl + C y verificar la elección de un nuevo líder.

### Recuperar el nodo
Reiniciar el servidor detenido con su comando original, conservando el mismo directorio de datos.

### Verificar el resultado
```bash
nats --server nats://127.0.0.1:4222 stream info PRUEBA_R3
nats --server nats://127.0.0.1:4224 stream get PRUEBA_R3 4
```
