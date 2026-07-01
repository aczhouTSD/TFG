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
📦 TFG-Compresión-Adaptativa
│
├── 📂 datasets/
│   └── README_datasets.md
│
├── 📂 entrenamiento/
│   ├── 1_entrenamiento_basico.ipynb
│   ├── 2_entrenamiento_regularizado.ipynb
│   └── 3_entrenamiento_ranking_empirico.ipynb
│
├── 📂 evaluacion/
│   ├── 1_evaluar_sin_ranking.ipynb
│   └── 2_evaluar_con_ranking_y_medias.ipynb
│
├── 📂 pesos_modelos/
│   ├── modelo_secuencial_mse.pth
│   ├── modelo_adaptativo_final.pth
│   └── ranking_empirico.pt
│
├── requirements.txt
└── README.md
```

---

# 📁 Descripción de los directorios

## 📂 `datasets/`

Esta carpeta contiene las instrucciones necesarias para descargar los conjuntos de datos utilizados durante el proyecto.

Debido a las limitaciones de tamaño de GitHub, las imágenes originales no se incluyen en el repositorio.

Se utilizan los siguientes datasets:

- **DIV2K (High Resolution)** → entrenamiento y test.

---

## 📂 `entrenamiento/`

Incluye todos los cuadernos utilizados durante el desarrollo del modelo, mostrando la evolución de la arquitectura.

### 📘 1. `1_entrenamiento_basico.ipynb`

Implementación inicial basada en un descarte secuencial de canales latentes.

Características:

- Arquitectura base `cheng2020_anchor`
- Enmascaramiento secuencial
- Modelo estático

---

### 📘 2. `2_entrenamiento_regularizado.ipynb`

Versión mejorada incorporando una función de pérdida personalizada.

Se añaden:

- Rate-Distortion Loss
- Regularización por Entropía de Energía
- Regularización LASSO (Sparsity)

---

### 📘 3. `3_entrenamiento_ranking_empirico.ipynb`

Versión definitiva presentada en el TFG.

Implementa:

- Extracción automática del ranking de importancia de los canales latentes
- Data-Driven Latent Masking
- Descarte dinámico asimétrico
- Entrenamiento del modelo adaptativo final

---

## 📂 `evaluacion/`

Cuadernos destinados a evaluar los modelos entrenados y generar las figuras incluidas en la memoria.

### 📙 `1_evaluar_sin_ranking.ipynb`

Permite:

- cargar modelos entrenados
- visualizar reconstrucciones
- generar mapas de calor secuenciales
- comparar distintas tasas de compresión

---

### 📙 `2_evaluar_con_ranking_y_medias.ipynb`

Cuaderno definitivo de evaluación.

Incluye:

- carga del ranking empírico
- enmascaramiento adaptativo
- inyección de medias en canales inactivos
- cálculo correcto del bitrate
- visualización de mapas de calor adaptativos
- generación de curvas Rate-Distortion

---

## 📂 `pesos_modelos/`

Contiene los pesos entrenados utilizados durante el desarrollo del proyecto.

| Archivo | Descripción |
|---------|-------------|
| `modelo_secuencial_mse.pth` | Modelo entrenado mediante descarte secuencial |
| `modelo_adaptativo_final.pth` | Modelo adaptativo final presentado en el TFG |
| `ranking_empirico.pt` | Ranking estadístico de importancia de canales |


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
