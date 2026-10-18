# Avances del Tec Integrador — Equipo 32

Proyecto académico de preparación de datos para un sistema de conteo de productos veterinarios mediante visión por computadora.

## Entregables

- **Avance 1 — Análisis exploratorio:** auditoría del export de segmentación disponible para el primer avance (60 imágenes anotadas, 60 instancias y 9 clases con ejemplos).
- **Avance 2 — Ingeniería de características:** análisis de 282 fotografías actuales; se calculan descriptores globales de geometría, color, iluminación y textura, se transforman y escalan variables, se filtra redundancia y se resume la variación con PCA.

- **Avance 3 — Baseline:** modelo de referencia para identificar el producto de cada caja (676 recortes anotados en 44 fotos, 44 clases) y propagarlo al conteo por producto. Compara referencias triviales, regresión logística y bosque aleatorio sobre 92 características por objeto (color, distribución de color, forma y textura), con validación cruzada agrupada por foto, análisis de sub/sobreajuste, importancia de características (filtro, embebido, envoltura, permutación y PCA) y metas de desempeño. En una prueba fija de 10 fotos el baseline alcanza macro-F1 de 0.169; en validación cruzada, 0.349 ± 0.067 (azar: 0.017). Identifica la marca el 92.5 % de las veces pero el producto exacto solo el 42.8 %, así que sirve como piso y no como solución.

Los notebooks incluyen sus resultados ejecutados. El Avance 2 se basa en la colección de fotos actualizada. Las fotografías actuales no traen etiquetas YOLO asociadas en esta carpeta, así que sus características describen la calidad visual y no sustituyen las cajas o máscaras requeridas para entrenar un detector.

## Datos y privacidad

El repositorio contiene los notebooks, no los archivos de fotografía ni el export de etiquetas. Las imágenes de producto pueden mostrar códigos de lote y caducidad. En la copia pública del Avance 1 se omitió la salida que incrustaba fotos y se retiró la ruta local del conjunto anotado.

El Avance 3 incrusta en sus salidas, por pedido del equipo, fotografías de referencia y ejemplos de recortes **en baja resolución** (mosaicos JPEG reducidos y miniaturas de ≤ 120 px) para ilustrar el caso de uso; no se publican los archivos originales de foto ni las exportaciones de Label Studio.

## Reproducción

Instala las dependencias de `requirements.txt` y ejecuta las celdas en orden desde la raíz del proyecto.

- Para **Avance 1**, coloca localmente el export YOLO con `data.yaml`, `images/` y `labels/` en una carpeta `vetlife-yolo-local-20260929051531/`, junto al notebook. En Google Colab también puedes cargar el ZIP cuando el notebook lo solicite.
- Para **Avance 2**, coloca la carpeta de imágenes JPG convertidas en `imagenes_jpg/`, junto a los notebooks. Esos archivos no se distribuyen en este repositorio.

- Para **Avance 3**, coloca localmente `label_data/` (fotos anotadas), la carpeta `Zproyect_Main/01_datos/exportaciones_label_studio/` (una subcarpeta con fecha por exportación de Label Studio) y, opcionalmente, `Zproyect_Main/Fotos_de_referencia/`, junto al notebook o en su carpeta padre. El notebook las busca solo. Se ejecuta de principio a fin y deja la lista de fotos de prueba en `avance3_fotos_prueba.csv` para reutilizar la misma partición en los siguientes modelos.

Requisitos sugeridos: Python 3.10 o posterior. No se debe ajustar PCA, escaladores o transformaciones con datos de validación/prueba en una evaluación predictiva; se ajustan sólo con entrenamiento.
