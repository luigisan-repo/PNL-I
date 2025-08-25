
Entendemos por **procesamiento del lenguaje natural (PLN)**, o NLP por sus siglas en inglés, es una rama de la inteligencia artificial que se enfoca en enseñar a las computadoras a entender, interpretar y manipular el lenguaje humano. El objetivo principal es cerrar la brecha entre la comunicación humana (lenguaje natural) y la comprensión de las máquinas, permitiendo que las computadoras realicen tareas como la traducción automática, el análisis de sentimientos, la creación de chatbots y la generación de resúmenes de texto.

A continuación, se presenta un resumen de lo que se hace y se aprende a través de los cuatro desafíos de NLP:


<div style="text-align: right;">

    <h1 style="display: inline-block;margin: 0;padding: 8px 16px;color: white;background: linear-gradient(to right,rgb(17, 75, 141), #4CAF50);border-radius: 12px;font-size: 1.8rem;box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);"> Desafíos  </h1>

</div>


### Desafío 1: Fundamentos de la Vectorización y Clasificación de Textos

En este desafío, se abordaron los conceptos de **vectorización** y **clasificación** de texto. Se construyó un conjunto de datos a partir de cinco textos con diferentes temáticas para luego transformarlos en una representación numérica que los modelos de aprendizaje automático puedan procesar.

- **Vectorización de documentos**: Se utilizaron técnicas como **TF-IDF (Term Frequency-Inverse Document Frequency)** para convertir fragmentos de texto en vectores numéricos. Se aprendió a calcular la **similitud de coseno** para determinar qué tan parecidos son dos documentos, y se confirmó que los documentos con contenido similar (ej., de la misma novela) tienen una alta similitud vectorial.
- **Clasificación de texto**: Se entrenaron modelos de clasificación **Naïve Bayes** (MultinomialNB y ComplementNB) para categorizar los fragmentos de texto en sus clases o etiquetas originales. Se observó que el modelo **ComplementNB** funcionó mejor que el **MultinomialNB** debido a la naturaleza **desbalanceada** de los datos, ya que fue diseñado para manejar este tipo de distribuciones de clases de manera más robusta. También se analizó el impacto de diferentes vectorizadores (**CountVectorizer** y **TfidfVectorizer**) en el rendimiento de los modelos.


### Desafío 2: Creación de Embeddings Personalizados

Este desafío se centró en la creación de **embeddings de palabras** personalizados a partir de un corpus específico: la Trilogía de la Fundación de Isaac Asimov. A diferencia de los modelos pre-entrenados, se aprendió a generar representaciones vectoriales adaptadas al contexto de un dominio particular.

- **Modelos Word2Vec**: Se implementaron y compararon dos arquitecturas de **Word2Vec**:
    
    - **Skip-gram (sg=1)**: Dada una palabra, predice su contexto. Es más efectivo para palabras raras.
    - **CBOW (Continuous Bag-of-Words) (sg=0)**: Dado un contexto, predice la palabra central. Es más rápido y funciona mejor con palabras frecuentes.
- **Análisis de similitudes**: Después de entrenar los modelos, se exploró la **similitud de coseno** para encontrar palabras relacionadas. Se confirmó que ambos modelos aprenden a agrupar palabras con significados similares (ej., "imperio", "galáctico") y a realizar operaciones de **aritmética vectorial** para encontrar relaciones semánticas entre palabras.
- **Visualización**: Se utilizaron técnicas de reducción de dimensionalidad como **t-SNE** para visualizar los embeddings en un espacio 2D y 3D, lo que permitió observar cómo las palabras semánticamente cercanas se agrupan en clústeres.



### Desafío 3: Modelos de Lenguaje Basados en Caracteres

Aquí se exploró la construcción de un **modelo de lenguaje a nivel de carácter** utilizando redes neuronales recurrentes (**RNN**). A diferencia de los modelos basados en palabras, este modelo predice el siguiente carácter en una secuencia, lo que le permite generar texto nuevo.
- **Preprocesamiento y tokenización**: Se aprendió a tokenizar un corpus de texto a nivel de carácter y a estructurar el conjunto de datos para el entrenamiento de un modelo de tipo _many-to-many_.
- **Arquitecturas de RNN**: Se implementaron y compararon tres arquitecturas de redes recurrentes: **SimpleRNN**, **LSTM** y **GRU**. Se analizó su rendimiento en función de la **perplejidad**, una métrica clave para evaluar la calidad de los modelos de lenguaje, la cual mide la "sorpresa" del modelo al ver nuevos datos.
- **Estrategias de generación**: Se experimentó con diferentes métodos de inferencia para la generación de texto:
    - **Greedy Search**: Elige el carácter más probable en cada paso.
    - **Beam Search (Determinista)**: Mantiene las secuencias más probables, a menudo llevando a la repetición.
    - **Beam Search (Estocástico)**: Introduce aleatoriedad controlada por un parámetro de **temperatura** para generar texto más creativo y evitar la repetición.
### Desafío 4: Un Bot de Preguntas y Respuestas con Seq2Seq

En este último desafío, se construyó un bot de preguntas y respuestas utilizando una arquitectura **sequence-to-sequence (seq2seq)**, ideal para tareas donde la salida es una secuencia de elementos diferente de la entrada, como la traducción o el diálogo.
- **Arquitectura Seq2Seq**: Se implementó un modelo compuesto por un **Encoder LSTM** (que procesa la pregunta de entrada y la comprime en un vector de contexto) y un **Decoder LSTM** (que usa este vector para generar la respuesta palabra por palabra).
- **Preprocesamiento avanzado**: Se preparó un conjunto de datos de conversaciones, añadiendo tokens especiales (`<sos>` para "start of sequence" y `<eos>` para "end of sequence") esenciales para el correcto funcionamiento de los modelos de decodificación.
- **Embeddings pre-entrenados**: A diferencia del desafío 2, se utilizaron embeddings de palabras pre-entrenados (**GloVe**) para inicializar la capa de embedding del encoder. Esto permite que el modelo aproveche un conocimiento lingüístico general sin tener que aprenderlo desde cero, mejorando su rendimiento.
- **Inferencia del bot**: Se implementó un proceso de inferencia de dos pasos, donde el encoder procesa la pregunta y el decoder genera la respuesta palabra por palabra, lo que permitió interactuar con el bot y observar sus respuestas.