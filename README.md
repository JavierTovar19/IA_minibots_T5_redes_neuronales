# IA_minibots_T5_redes_neuronales
## Ejercicios.
### 1. Con base en el programa Clase_NNA3, desarrolle dos redes neuronales con 2 capas oculta, una que aprenda a reconocer una compuerta NAND y la otra aprenda a reconocer una compuerta XOR.
### 2. Con base en la librería tensorflow, descargue el data set fashion MNIST. Haga una clasificación de prendas de vestir. Explique cada una de las funciones y las principales instrucciones, saque conclusiones.
### 3. Consiga un data set de cualquier tipo, puede ser de https://www.kaggle.com/datasets, estudie sus características (features) y su rótulo. Diseñe una red neuronal y haga ejemplos con base en los pesos aprendidos. 

Para trabajar en este punto, se uso primero un data set de fraudes en pagos digitales, el cual se descargo de kaggle. El cual presento variables irrelevantes para el estudio, tales como el ID del cliente y el id de la transacción, el ID del cliente podria ser relevante para el estudio si se contara con una cantidad masiva de datos, lo cual no es el caso, por lo que se descartaron. 

Por otra parte existen variables de tipo texto, las cuales se categorizan en variables discretas, con las cuales se puede trabajar directamente.

Por ultimo la variable objetivo es la que se desea predecir, en este caso se desea predecir si un pago es fraudulento o no en la columna **fraud_label**, el cual es un valor binario, 0 para no fraudulento y 1 para fraudulento.

Al entrenar el modelo, se observó una fuerte discrepancia en la distribución de clases: aproximadamente el 6.5% de las transacciones corresponden a fraude, mientras que el 93.5% restante son legítimas.

Este desbalance implica que un modelo puede obtener una alta exactitud simplemente clasificando todas las observaciones como "no fraude". Por ejemplo, un clasificador trivial que siempre prediga 0 alcanzaría una precisión cercana al 93.5%, sin detectar realmente los casos de fraude.

Este fenómeno evidencia que la métrica de accuracy no es adecuada en este contexto y que deben considerarse métricas como precision, recall, F1-score o AUC-ROC, especialmente enfocadas en la clase minoritaria.

Se intentaron estrategias de balanceo de datos; sin embargo, la reducción del conjunto mayoritario mediante submuestreo disminuye la cantidad total de información disponible y puede afectar la capacidad generalizadora del modelo. Esto contribuyó a que el desempeño final no fuera satisfactorio en este caso.

Debido a este problema, con una aproximación similar, se hizo un segundo intento con un dataset diferente, acerca de ataques al corazon, el cual se descargo de kaggle, este no presenta variables irrelevantes, las variables numericas son mapeadas por categorias numericas,y el objetivo es predecir si un ataque al corazon es fatal o no, el cual es un valor binario, 0 para no fatal y 1 para fatal.

El balance de datos en este dataset, es mucho mas optimo, ya que cerca del 50% de los datos son no fatales y el 50% son fatales, lo que es favorable para el entrenamiento del modelo.

En el archivo: [P3bien_heart_attack.ipynb](Codigo/P3bien_heart_attack.ipynb) se puede observar el proceso completo de preparación del dataset, construcción de la red neuronal y entrenamiento del modelo. El modelo alcanza una precisión cercana al 86%, lo que indica que aproximadamente 4 de cada 5 predicciones coinciden con la etiqueta real. No obstante, es importante complementar este análisis con otras métricas para evaluar el desempeño real del clasificador.

Por su parte, el archivo:

[P3mal_fraud_prediction.ipynb](Codigo/P3mal_fraud_prediction.ipynb)
documenta los intentos realizados para abordar el problema de detección de fraude y las limitaciones encontradas debido al fuerte desbalance de clases.