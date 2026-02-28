# Taller 1 - Deep Learning

## Descripción del Proyecto

Este proyecto implementa un modelo de clasificación de género de usuarios de Twitter utilizando técnicas de Deep Learning. El dataset utilizado proviene de Kaggle y contiene información de perfiles de Twitter etiquetados con su género (female, male, brand, unknown).

### Objetivos
- Realizar análisis exploratorio de datos (EDA) sobre el dataset de usuarios de Twitter
- Preprocesar y limpiar datos categóricos y numéricos
- Implementar un modelo de clasificación binaria (female vs male) usando redes neuronales
- Evaluar el desempeño del modelo usando métricas apropiadas

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
├── Taller1DL.ipynb       # Notebook principal con todo el análisis y modelo
├── pyproject.toml        # Configuración del proyecto y dependencias
├── README.md             # Este archivo
└── .venv/                # Entorno virtual (creado por uv sync)
```

## Uso

1. Abre `Taller1DL.ipynb` en Jupyter Lab
2. Ejecuta las celdas secuencialmente para:
   - Descargar el dataset desde Kaggle
   - Realizar análisis exploratorio
   - Preprocesar los datos
   - Entrenar el modelo de clasificación
   - Evaluar resultados

## Dependencias Principales

- **TensorFlow** 2.20.0 - Framework de Deep Learning
- **Scikit-learn** 1.8.0 - Preprocesamiento y métricas
- **Pandas** 3.0.1 - Manipulación de datos
- **NumPy** 2.4.2 - Operaciones numéricas
- **Matplotlib** 3.10.8 - Visualización
- **KaggleHub** 1.0.0 - Descarga de datasets
- **Jupyter Lab** 4.5.5 - Entorno de notebooks

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

## Notas

- El proyecto utiliza clasificación binaria (female vs male) por simplicidad
- Los datos se dividen en train/validation/test (60/20/20) con estratificación
- Se aplican técnicas de preprocesamiento como imputación, one-hot encoding y normalización
