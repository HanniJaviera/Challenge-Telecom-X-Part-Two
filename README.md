# Predicción de Churn en Telecom X - Fase de Modelado Predictivo

## 1. Descripción del Proyecto
Este repositorio contiene la segunda fase del análisis de datos para **Telecom X**. El objetivo central es el desarrollo, entrenamiento y evaluación de modelos de Machine Learning para predecir la cancelación de servicios (*churn*). Mediante la identificación de patrones de comportamiento, se busca proporcionar a la empresa herramientas accionables para reducir la pérdida de clientes.

---

## 2. Metodología de Preparación de Datos
Para asegurar la integridad y el rendimiento de los modelos, se realizaron los siguientes pasos de preprocesamiento:

* **Encoding:** Transformación de variables categóricas mediante *One-Hot Encoding*.
* **Balanceo de Clases:** Aplicación de la técnica **SMOTE** (*Synthetic Minority Over-sampling Technique*) para equilibrar la muestra de entrenamiento, evitando sesgos hacia la clase mayoritaria.
* **Escalamiento:** Uso de *StandardScaler* para normalizar las características en modelos sensibles a la magnitud de los datos.

---

## 3. Justificación de Modelos Seleccionados

### Modelo A: Regresión Logística
**Justificación:** Este modelo requiere normalización de datos debido a que utiliza una función sigmoide para el cálculo de probabilidades. Sin el escalamiento, variables con rangos numéricos elevados (como Cargos Totales) dominarían de forma desproporcionada sobre variables binarias (como Adulto Mayor), sesgando los coeficientes y la importancia real de cada factor.

### Modelo B: Random Forest
**Justificación:** Al ser un conjunto de árboles de decisión que realizan particiones basadas en umbrales (ej. ¿es el cargo > 50?), la magnitud absoluta de los datos no afecta la lógica de la división. Es un modelo robusto que no requiere normalización previa, permitiendo capturar relaciones no lineales complejas entre las variables.

---

## 4. Análisis de los Principales Predictores
Tras la evaluación de la importancia de las variables en ambos modelos, se identificaron los siguientes hallazgos críticos:

1. **Factor de Antigüedad:** La variable `Meses_Antiguedad` es el predictor más relevante. Los clientes nuevos presentan el mayor riesgo de fuga; la probabilidad de cancelación disminuye drásticamente a medida que aumenta el tiempo de permanencia.
2. **Sensibilidad al Costo:** Existe una alta correlación entre los cargos mensuales elevados y la intención de abandono. El cliente de Telecom X demuestra ser altamente sensible a la carga financiera del servicio.
3. **Riesgo en Fibra Óptica:** Se detectó un patrón de riesgo específico en usuarios de este servicio, sugiriendo la necesidad de auditar la relación calidad-precio o la estabilidad técnica de dicha tecnología.
4. **Métodos de Pago y Contratos:** El uso de `Electronic Check` se asocia a una mayor volatilidad, mientras que los contratos a largo plazo (1 y 2 años) actúan como una herramienta efectiva de retención.

---

## 5. Evaluación del Desempeño

| Métrica | Regresión Logística | Random Forest |
| :--- | :---: | :---: |
| Exactitud (Accuracy) | 0.7871 | 0.7935 |
| **Recall (Sensibilidad)** | 0.3262 | **0.4626** |
| F1-Score | 0.4485 | 0.
