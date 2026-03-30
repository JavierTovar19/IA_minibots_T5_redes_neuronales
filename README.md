# IA_minibots_T5_redes_neuronales
## Ejercicios.
### 1. Con base en el programa Clase_NNA3, desarrolle dos redes neuronales con 2 capas oculta, una que aprenda a reconocer una compuerta NAND y la otra aprenda a reconocer una compuerta XOR.

El código [P1_red neuronal.ipynb](Codigo/P1_red_neuronal.ipynb) desarrolla una red neuronal tipo feedforward con dos capas ocultas para que pueda aprender las compuertas lógicas NAND o XOR utilizando aprendizaje supervisado y el algoritmo de backpropagation. Primero se define la función sigmoide y su derivada, ya que esta función introduce la no linealidad necesaria para que la red pueda resolver problemas como XOR y además permite calcular los gradientes durante el entrenamiento.

Luego se construye la matriz de entradas X con las cuatro combinaciones binarias posibles y el vector Y con los valores esperados según la compuerta que se quiera aprender. Después se inicializan de forma aleatoria los pesos y los sesgos de cada capa. En cada iteración (época) se realiza la propagación hacia adelante, donde se calculan los valores Z y las activaciones A aplicando la ecuación matricial y la función sigmoide en cada capa. A continuación, se calcula el error comparando la salida obtenida con la salida esperada, y ese error se propaga hacia atrás usando la regla de la cadena para ajustar los pesos mediante descenso del gradiente con una tasa de aprendizaje η. 

Este proceso se repite durante 10000 épocas hasta que la red logra aprender correctamente la función lógica, demostrando que una red con varias capas sí puede resolver problemas que no son linealmente separables, como el caso de XOR.


### 2. Con base en la librería tensorflow, descargue el data set fashion MNIST. Haga una clasificación de prendas de vestir. Explique cada una de las funciones y las principales instrucciones, saque conclusiones.

El modelo desarrollado utilizando TensorFlow y Keras permitió clasificar imágenes del dataset Fashion MNIST con una buena precisión. La normalización de los datos mejoró el rendimiento del entrenamiento, mientras que el uso de capas densas con funciones de activación ReLU facilitó la extracción de características relevantes.

El optimizador Adam demostró ser eficiente para ajustar los pesos del modelo, logrando una convergencia rápida. Además, la función de pérdida utilizada fue adecuada para problemas de clasificación multiclase.

Finalmente, el modelo alcanzó una precisión considerable en el conjunto de prueba, lo que indica que es capaz de generalizar correctamente sobre datos no vistos. Sin embargo, el rendimiento podría mejorarse utilizando técnicas más avanzadas como redes convolucionales (CNN), mayor cantidad de épocas o ajuste de hiperparámetros.

Todo se puede evidenciar mejor en el codigo [P2_prendas.ipynb](Codigo/P2_prendas.ipynb)

### 3. Consiga un data set de cualquier tipo, puede ser de https://www.kaggle.com/datasets, estudie sus características (features) y su rótulo. Diseñe una red neuronal y haga ejemplos con base en los pesos aprendidos. 

Para trabajar en este p
P3bien_heart_attack.ipynb
P3mal_fraud_prediction.ipynb
.gitignore
LICENSE
README.md
IA_minibots_T5_redes_neuronales
/
README.md
in
main

Edit

Preview
Indent mode

Spaces
Indent size

2
Line wrap mode

Soft wrap
Editing README.md file contents
Selection deleted
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
unto, se uso primero un data set de fraudes en pagos digitales, el cual se descargo de kaggle. El cual presento variables irrelevantes para el estudio, tales como el ID del cliente y el id de la transacción, el ID del cliente podria ser relevante para el estudio si se contara con una cantidad masiva de datos, lo cual no es el caso, por lo que se descartaron. 

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
