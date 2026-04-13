# Taller 3: Exploratory Data Analysis & Data Wrangling — Instacart

Análisis exploratorio completo sobre el dataset público de Instacart, desarrollado como parte del programa de Maestría en Fundamentos de Data Science. El proyecto cubre auditoría de calidad de datos, construcción de un One Big Table (OBT) y análisis multivariado de negocio.

---

## Contenido del repositorio

```
workshop-3/
├── taller_3_Manuel_Pillapa.ipynb   # Notebook principal con todo el análisis
├── datos/
│   ├── instacart_orders.csv        # Pedidos por usuario
│   ├── order_products.csv          # Productos por pedido
│   ├── products.csv                # Catálogo de productos
│   ├── aisles.csv                  # Pasillos de supermercado
│   └── departments.csv             # Departamentos
└── README.md
```

---

## Estructura del análisis

### Paso 1 — Exploración Inicial
Radiografía de las 5 tablas: dimensiones, tipos de datos, distribuciones y primeros hallazgos estadísticos.

### Paso 2 — Auditoría de Calidad de Datos (4 dimensiones)
- **2.1 Precisión:** Detección y eliminación de duplicados explícitos e implícitos en `orders`.
- **2.2 Completitud:** Tratamiento de valores nulos — nulos estructurales (MNAR) en `days_since_prior_order`, sentinela -1 en `add_to_cart_order`, imputación en `product_name`.
- **2.3 Sensibilidad:** Análisis de outliers con regla IQR de Tukey sobre tiempos de espera entre pedidos.

### Paso 3 — Data Wrangling & One Big Table (OBT)
Construcción de una tabla desnormalizada mediante left joins secuenciales de las 5 tablas, validada con assert de integridad de filas.

### Paso 4 — Análisis Multivariado de Negocio

**Grupo A — Preguntas Esenciales**
- A1: Heatmap de demanda por día y hora de la semana
- A2: Distribución de días entre recompras (ciclos de 7, 14, 30 días)

**Grupo B — Profundización**
- B1: Retención y recurrencia — distribución de pedidos por usuario
- B2: Top 20 productos más vendidos y su ratio de recompra (Principio de Pareto)

**Grupo C — Patrones de Causalidad**
- C1: Tamaño de la canasta comercial — media, curtosis y distribución
- C2: Correlación Spearman/Pearson entre posición #1 en carrito y fidelidad
- C3: Proporción de recompras por producto
- C4: Proporción de recompras por usuario
- C5: Top 20 productos elegidos primero al armar el carrito

---

## Principales hallazgos

- La demanda se concentra **domingos y lunes entre 9am–16h**, con ciclos de recompra dominantes a los 7, 14 y 30 días.
- El negocio está sostenido por un núcleo de **productos frescos** (frutas, verduras, lácteos) con ratios de recompra superiores a **0.85**.
- La canasta promedio es de **10 artículos**, con distribución leptocúrtica (curtosis = 4.13) lo que indica que la mayoría de pedidos son pequeños y hay una cola de pedidos grandes.
- Correlación Spearman **r = 0.85** entre poner un producto primero en el carrito y su tasa de recompra global, el primer ítem es un predictor de fidelidad.
- El **54% de los productos** comprados por usuario son recompras, con un 25% de usuarios superando ratio 0.72 de fidelidad.

---

## Cómo ejecutar el proyecto

### 1. Clonar el repositorio
```bash
git clone https://github.com/tu-usuario/workshop-3.git
cd workshop-3
```

### 2. Instalar dependencias
```bash
pip install pandas numpy scipy matplotlib jupyter
```

### 3. Abrir el notebook
```bash
jupyter notebook taller_3_Manuel_Pillapa.ipynb
```

### 4. Ejecutar las celdas
Ejecutar en orden desde la primera celda. Las celdas de carga de datos asumen que los archivos CSV están en la carpeta `datos/`.

---

## Stack tecnológico

- Python 3.13
- pandas · numpy · scipy · matplotlib

---

## Autor

**Manuel Pillapa**  
Maestría en Fundamentos de Data Science
