# 🏊‍♂️ Swimming Pool Detection

Proyecto de visión por computador cuyo objetivo es **detectar piscinas en imágenes aéreas/satelitales**, combinando **métodos tradicionales de procesado de imagen (HSV, Canny, Mask, NDVI)** y **modelos de deep learning (YOLOv8 con Ultralytics)**.

---

## 👥 Autores

- Eric Rodríguez Merichal  
- Wenpeng Ji  
- Guillermo Vivancos Alonso

---

## 📂 Estructura del proyecto

### Archivos principales

- **`Swiming_pool_Detection.ipynb`**  
  Script principal del proyecto.  
  Compara las bounding boxes (bbox) detectadas por cada método y calcula el *accuracy* usando IoU (*Intersection over Union*).

- **`NDVI.py`**  
  Preprocesado de imágenes: elimina elementos irrelevantes y filtra por color para generar imágenes modificadas con el algoritmo NDVI.

- **`generate_proc_img.py`**  
  Genera imágenes preprocesadas usando NDVI.

- **`old_school.py`**  
  Contiene los algoritmos clásicos HSV+Canny y HSV+Mask.

- **`Verificar_DATASET.ipynb`**  
  Organiza y prepara la base de datos: convierte labels XML a TXT, clasifica imágenes con y sin piscina y reestructura las carpetas.

- **`Detect_video.ipynb`**  
  Detecta piscinas frame a frame en un vídeo y genera como salida `test_video_out.mp4`.

- **`make_video.ipynb`**  
  Convierte 300 imágenes del directorio `test_data_images` en un vídeo para poder realizar predicciones sobre él.

---

### Carga de labels / detecciones

- **`load_clasification`**  
  Carga los labels de la base de datos original.

- **`load_hsvANDcanny`**  
  Carga las bbox detectadas con HSV+Canny.  
  - Parámetro `preprocesado` (0 o 1): si es 1, aplica preprocesado antes de detectar.

- **`load_hsvMask`**  
  Carga las bbox detectadas con HSV+Mask.  
  - Parámetro `preprocesado` (0 o 1): si es 1, aplica preprocesado antes de detectar.

- **`load_ultralytics`**  
  Carga las bbox predichas por YOLOv8 entrenado con Ultralytics.  
  - Parámetro `epochs`: puede ser 10 o 100 (entrenamientos realizados).  
  - Parámetro `modificador`: `True` si se usan imágenes NDVI, `False` si son las originales.

---

### Entrenamiento y predicción con YOLOv8

- **`yolo_ultralytics.ipynb`**  
  Entrena YOLOv8 sobre imágenes normales (`DATABASE/ultralytics/images`) usando división en `train/test/val`.  
  Resultados en carpetas `10epoch_accuracy` y `100_epoch_accuracy`.

- **`yolo_ultralytics_modif.ipynb`**  
  Igual que el anterior, pero entrenando con imágenes modificadas (NDVI) en `DATABASE/ultralytics_modif/images`.

- **`yolo_ultralytics_pred.ipynb`**  
  Predice sobre todas las imágenes de test **sin labels**. Calcula la probabilidad media de acierto.  
  Usa `DATABASE/ultralytics_sin_accuracy/images` (train/val).  
  Resultados en `DATABASE/predictions_ultralytics`.

- **`yolo_ultralytics_pred_modif.ipynb`**  
  Versión NDVI del anterior.  
  Usa `DATABASE/ultralytics_sin_accuracy_modif/images`.  
  Resultados en `DATABASE/predictions_ultralytics_modif`.

---

## 📁 Estructura de carpetas

- **`DATABASE/`**  
  Contiene todas las bases de datos utilizadas (imágenes normales y NDVI, train/test/val).

- **`runs/`**  
  Resultados de los entrenamientos con Ultralytics.  
  - Los nombres terminados en `*Detect` → predicciones sobre test sin labels  
  - Los nombres terminados en `*Accuracy` → predicciones sobre test con labels
  - Contiene métricas como `results.jpg`, `precision-recall.jpg`, `labels.jpg`, `train_batch.jpg`, etc.

- **`ultralytics_trainings/`**  
  Histórico de todos los entrenamientos realizados con sus respectivas configuraciones.

---

## 📌 Notas importantes

- Las imágenes **modificadas** hacen referencia a las procesadas con **NDVI**.
- Se han comparado de forma sistemática los resultados de:
  - Algoritmos tradicionales (HSV+Canny / HSV+Mask)
  - Deep learning (YOLOv8 entrenado con imágenes normales vs NDVI)
- Las métricas de cada entrenamiento pueden consultarse en sus carpetas dentro de `runs/`.

---

## 🚀 Futuras mejoras

- Afinar hiperparámetros en YOLOv8.  
- Integrar validación cruzada.  
- Automatizar pipeline de preprocesado y predicción por lotes.

