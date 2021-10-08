# 🧠 Notas del Curso de Fundamentos de Procesamiento de Lenguaje Natural con Python y NLTK

- Instructor: Francisco Camacho
- Link al curso: [Curso de Fundamentos de Procesamiento de Lenguaje Natural con Python y NLTK](https://platzi.com/clases/python-lenguaje-natural/)

_Parte considerable de las notas están dentro de los 5 notebooks_

## Introducción al Procesamiento de Lenguaje Natural

- Perspectiva y estado del arte: NLP como el camino hacia el ideal de IA. Creemos que es el camino hacia la verdadera IA. NLP significa **Natural Language Processing**. 🤯
- También relacionado, está el NLU **Natural Language Understanding**, no es lo mismo. Es un área más pequeña de tareas específicas que una máquina puede ejecutar (que la máquina no solo lee, si no que también entiende).
- **Test de Turing**: Si un humano no puede distinguir entre una máquina y otra persona **en una conversación**, entonces esa máquina ha alcanzado un nivel de inteligencia comparable al de un humano. 🧠
- En la cultura Sci-Fi hay un test muy similar: Voight-Kampff (Blade Runner). 🤖
- Usos actuales de NLP:
  - Máquinas de Búsqueda.
  - Traducción de texto.
  - Chatbots.
  - Análisis de discurso.
  - Reconocimiento del habla.
- NLP es un área muy difícil porque el lenguaje no es 100% objetivo, es ambiguo si no se tiene contexto 😵. El lenguaje humano es difuso, ambiguo y requiere mucho contexto.

## Evolución del NLP

- La evolución en general:
  - 1950-1990: Sistemas basados en reglas. Se ponían las reglas del lenguaje de manera explícita.
  - 1990-2000: Estadística de Corpus. Distribución de probabilidad de las palabras 🤔
  - 2000-2014: Machine learning.
  - 2014-2020: Deep learning. Al inicio del uso de GPUs comenzó con más fuerza. 💪🏽
- En general, hay dos vertientes:

![https://i.imgur.com/fC0XYHc.png](https://i.imgur.com/fC0XYHc.png)

- El de bajo nivel es bueno para una sola (o pocas) tareas. La otra aproximación, con deep learning, es bueno realizando varias tareas. 👀 De esta, una ejemplo son las redes secuenciales, donde se observa el texto antes y después de una palabra. Para decidir que palabras observar para el contexto, se usar mecanismos de atención (con transformers).
- Aún hay mucho camino por recorrer, estamos lejos de lograr NLP perfecto 😵.

    [AI still doesn't have the common sense to understand human language](https://www.technologyreview.com/2020/01/31/304844/ai-common-sense-reads-human-language-ai2/)

- En este curso, vamos a estudiar dos librerías muy importantes: NLTK (primeras dos áreas) y SpaCy (áreas dos y tres). 😢

## Conceptos básicos de NLP

- Veremos estructuras básicas del lenguaje humano.
- Del libro *Manning & Schutze (1999), Foundations of Statistical Natural Language Processing*, un libro importante de los fundamentos, tenemos la definición del lenguaje:

    > Entender y caracterizar las reglas que determinan cómo estructurar expresiones lingüística...
    >
- El lenguaje como un objeto de estudio tiene dos aproximaciones: NLP (ingeniería) enfocado a aplicaciones prácticas y LC (Lingüística computacional, Ciencia), enfocado en fines puramente científicos (¿Qué y cómo computan las personas?). Ambas tienen el lenguaje como objeto de estudio 🤔
- La LC está basado en modelos, de los cuales se pueden bajar en conocimiento (en reglas) o en datos (ML).
- Para trabajar con una cadena de texto, debemos *normalizarla,* los cuales son procesos de limpieza y transformación:
  - Tokenización: Consiste en separar una frase en unidades mínimas lingüísticas (palabras, podría ser). 👀
  - Lematización: Convertir cada una de las palabras (o tokens) a su raíz fundamental, por ejemplo, quitamos la conjugación. 😯
  - Segmentación: Segmentamos en frases, por ejemplo podríamos separar con comas, pero no es tan sencillo 🤯.
- Este proceso anterior, queremos aplicarlo a muchas cadenas de texto, el cual llamamos *corpus.* Un conjunto de corpus se llama *corpora.* ✨

## Configurara ambiente de trabajo

- `nltk` ya tiene varios corpus y corpora para trabajar 😄. Para usar una, debemos descargarla. Usaremos un corpus en español `nltk.download("cess_esp")`. Este corpus consiste de titulares de noticas en español.
- Se recomienda tomar el curso de expresiones regulares 👀. Python tiene una librería de expresiones regulares llamada `re`. Las expresiones regulares son un lenguaje estandarizado para definir cadenas de búsqueda de texto.

    [re - Regular expression operations - Python 3.9.7 documentation](https://docs.python.org/3/library/re.html)

- Hay una operación llamada `flatten`, donde *aplanamos* una lista, de tal manera que no tenemos una lista de listas, si no una sola lista con una secuencia de tokens larga 👀.
- Contenido en notebook `regular_expressions.ipynb`.

## N-gramas y colocaciones del lenguaje

- **¿Qué es un N-grama?** Es una secuencia de N palabras consecutivas. Por ejemplo, un digrama serían dos palabras consecutivas. 👀
- **¿Qué son las colocaciones?** Las colocaciones de una palabra son sentencias que indican los lugares que acostumbra a tomar esa palabra en el lenguaje (sin seguir las reglas del lenguaje). 🎚️
  - Por ejemplo, se escucha bien *le dieron ganas de dormir* pero se escucha raro *le introdujeron ganas de dormir.*

## Introducción a los recursos léxicos

- Un recurso léxico es una colección de palabras o frases con meta-datos. También se les llama lexicon. 🤓
- Ejemplo:
  - Le puedes decir que se **calle** o me va a enloquecer.
  - Ten cuidado al cruzar la **calle** porque el semáforo no funciona.
- En este caso, el lexicon:
  - Calle (verbo): Conjugación del verbo callar.
  - Calle (sustantivo): Referencia al espacio público por donde hay tránsito.
- Calle es la entra léxica, además se tiene una categoría léxica (verbo o  sustantivo) y por último un significado o descripción. 🧠

## Introducción a WordNet

- Fundamentos con NLTK: WordNet, es un recurso léxico con mucho uso en muchas tareas de procesamiento, pero ya no tanto por el estado actual del deep learning.🧠
- WordNet es una base de datos con carácter léxico para el idioma inglés. Se compone por conjuntos de sinónimos (**synsets**), cada uno expresando un concepto diferente. Diferentes **synsets** se relacionan por su relación conceptual semántica 🤯.
- Por ejemplo, un synset:
  - Palabras → Carro, automovil, auto, coche
  - Definición → Vehículo motorizado de cuatro ruedas, propulsado por un motor de combustión interna.
- Para relacionarse, existe una **jerarquía** en WordNet. Hay hiperónimos (mas general) y hipónimo (mas particular).👑

## Usando código estructurado: conexión de Drive a Google Colab

- Podemos montar un notebook de Collab en nuestro Drive para usar los archivos que tenemos ahí. Para hacer eso, hacemos:

    ```python
    from google.colab import drive
    drive.mount('content/drive')
    ```

## Usando código estructurado: Funciones externa

- Podemos ejecutar comandos de terminal desde python usando `!comando` 👀.
