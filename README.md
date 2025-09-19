# 🏊‍♂️ Swimming Pool Detection

Detección de piscinas en imágenes aéreas y satelitales mediante técnicas clásicas de visión por computador (HSV, Canny, NDVI) y modelos de deep learning (YOLOv8 con Ultralytics).

Proyecto colaborativo desarrollado como parte de la asignatura de Visión por Computador.

---

## 👥 Autores
- Eric Rodríguez Merichal  
- Wenpeng Ji  
- Guillermo Vivancos Alonso

---

## 📌 Descripción

- Procesado de imágenes con NDVI para eliminar obstáculos visuales y resaltar piscinas.  
- Implementación de detectores clásicos (HSV+Canny, HSV+Mask).  
- Entrenamiento de YOLOv8 sobre imágenes normales y procesadas (NDVI).  
- Comparación de resultados mediante IoU y métricas de precisión/recall.  
- Pruebas en imágenes, lotes de datos y vídeos.

---

## 📁 Contenido del proyecto completo

- Notebooks de entrenamiento y predicción (`yolo_ultralytics*.ipynb`)
- Scripts de preprocesado (`NDVI.py`, `generate_proc_img.py`, `old_school.py`)
- Scripts de clasificación y verificación de datasets
- Resultados de los entrenamientos en `runs/`
- Bases de datos en `DATABASE/`

⚠️ Debido al gran tamaño de los datos y modelos entrenados, este repositorio no incluye todos los archivos.

---

## 📎 Repositorio completo

🔗 [Ver el repositorio original completo en GitHub](https://github.com/tu-otro-usuario/Swimming_Pool_Detection)

Aquí encontrarás:
- Todo el código fuente
- Los notebooks completos
- Las bases de datos usadas
- Los modelos entrenados y métricas de evaluación

---

## 🚀 Tecnologías
- Python 3  
- OpenCV  
- Ultralytics (YOLOv8)  
- NumPy · Pandas · Matplotlib
