# Challenge Telecom X: Análisis de Evasión de Clientes (Churn)

## **Propósito del Análisis**
El objetivo principal de este proyecto es **predecir el churn (cancelación) de clientes** de una compañía de telecomunicaciones en función de variables relevantes, como antigüedad del cliente, tipo de servicios contratados, métodos de pago y comportamiento de consumo.  
Este análisis busca **identificar patrones que permitan reducir la fuga de clientes** y mejorar las estrategias de retención.

---

## **Estructura del Proyecto**
El proyecto se organiza de la siguiente forma:

```
📂 Challenge-Telecom-X/
 ├─ 📄 README.md               -> Documento principal con descripción del proyecto
 ├─ 📄 requirements.txt        -> Bibliotecas necesarias para ejecutar el análisis
 ├─ 📄 Challenge_Telecom_X.ipynb -> Cuaderno principal de Google Colab / Jupyter
 ├─ 📂 data/
 │   ├─ clientes_raw.csv       -> Datos crudos originales
 │   ├─ clientes_clean.csv     -> Datos tratados/listos para modelado
 ├─ 📂 eda/
 │   ├─ correlacion_variables.png
 │   ├─ distribucion_churn.png
 │   └─ importancia_variables.png
 └─ 📂 models/
     ├─ modelo_regresion.pkl
     ├─ modelo_arbol.pkl
     └─ modelo_bosque.pkl
```

---

## **Preparación de Datos**
1. **Clasificación de Variables**  
   - **Categóricas:** tipo de servicio (`PhoneService`, `InternetService`, `Contract`, `PaymentMethod`, `gender`)  
   - **Numéricas:** antigüedad (`tenure`), gasto mensual (`MonthlyCharges`), gasto total (`TotalCharges`), uso diario (`CuentasDiarias`)  

2. **Transformaciones Aplicadas**  
   - **Codificación de variables categóricas:** One-Hot Encoding  
   - **Normalización de variables numéricas:** StandardScaler para algoritmos sensibles a la escala  

3. **División de Datos**  
   - **Entrenamiento:** 80%  
   - **Prueba:** 20%  
   - Se utilizó `train_test_split` con `random_state` fijo para reproducibilidad  

4. **Justificación de decisiones**  
   - Se eligió **One-Hot Encoding** para convertir categorías en variables binarias sin asignar jerarquía.  
   - Se normalizaron las variables numéricas para mejorar la convergencia de modelos basados en distancia (como KNN) y estabilidad en regresión.  
   - Se separaron los datos para evitar **overfitting** y evaluar el modelo en datos nunca vistos.  

---

## **Análisis Exploratorio de Datos (EDA)**
Durante el EDA se realizaron:
- **Gráficos de distribución** de `tenure` y `TotalCharges` para diferenciar clientes que cancelan vs. permanecen.
- **Matriz de correlación** para identificar relaciones entre variables numéricas y churn.
- **Gráfico de importancia de variables** tras el entrenamiento de un bosque aleatorio.

Ejemplo de insights:
- Los clientes con **baja antigüedad y bajo gasto** son más propensos a cancelar.  
- Los métodos de pago automáticos están **asociados a menor churn**.

---

## **Instrucciones para Ejecutar el Cuaderno**

1. **Instalar dependencias**  
   Desde la terminal o Colab:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels
```

2. **Cargar los datos**  
   - Colocar los archivos CSV en la carpeta `data/`.  
   - Asegúrate de usar `clientes_clean.csv` para el modelado.

3. **Ejecutar el cuaderno**  
   - Abrir `Challenge_Telecom_X.ipynb` en Google Colab o Jupyter Notebook.  
   - Ejecutar las celdas secuencialmente, desde la preparación de datos hasta la evaluación de los modelos.

---

## **Modelos Incluidos**
- **Regresión Lineal (OLS)** para entender la relación de las variables con el churn.  
- **Árbol de Decisión** para segmentación de clientes.  
- **Bosque Aleatorio** para mejorar la precisión y recall en la predicción de churn.  
