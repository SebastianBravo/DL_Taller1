# Taller 1 - Deep Learning

## Autores

- **María Camila Cuéllar Avella** maria-cuellara@javeriana.edu.co 
- **Oscar Daniel Cagua Cuadros** cagua-oscar@javeriana.edu.co  
- **Juan Navas** navas.juans@javeriana.edu.co 
- **Juan Sebastián Bravo** bravos.js@javeriana.edu.co  

## Descripción del Proyecto

Este proyecto implementa un modelo de clasificación de género de usuarios de Twitter utilizando técnicas de Deep Learning. El dataset utilizado proviene de Kaggle y contiene información de perfiles de Twitter etiquetados con su género (female, male, brand, unknown).

## Inicio Rápido

```bash
# 1. Instalar uv (gestor de paquetes)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# 2. Clonar o navegar al proyecto
cd DL_Taller1

# 3. Sincronizar dependencias
uv sync

# 4. Activar entorno virtual
.venv\Scripts\Activate.ps1

# 5. Iniciar Jupyter Lab
jupyter lab
```

Abre `Taller1DL.ipynb` y ejecuta las celdas secuencialmente.

### Objetivos
- Realizar análisis exploratorio de datos (EDA) sobre el dataset de usuarios de Twitter
- Preprocesar y limpiar datos categóricos y numéricos
- Implementar diferentes arquitecturas de redes neuronales para clasificación binaria (female vs male)
- Comparar el desempeño de modelos con diferentes niveles de complejidad
- Evaluar y visualizar las métricas de clasificación

### Dataset
- **Fuente**: [Twitter User Gender Classification](https://www.kaggle.com/crowdflower/twitter-user-gender-classification)
- **Características**: Información de perfiles de Twitter incluyendo descripción, ubicación, colores del perfil, etc.
- **Target**: Variable `gender` con clases female, male, brand, unknown

## Requisitos Previos

- Python 3.13 o superior
- [uv](https://github.com/astral-sh/uv) - Gestor de paquetes de Python ultrarrápido

## Instalación y Configuración

### 1. Instalar uv (si no lo tienes)

**Windows (PowerShell):**
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**macOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### 2. Sincronizar dependencias con uv

Una vez instalado uv, sincroniza todas las dependencias del proyecto:

```bash
uv sync
```

Este comando:
- Crea automáticamente un entorno virtual en `.venv`
- Instala todas las dependencias especificadas en `pyproject.toml`
- Asegura que las versiones de los paquetes sean consistentes

### 3. Activar el entorno virtual

**Windows (PowerShell):**
```powershell
.venv\Scripts\Activate.ps1
```

**Windows (CMD):**
```cmd
.venv\Scripts\activate.bat
```

**macOS/Linux:**
```bash
source .venv/bin/activate
```

### 4. Ejecutar Jupyter Notebook

Con el entorno virtual activado:

```bash
jupyter lab
```

O directamente con uv:

```bash
uv run jupyter lab
```

## Estructura del Proyecto

```
DL_Taller1/
├── Taller1DL.ipynb              # Notebook principal: EDA, preprocesamiento y modelo MLP 2 capas
├── Perceptron_Unicapa.ipynb     # Notebook especializado: Perceptron unicapa
├── MLP_1_Capa_Oculta.ipynb      # Notebook especializado: MLP con 1 capas oculta
├── MLP_2_Capas_Ocultas.ipynb    # Notebook especializado: MLP con 2 capas ocultas
├── preprocessed_data/           # Datos preprocesados (.npy)
│   ├── X_train.npy
│   ├── X_val.npy
│   ├── X_test.npy
│   ├── y_train.npy
│   ├── y_val.npy
│   └── y_test.npy
├── preprocessor.joblib          # Pipeline de preprocesamiento guardado
├── pyproject.toml               # Configuración del proyecto y dependencias
├── README.md                    # Este archivo
└── .venv/                       # Entorno virtual (creado por uv sync)
```

## Arquitecturas de Modelos Implementadas

### 1. Perceptrón Unicapa
- Una única capa de salida con función escalón (TLU)
- Limitado a problemas linealmente separables

### 2. MLP con 1 Capa Oculta
- Capa oculta con número de neuronas igual al número de entradas
- Función de activación ReLU en capa oculta
- Función de activación Sigmoid en capa de salida

### 3. MLP con 2 Capas Ocultas
- Primera capa oculta: n/2 neuronas (mitad de las entradas)
- Segunda capa oculta: n/2 neuronas (igual que la primera)
- Ambas capas ocultas con ReLU
- Capa de salida con Sigmoid para clasificación binaria

## Uso

### Workflow Completo (Taller1DL.ipynb)

1. Abre `Taller1DL.ipynb` en Jupyter Lab
2. Ejecuta las celdas secuencialmente para:
   - **Sección 1**: Descargar el dataset desde Kaggle con KaggleHub
   - **Sección 2**: Realizar análisis exploratorio con gráficos y correlaciones
   - **Sección 3**: Seleccionar variables y limpiar datos
   - **Sección 4-5**: Preprocesar datos (imputación, one-hot, escalado) y particionar (60/20/20)
   - **Sección 6**: Entrenar modelos
   - Evaluar resultados con métricas y matriz de confusión

## Dependencias Principales

- **TensorFlow** 2.20.0 - Framework de Deep Learning
- **Keras** - API de alto nivel para construcción de redes neuronales
- **Scikit-learn** 1.8.0 - Preprocesamiento, particionamiento y métricas
- **Pandas** 3.0.1 - Manipulación de datos
- **NumPy** 2.4.2 - Operaciones numéricas
- **Matplotlib** 3.10.8 - Visualización de gráficos
- **Seaborn** - Visualización estadística avanzada
- **KaggleHub** 1.0.0 - Descarga de datasets desde Kaggle
- **Jupyter Lab** 4.5.5 - Entorno de notebooks interactivos
- **Joblib** 1.5.3 - Serialización de objetos Python

## Comandos Útiles con uv

```bash
# Agregar una nueva dependencia
uv add nombre-paquete

# Remover una dependencia
uv remove nombre-paquete

# Actualizar todas las dependencias
uv sync --upgrade

# Ejecutar un comando en el entorno virtual sin activarlo
uv run python script.py
```

## Notas Técnicas

### Preprocesamiento
- **Particionamiento**: Train/Validation/Test (60/20/20) con estratificación
- **Variables numéricas**: Imputación con mediana + StandardScaler
- **Variables categóricas**: Imputación con moda + OneHotEncoder
- **Data leakage**: El preprocesador se ajusta solo con datos de entrenamiento

### Configuración del Modelo MLP con 2 Capas Ocultas
- **Optimizador**: Adam (tasa de aprendizaje adaptativa)
- **Función de pérdida**: Binary Crossentropy
- **Épocas**: 100
- **Batch size**: 32
- **Activación capas ocultas**: ReLU
- **Activación salida**: Sigmoid
- **Umbral de decisión**: 0.5

### Métricas de Evaluación
- Accuracy (exactitud general)
- Precision (precisión por clase)
- Recall (sensibilidad/exhaustividad)
- F1-Score (media armónica de precision y recall)
- Matriz de confusión

### Clasificación Binaria
El proyecto se enfoca en clasificación binaria (female vs male), descartando las clases "brand" y "unknown" del dataset original para simplificar el problema y permitir el uso de una arquitectura con una neurona de salida y activación sigmoide.