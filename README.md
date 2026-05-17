# Evaluacion2_Prog_DS

Proyecto de Clasificación de Variedades de Frijol Seco
Integrantes

Cristian Romero
Javier Sagredo

Origen y descripción de los datos
Los datos utilizados provienen del Dry Bean Dataset del UCI Machine Learning Repository, donado en 2020 por investigadores turcos. El dataset contiene 13,611 registros de granos de frijol pertenecientes a 7 variedades distintas: Barbunya, Bombay, Cali, Dermason, Horoz, Seker y Sira.
Cada grano fue fotografiado y analizado mediante un sistema de visión computacional, extrayendo 16 características morfológicas (área, perímetro, longitud, redondez, compacidad, factores de forma, etc.). El target es la columna Class, que indica la variedad del grano.
El dataset se eligió por cumplir las condiciones óptimas para abordar tanto aprendizaje supervisado como no supervisado: tamaño suficiente, cero valores nulos, variables numéricas listas para modelado y separabilidad natural entre clases.
Justificación del entorno (Google Colab)
Se optó por Google Colab por las siguientes razones:

Acceso a recursos computacionales gratuitos – útil para entrenar SVM, Random Forest y XGBoost sin saturar el equipo local.
Almacenamiento en la nube – los datasets, modelos serializados (.pkl) y resultados se guardan directamente en Google Drive.
Colaboración en tiempo real – permite trabajar simultáneamente con el compañero sin conflictos de versiones, especialmente útil para coordinar las partes supervisado y no supervisado.
Sin configuración local – no requiere instalar scikit-learn, xgboost, optuna ni gestionar entornos virtuales.
Integración sencilla con GitHub – se puede abrir directamente cualquier notebook desde el repositorio público mediante el botón "Open in Colab", facilitando la revisión por parte del docente.

Estructura del proyecto
El proyecto está organizado en 6 notebooks que cubren el ciclo completo de machine learning:

01_análisis_exploratorio.ipynb – EDA completo: distribución de clases, histogramas, boxplots por clase, matriz de correlación y visualización PCA en 2 componentes principales.
02_aprendizaje_supervisado.ipynb – Implementación base de tres modelos supervisados (Árbol de Decisión, Regresión Logística, SVM lineal) con evaluación de métricas y verificación de overfitting.
03_aprendizaje_supervisado_optimizado.ipynb – Optimización de hiperparámetros con GridSearchCV en dos rondas, experimento de reducción de variables y comparación con modelos ensemble (Random Forest, XGBoost).
04_aprendizaje_no_supervisado.ipynb – Implementación base de tres modelos no supervisados (K-Means, Agrupamiento Jerárquico, DBSCAN) con métricas ARI, Silhouette y V-Measure.
05_aprendizaje_no_supervisado_optimizado.ipynb – Optimización mediante tres técnicas distintas: GridSearch, RandomSearch y Optuna para comparar la eficacia de cada método de búsqueda.
06_Análisis_final.ipynb – Integración de resultados, comparativa supervisado vs no supervisado, gráficos finales y conclusiones generales.

Los resultados intermedios se exportan como archivos .pkl en la carpeta Processed/ para mantener el flujo entre notebooks sin necesidad de re-entrenar.
Resultados clave

Calidad del dataset: 13,611 registros con 0 valores nulos, listo para modelado sin necesidad de limpieza.
Variables redundantes detectadas: 6 features con alta colinealidad (correlación >0.92), eliminadas sin pérdida de accuracy.
Modelo supervisado ganador: SVM con kernel RBF, C=30, gamma='scale' → Accuracy 92.69%, F1-Score 92.68%.
Modelo no supervisado ganador: Agrupamiento Jerárquico con GridSearch → ARI 0.7054, Silhouette 0.2738.
Comparación con modelos ensemble: Random Forest (92.32%) y XGBoost (92.40%) no superaron al SVM, confirmando que el techo práctico del dataset con algoritmos clásicos está en ~92.7%.
Conclusión técnica: Para este problema con etiquetas disponibles, el aprendizaje supervisado es la elección óptima. El no supervisado conserva valor para tareas exploratorias y descubrimiento de variedades no catalogadas.

Cómo ejecutar el proyecto

Abrir cualquiera de los notebooks en Google Colab mediante el botón "Open in Colab" al inicio del archivo.
Montar Google Drive cuando se solicite.
Asegurar que la ruta del archivo Dry_Bean_Dataset.xlsx sea correcta dentro de la carpeta Raw/ del Drive.
Ejecutar los notebooks en orden secuencial (01 → 06) para reproducir el flujo completo. Cada notebook carga los resultados del anterior desde archivos .pkl ubicados en Processed/.

Enlace al repositorio
https://github.com/javisagredo-dev/Evaluacion2_Prog_DS
