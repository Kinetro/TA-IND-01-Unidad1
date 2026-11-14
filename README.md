
# TA-IND-01 — Análisis de Sistemas Distribuidos

## Descripción

Este proyecto presenta un análisis de NATS JetStream como sistema distribuido y su comparación con Apache Pulsar, aplicando los conceptos de la Unidad 1 de Aplicaciones Distribuidas.

Se estudian las transparencias de distribución, CAP, PACELC, los modelos de comunicación y la tolerancia a fallos, utilizando documentación técnica y experimentación propia.

## Experimentación

Se configuró un clúster local de NATS JetStream en CachyOS Linux, compuesto por tres nodos y un flujo de mensajes con tres réplicas.

Durante las pruebas se realizaron las siguientes actividades:

- Configuración y verificación del clúster.
- Publicación y recuperación de mensajes.
- Interrupción controlada del nodo líder.
- Verificación de la elección de un nuevo líder.
- Recuperación y sincronización del nodo detenido.

Los resultados mostraron que el clúster continuó funcionando durante la caída de un nodo, manteniendo el quórum necesario.

Los comandos, resultados y capturas se encuentran en `experimentos/`.

## Estructura del repositorio

```text
TA-IND-01-Unidad1/
├── informe/
│   ├── informe.tex
│   └── informe.pdf
├── imagenes/
│   └── logo-uteq.jpg
├── diagramas/
│   ├── arquitectura_nats.drawio
│   └── arquitectura_nats.drawio.png
├── experimentos/
│   ├── EXPERIMENTO.md
│   ├── capturas/
│   └── resultados/
├── Anexos/
│   ├── esquema_inicial.jpeg
│   └── fuentes/
├── referencias.bib
├── BITACORA.md
└── README.md
```

## Compilación del informe

El informe está desarrollado en LaTeX y utiliza `biblatex` con el estilo IEEE.

### Requisitos

- TeX Live
- pdfLaTeX
- Biber
- Paquetes de LaTeX utilizados en `informe.tex`

En CachyOS se pueden instalar las dependencias principales con:

```bash
sudo pacman -S --needed texlive-basic texlive-latex \
texlive-latexrecommended texlive-latexextra \
texlive-bibtexextra texlive-fontsrecommended biber
```

### Instrucciones

Clonar el repositorio:

```bash
git clone https://github.com/Kinetro/TA-IND-01-Unidad1.git
cd TA-IND-01-Unidad1/informe
```

Compilar el documento en el siguiente orden:

```bash
pdflatex informe.tex
biber informe
pdflatex informe.tex
pdflatex informe.tex
```

El resultado será `informe/informe.pdf`.

Para que la compilación funcione correctamente, deben conservarse las carpetas, imágenes y el archivo `referencias.bib` en sus rutas originales.

## Evidencias de autoría

El repositorio incluye:

- Esquema inicial de arquitectura elaborado a mano.
- Diagrama definitivo editable en draw.io.
- Capturas originales de las pruebas realizadas.
- Comandos y resultados de experimentación.
- Capturas de lectura de fuentes científicas.
- Bitácora con las sesiones de trabajo.
- Historial de commits del desarrollo.

## Video de sustentación

[Ver video de sustentación de NATS JetStream](https://youtu.be/fAZ8cB-4gjY)

En el video se explica la arquitectura de NATS JetStream, el experimento de tolerancia a fallos y las principales conclusiones del análisis.

## Datos académicos

**Universidad:** Universidad Técnica Estatal de Quevedo  
**Facultad:** Ciencias de la Computación  
**Carrera:** Software  
**Asignatura:** Aplicaciones Distribuidas  
**Actividad:** TA-IND-01  
**Estudiante:** Quintero Rico Luis David  
**Paralelo:** Séptimo nivel, paralelo B  
**Período académico:** 2026–2027
