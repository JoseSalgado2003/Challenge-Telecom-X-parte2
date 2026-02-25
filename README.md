# 🚀 Telecom X - Parte 2: Predicción de Cancelación de Clientes (Churn)

## 📌 Propósito del Proyecto
El objetivo principal de este proyecto es **predecir la cancelación (churn) de clientes** en la empresa de telecomunicaciones Telecom X. A través de la construcción de modelos de Machine Learning y el análisis de variables relevantes (como el tiempo de contrato y el gasto total), buscamos anticiparnos a la pérdida de clientes y proporcionar información estratégica para el desarrollo de campañas de retención efectivas.

## 📂 Estructura del Proyecto
El repositorio está organizado de la siguiente manera para facilitar su reproducibilidad:

* **`notebook_telecomX_parte2.ipynb`**: Cuaderno principal de Jupyter/Colab que contiene todo el código, desde el preprocesamiento hasta la evaluación de los modelos.
* **`datos_tratados.csv`**: Archivo CSV con el dataset limpio y procesado de la Fase 1, listo para el modelado predictivo.
* **`/visualizaciones`**: Carpeta que contiene las imágenes exportadas de los gráficos generados durante el análisis (matrices de confusión, importancia de variables, etc.).
* **`README.md`**: Este archivo con la documentación del proyecto.

## 🛠️ Proceso de Preparación de Datos
Para asegurar el correcto funcionamiento de los algoritmos de Machine Learning, los datos pasaron por un riguroso preprocesamiento:

1. **Clasificación de Variables:** Se identificaron y separaron las variables numéricas (como `Charges.Total` y `tenure`) de las categóricas (como `Contract` y `PaymentMethod`).
2. **Codificación (Encoding):** Se aplicó *One-Hot Encoding* (`pd.get_dummies`) para transformar las variables categóricas a un formato numérico binario, haciéndolas compatibles con los modelos predictivos.
3. **Manejo de Nulos:** Se eliminaron las filas con valores `NaN` para evitar errores en las fases de entrenamiento.
4. **Separación de Datos:** El dataset se dividió en dos conjuntos utilizando `train_test_split`: **80% para entrenamiento** y **20% para prueba**, utilizando estratificación (`stratify`) para mantener la proporción original de la variable objetivo.
5. **Balanceo de Clases:** Dado el desbalanceo natural del churn, se aplicó la técnica **SMOTE** (Synthetic Minority Over-sampling Technique) exclusivamente en los datos de entrenamiento.
6. **Normalización:** Se aplicó `StandardScaler` a los datos de entrenamiento para estandarizar las escalas de las variables numéricas.

## 🧠 Modelización: Decisiones y Justificaciones
Se entrenaron y compararon diferentes modelos, tomando decisiones arquitectónicas basadas en la naturaleza de cada algoritmo:

* **Regresión Logística:** Este modelo se alimentó con los datos **normalizados**. *Justificación:* Al basarse en la optimización de parámetros y el cálculo de coeficientes, la Regresión Logística es muy sensible a la magnitud de las variables; sin normalización, las variables con escalas mayores dominarían el modelo.
* **Random Forest:** Este modelo se entrenó con los datos **sin normalizar**. *Justificación:* Los algoritmos basados en árboles de decisión realizan particiones basadas en reglas (umbrales) sobre cada variable individualmente, por lo que son completamente inmunes a la escala de los datos.

## 📊 Insights del Análisis Exploratorio (EDA)
Durante el análisis dirigido previo al modelado, se descubrieron patrones clave:
* **Tiempo de Contrato vs Cancelación:** Los gráficos de caja (boxplots) revelaron que los clientes con un `tenure` (tiempo de retención) bajo tienen una probabilidad muchísimo mayor de cancelar el servicio. Los primeros meses son críticos.
* **Gasto Total:** Se observó que una facturación mensual alta en contratos de corto plazo es un fuerte detonante para el churn.
* **Importancia de Variables:** Según el modelo Random Forest, las variables que más influyen en la decisión de abandono son el tipo de contrato, la permanencia y los cargos totales.

## 💻 Instrucciones de Ejecución
Para reproducir este análisis en tu máquina local, sigue estos pasos:

1. **Clona el repositorio:**
   ```bash
   git clone [https://github.com/JoseSalgado2003/Challenge-Telecom-X-parte2.git]

2. **Instala las bibliotecas requeridas:**
    Asegúrate de tener instalado Python 3.x y ejecuta el siguiente comando para instalar las dependencias:
    Bash

    ```pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn

    Carga los datos:
    Verifica que el archivo datos_tratados.csv esté en el mismo directorio
    que el cuaderno, o ajusta la ruta en la celda de lectura:
    pd.read_csv('datos_tratados.csv').

    Ejecuta el cuaderno:
    Abre notebook_telecomX_parte2.ipynb en Jupyter Notebook, JupyterLab o
    Google Colab, y ejecuta las celdas secuencialmente.

Desarrollado por [José Salgado / JoseSalgado2003]
