# Avances del Tec Integrador — Equipo 32

Proyecto académico de preparación de datos para un sistema de conteo de productos veterinarios mediante visión por computadora.

## Entregables

- **Avance 1 — Análisis exploratorio:** auditoría del export de segmentación disponible para el primer avance (60 imágenes anotadas, 60 instancias y 9 clases con ejemplos).
- **Avance 2 — Ingeniería de características:** análisis de 282 fotografías actuales; se calculan descriptores globales de geometría, color, iluminación y textura, se transforman y escalan variables, se filtra redundancia y se resume la variación con PCA.

Los notebooks incluyen sus resultados ejecutados. El Avance 2 se basa en la colección de fotos actualizada. Las fotografías actuales no traen etiquetas YOLO asociadas en esta carpeta, así que sus características describen la calidad visual y no sustituyen las cajas o máscaras requeridas para entrenar un detector.

## Datos y privacidad

El repositorio contiene los notebooks, no las fotografías ni el export de etiquetas. Las imágenes de producto pueden mostrar códigos de lote y caducidad. En la copia pública del Avance 1 se omitió la salida que incrustaba fotos y se retiró la ruta local del conjunto anotado.

## Reproducción

Instala las dependencias de `requirements.txt` y ejecuta las celdas en orden desde la raíz del proyecto.

- Para **Avance 1**, coloca localmente el export YOLO con `data.yaml`, `images/` y `labels/` en una carpeta `vetlife-yolo-local-20260929051531/`, junto al notebook. En Google Colab también puedes cargar el ZIP cuando el notebook lo solicite.
- Para **Avance 2**, coloca la carpeta de imágenes JPG convertidas en `imagenes_jpg/`, junto a los notebooks. Esos archivos no se distribuyen en este repositorio.

Requisitos sugeridos: Python 3.10 o posterior. No se debe ajustar PCA, escaladores o transformaciones con datos de validación/prueba en una evaluación predictiva; se ajustan sólo con entrenamiento.
