# 🧠 Compresión Neuronal de Imágenes Adaptativa (TFG)

> **Trabajo de Fin de Grado**
>
> ** Representación adaptativa de imágenes para compresión escalable con redes neuronales **

Este repositorio contiene el código fuente, los modelos entrenados y los cuadernos de experimentación desarrollados durante el Trabajo de Fin de Grado.

El proyecto propone una modificación de la arquitectura **`cheng2020_anchor`** (implementada en **CompressAI**) para convertirla en un modelo **adaptativo, dinámico y escalable**, capaz de trabajar a múltiples tasas de compresión mediante un único modelo unificado.

Para ello se incorporan distintas técnicas de regularización y selección inteligente de canales latentes, entre ellas:

- 📊 Regularización por **Entropía de Energía**
- 🎯 Regularización **LASSO (Sparsity)**
- 🧠 **Data-Driven Latent Masking**, basado en un ranking empírico de importancia de los canales latentes

---

# 📂 Estructura del repositorio

```text
📦 TFG
│
├── 📂 datasets/
│
├── 📂 entrenamiento/
│   ├── Codigo_TFG_MSE.ipynb
│   ├── Codigo_TFG_MSE_H_S.ipynb
│   └── Codigo_TFG_MSE_H_S_DataDriven.ipynb
│
├── 📂 evaluacion/
│   ├── Modelo_Base.ipynb
│   └── Modelo_Ranking_Empírico.ipynb
│
├── 📂 modelos/
│   ├── CHENG2020_Q3_MSE_001_05.pth
│   ├── CHENG2020_Q3_MSE_0018_1.pth
│   ├── CHENG2020_Q3_MSE_0018_1_H_01_S_005.pth
│   ├── CHENG2020_Q3_MSE_0018_1_H_01_S_005_DataDriven.pth
│   ├── CHENG2020_Q3_MS-SSIM_2o4_12.pth
│   ├── CHENG2020_Q3_MS-SSIM_2o4_12_H_01_S_005.pth
│   ├── CHENG2020_Q3_MS-SSIM_2o4_12_H_01_S_005_DataDriven.pth
│   └── CHENG2020_Q3_MS-SSIM_5_130.pth
│
└── README.md
```

---

# 📁 Descripción de los directorios

## 📂 `datasets/`

Conjuntos de datos utilizados durante el proyecto.

Se utilizan los siguientes datasets:

- **DIV2K (High Resolution)** → entrenamiento y test (High Resolution Images de Train Data y Validation Data). Disponibles en: https://data.vision.ee.ethz.ch/cvl/DIV2K/

---

## 📂 `entrenamiento/`

Incluye todos los cuadernos utilizados durante el desarrollo del modelo, mostrando la evolución de la arquitectura.

### 📘 1. `Codigo_TFG_MSE.ipynb`

Implementación inicial basada en un descarte secuencial de canales latentes.

Características:

- Arquitectura base `cheng2020_anchor`
- Enmascaramiento secuencial
- Modelo estático

---

### 📘 2. `Codigo_TFG_MSE_H_S.ipynb`

Versión mejorada incorporando una función de pérdida personalizada.

Se añaden:

- Rate-Distortion Loss
- Regularización por Entropía de Energía
- Regularización LASSO (Sparsity)

---

### 📘 3. `Codigo_TFG_MSE_H_S_DataDriven.ipynb`

Versión definitiva presentada en el TFG.

Implementa:

- Extracción automática del ranking de importancia de los canales latentes
- Data-Driven Latent Masking
- Descarte dinámico asimétrico
- Entrenamiento del modelo adaptativo final

---

## 📂 `evaluacion/`

Cuadernos destinados a evaluar los modelos entrenados y generar las figuras incluidas en la memoria.

### 📙 `Modelo_Base.ipynb`

Permite:

- cargar modelos entrenados sin ranking
- visualizar reconstrucciones
- generar mapas de calor secuenciales
- comparar distintas tasas de compresión
- generación de curvas Rate-Distortion

---

### 📙 `Modelo_Ranking_Empírico.ipynb`

Incluye:

- cargar modelos entrenados con ranking
- visualizar reconstrucciones
- generar mapas de calor secuenciales
- comparar distintas tasas de compresión
- generación de curvas Rate-Distortion

---

## 📂 `pesos_modelos/`

Contiene los pesos entrenados utilizados durante el desarrollo del proyecto. Donde la nomenclatura del fichero es "CHENG_ANCHOR_Q3_XXXX", en el que las "XXXX", son los hiperparámetros usados.

-```

---

# 📦 Dependencias principales

- PyTorch
- Torchvision
- CompressAI
- NumPy
- Matplotlib
- ipywidgets

---

# 📊 Flujo del proyecto

```text
DIV2K
   │
   ▼
Entrenamiento Base -- Regularización (H + Sparsity) -- Data-Driven Masking
   │
   ▼
Modelo Final
   │
   ▼
Evaluación en DIV2K
```

---

# 🧠 Contribuciones científicas

Las principales aportaciones de este trabajo son:

- ✔️ Adaptación de una arquitectura de compresión neuronal de tasa fija a una arquitectura de tasa variable.
- ✔️ Desarrollo de un mecanismo de selección adaptativa de canales basado en estadísticas de activación.
- ✔️ Introducción de una función de pérdida con regularización espacial.
- ✔️ Implementación de un modelo unificado capaz de operar a múltiples niveles de compresión sin necesidad de entrenar una red independiente para cada tasa.

---

# 📄 Referencias

Este trabajo se basa principalmente en:

- Cheng, Zhengxue et al. **Learned Image Compression with Discretized Gaussian Mixture Likelihoods and Attention Modules (CVPR 2020).**
- CompressAI: A PyTorch Library and Evaluation Platform for End-to-End Compression Research.

---

# 👨‍🎓 Autor 

Alejandro Cheng Zhou


Grado en Ingeniería y Sistemas de Datos

Universidad Politécnica de Madrid

---

# 📜 Licencia

Este repositorio se publica con fines académicos como parte del Trabajo de Fin de Grado del autor.
