# 🌳 Detección y Conteo de Árboles con YOLOv8

Este proyecto implementa un sistema para **entrenar un modelo YOLOv8 personalizado** y usarlo para **identificar y contar árboles en imágenes satelitales**. Fue desarrollado y validado en **Google Colab**, por lo que **se recomienda ejecutar todo el flujo en dicha plataforma** para evitar errores relacionados con rutas o instalación de bibliotecas.

---

## Requisitos

- Google Colab (recomendado)
- Alternativamente: Python 3.8+ si se ejecuta localmente (ver advertencias abajo)

---

## Flujo general del proyecto

### 1. Entrenamiento del modelo

1. Abre el notebook de entrenamiento en Google Colab **"Training/train_yolov8_trees_detection.ipyn"**.
2. **Sube el archivo `.zip` del dataset** al entorno de Colab.
   - Este `.zip` debe tener en alguna de sus carpetas la estructura esperada por YOLOv8:
     ```
     dataset.zip
     ├── train/
     │   ├── images/
     │   ├── labels/
     ├── test/
     │   ├── images/
     │   ├── labels/
     └── valid/
         ├── images/
         ├── labels/
     ```
3. Siguiendo el notebook se descomprime el dataset y se configura el archivo `data.yaml`.
4. Se entrena el modelo YOLOv8 con las clases (En este caso `tree`).
5. Al finalizar, se genera un archivo de pesos llamado `best.pt` en: **runs/detect/train/weights/best.pt**
6. Este archivo se **comprime**, ya que será utilizado en el siguiente notebook.

### 2. Identificación y Conteo de Árboles
1. Abre el notebook **Identification_and_Counting/detect_and_count_trees** de inferencia en Colab.
2. Sube los siguientes archivos al entorno:
   - **weights.zip**: pesos del modelo entrenado**
   - Imagen satelital en la que se desea realizar la detección (por ejemplo: **test_images/trees2.jpg**)
3. Siguiendo el notebook se descomprime el archivo de pesos:
4. Se carga el modelo entrenado (`best.pt`), se hace la detección en la imagen cargada y se visualiza:
   - Bounding boxes
   - Etiquetas con confianza
   - Conteo total de árboles detectados
  
![Detección en acción](media/deteccion.gif)

---
## ⚠️ Consideraciones si se quiere usar el proyecto localmente
- La instalación de bibliotecas no es automática como en Colab. Debes instalar manualmente.
- Las rutas a archivos del codigo pueden diferir. Se debe de adaptar el código para que las rutas funcionen correctamente en el sistema operativo.

Algunos notebooks usan %matplotlib inline, que solo funciona en entornos tipo notebook/Jupyter.

---

## Créditos
Este proyecto fue desarrollado como parte del curso Proyecto de Aplicación de la Ingeniería en Computadores del Tecnológico de Costa Rica.
Combina herramientas de visión por computadora e inteligencia artificial para abordar un problema ambiental de alto valor: la **Identificación y Conteo de Árboles a partir de Fotografías Satelitales para Estimación de Biomasa**
