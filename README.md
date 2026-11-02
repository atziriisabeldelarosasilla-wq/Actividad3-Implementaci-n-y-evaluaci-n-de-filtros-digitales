[README.md](https://github.com/user-attachments/files/34293157/README.md)
# Implementación y evaluación de filtros digitales

**Actividad formativa 3 — Señales y Sistemas**
Universidad Ciudadana de Nuevo León

## Propósito

Este repositorio contiene el código en Python usado para diseñar y evaluar
tres filtros digitales (pasa bajos, pasa altos y pasa banda) aplicados a una
señal de prueba compuesta por varias frecuencias contaminada con ruido
blanco. El objetivo es comparar la señal antes y después del filtrado, tanto
en el dominio del tiempo como en el de la frecuencia, y analizar qué tan
efectivo es cada filtro para eliminar las componentes no deseadas.

## Contenido

```
filtros_digitales/
├── filtros_digitales.py     # script principal (comentado paso a paso)
├── figuras/                 # gráficas generadas al correr el script
│   ├── 01_senales_entrada.png
│   ├── 02_respuesta_frecuencia_filtros.png
│   ├── 03_comparacion_pasa_bajos.png
│   ├── 03_comparacion_pasa_altos.png
│   ├── 03_comparacion_pasa_banda.png
│   └── 04_resumen_comparacion.png
└── README.md
```

## ¿Qué hace el script?

1. **Definición de la señal de entrada**: genera ruido blanco y una señal
   compuesta por tres tonos senoidales (20 Hz, 150 Hz y 450 Hz) sumados y
   contaminados con ruido blanco gaussiano.
2. **Diseño de los filtros**:
   - **Pasa bajos** — IIR Butterworth, orden 4, frecuencia de corte 80 Hz.
   - **Pasa altos** — IIR Chebyshev tipo I, orden 4, rizo 1 dB, frecuencia
     de corte 250 Hz.
   - **Pasa banda** — FIR por método de ventana (Hamming), banda de paso
     100–250 Hz, 101 coeficientes.
3. **Aplicación de los filtros** a la señal ruidosa usando `scipy.signal.filtfilt`
   (filtrado de fase cero).
4. **Visualización de resultados**: gráficas de la señal antes/después en
   tiempo y frecuencia, respuesta en frecuencia (magnitud en dB) de cada
   filtro, y una métrica de reducción de energía como indicador de
   efectividad.

## Requisitos

- Python 3.9+
- `numpy`
- `scipy`
- `matplotlib`

Instalación:

```bash
pip install numpy scipy matplotlib
```

## Cómo correrlo

```bash
python filtros_digitales.py
```

Las gráficas se guardan automáticamente en la carpeta `figuras/`.

## Resultados (resumen)

| Filtro                                       | Reducción de energía de ruido |
|-----------------------------------------------|:------------------------------:|
| Pasa bajos (Butterworth, fc = 80 Hz)          | ≈ 59.5 % |
| Pasa altos (Chebyshev I, fc = 250 Hz)         | ≈ 75.1 % |
| Pasa banda (FIR Hamming, 100–250 Hz)          | ≈ 70.5 % |

El detalle del análisis se encuentra en el documento de la actividad
(`Actividad_formativa_3_Filtros_digitales.docx`).

## Autoría

Trabajo realizado como parte de la actividad "Implementación y evaluación
de filtros digitales" de la Universidad Ciudadana de Nuevo León.
