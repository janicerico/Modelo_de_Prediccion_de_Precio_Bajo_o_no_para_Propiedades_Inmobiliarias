## <h1 align=center> Proyecto Individual No. 2. Machine Learning
## <h1 align=center> Etapa de LABs - Carrera: Data Science

<p align="center">
<img src=https://user-images.githubusercontent.com/109157476/213493684-d39b7139-403c-4dac-873f-2505d3ec7fd9.png>

# <h1 align=center> Por: Janice Rico

<p align="center">
<img src=https://user-images.githubusercontent.com/109157476/214588778-c726ed0a-2188-4d95-a010-bcb7fdb784ac.png>

## <h1 align=center> TEMA:
# <h1 align=center> Modelo de Predicción de Precio Bajo o no, para Propiedades Inmobiliarias.
  
  ## <h1 align=center> INTRODUCCIÓN
 
Como parte del área de Machine Learning, una empresa inversora en bienes raíces solicitó un modelado que permita predecir si un inmueble tiene un precio Bajo o no, de acuerdo a diferentes variables como la ubicación y los diferentes servicios con los que cuenta, ya que como es muy bien sabido, estos valores se encuentran en constante cambio por múltiples factores que los afectan. Se desea detectar buenas oportunidades de inversión que llevarán posteriormente a mayor desarrollo inmobiliario, y por ende social.

## <h1 align=center> DATOS
 
2 tablas en formato parquet correspondientes a los datos para realizar el entrenamiento (22 columnas) y los datos para realizar el testeo y predicción (21 columnas).

Dichas tablas se encuentras alojadas en el siguiente drive: https://drive.google.com/drive/folders/1-CepGNc6QMT1Ppq_z0N6BNvY2vsuVd_n?usp=share_link
  
## <h1 align=center> TRANSFORMACIONES REQUERIDAS (Procesos de EDA y ETL)

Antes de trabajar en los entrenamientos y prueba, los datos fueron sometidos a un proceso de Observación, Estudio y Transformación, logrando de esta manera contar con datasets lo más aptos y originales posible, para los posteriores usos. Todo se hizo en el entorno de Python, utilizando librerías como pandas, numpy, matplotlib,  geopandas y sklearn.
  
Para ello se eliminaron columnas que no aportaban información tan relevante a la hora de entrenar el modelo, así como la eliminación de datos nulos. Del mismo modo, a partir de la columna "price", se generó una columna "is_low", para denotar si una propiedad tenía un precio bajo o no. Y por último, Las columnas que eran de tipo string se llevaron a un tipo de dato numérico para poder trabajar con el modelo.
  
Todas estas transformaciones están detalladas en el cuaderno de Jupyter: **"ETL, Machine Learning Model and Prediction.ipynb"**.

## <h1 align=center> MODELO DE MACHINE LEARNING UTILIZADO: Aprendizaje Supervisado - Regresión Logística

Se escogió este modelo de Regresión Logística, ya que es un método estadístico especializado en resolver problemas de clasificación binaria, es decir, donde se espera un resultado que sólo toma dos valores. En el caso de las propiedades en venta, sólo se quería saber si el precio era bajo o no. Se utilizó el hiperparámetro "solver='lbfgs'" (), porque es el más usado en datasets que no son tan grandes, y como máximas iteraciones necesarias para que los solvers converjan, 10000.

Inicialmente el dataset de train se dividió a su vez en train y test, para entrenar el modelo y luego hacer la predicción con parte del mismo (30%). Una vez obtenida una accurary (0.65) y un recall (0.61) aceptables, se procedió a realizar la predicción con el dataset original para testeo, dando como resultado una columna "pred" con ceros y unos, donde "is_low=1" pertecenecía a un rango de precios bajos, y "is_low=0" no pertenecía.
  
Esa columna "pred" se convirtió en una serie y se exportó a un archivo .csv sin índice (**janicerico.csv**).
