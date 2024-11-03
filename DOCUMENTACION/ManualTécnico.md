# PROYECTO 2

| Nombre                       | Carnet    |
| ---------------------------- | --------- |
| Angel Francisco Sique Santos | 202012039 |

## Objetivo
El objetivo de este proyecto es practicar y aplicar conceptos de Machine Learning mediante la creación de un sitio web interactivo que permita entrenar y evaluar modelos de aprendizaje automático utilizando la biblioteca **tytus.js**. Este sitio web se desarrolla en **GitHub Pages** usando **JavaScript** y **HTML**.

## Descripción del Proyecto
El sitio web cuenta con una interfaz intuitiva que permite a los usuarios cargar archivos CSV y seleccionar diferentes modelos de Machine Learning. Además, incluye herramientas de parametrización y visualización de resultados. Los componentes clave de la interfaz son:

- **Selector de archivos**: Permite cargar archivos CSV o datasets como entradas para los modelos de Machine Learning.
- **Selector de modelos de Machine Learning**: Incluye diferentes algoritmos para análisis y predicción. 
- **Parametrización**:
  - Permite especificar el porcentaje de datos para entrenamiento y prueba.
  - Define el objetivo del entrenamiento (por ejemplo, detectar tendencias, patrones, clasificación o predicción).
  - Configura parámetros específicos del modelo (por ejemplo, el rango en el eje x para predicciones, número de clases para clasificación, selección de variables de entrada y salida en aprendizaje supervisado, entre otros).
- **Botones de operaciones**:
  - Entrenamiento del modelo.
  - Predicción en base al modelo entrenado.
  - Visualización de gráficos.
  - Cualquier otra operación necesaria para cada modelo.

## Bibliotecas Permitidas
Para la implementación de los modelos y su funcionalidad de entrenamiento y predicción, es obligatorio el uso de la biblioteca **tytus.js**:
- Enlace a la biblioteca: [tytus.js en GitHub](https://github.com/tytusdb/tytusjs/blob/main/dist/tytus.js)

Para la visualización y otras funciones complementarias, se permite el uso de cualquier biblioteca de JavaScript puro. No está permitido el uso de frameworks, entornos o plataformas de desarrollo.

Consulta el [repositorio de tytus.js](https://github.com/tytusdb/tytusjs) para obtener más detalles sobre los modelos disponibles y ejemplos de uso.

Este proyecto está diseñado para facilitar el aprendizaje y la exploración de modelos de Machine Learning en un entorno web simple pero efectivo.


# Documentación del Código HTML

## Descripción General
Este documento HTML crea una interfaz web interactiva que permite a los usuarios cargar datos en formato CSV y aplicar diferentes modelos de aprendizaje automático. Los modelos incluidos son **Regresión Lineal**, **Regresión Polinomial**, **Árbol de Decisión ID3** y una **Red Neuronal** basada en datos CSV. La interfaz está desarrollada usando la biblioteca CSS Bulma y cuenta con un carrusel que permite navegar entre los modelos.

## Estructura del Código

### Encabezado `<head>`
En el encabezado se configuran los metadatos y se enlazan las hojas de estilo y scripts externos:

- **Metaetiquetas**: `charset` para definir la codificación como UTF-8 y `viewport` para que el diseño sea responsive.
- **Título**: Indica el título del documento en el navegador.
- **CSS**: 
  - Bulma y bulma-carousel para el diseño de la interfaz.
  - `styles.css`: hoja de estilos personalizada.
  - `notie.min.css`: para la biblioteca de notificaciones `notie`.
- **Iconos Font Awesome**: Añadido mediante un script para iconos visuales en los botones de la página.

### Cuerpo `<body>`

#### Sección Principal `section.section`
Esta sección contiene todos los elementos de la página dentro de un contenedor centralizado.

- **Título Principal**: Un encabezado `h1` que presenta el proyecto.
- **Carrusel**: Un contenedor `div` con el ID `carousel-demo` que alberga cada sección de modelo de aprendizaje automático.

### Secciones de Modelos de Aprendizaje Automático

Cada sección del carrusel representa un modelo de aprendizaje y contiene los siguientes elementos:

1. **Título del Modelo** (`h2`): Describe el tipo de modelo.
2. **Lienzo (`canvas`)**: Donde se graficarán los resultados del modelo.
3. **Selector de Archivo (`file-input`)**: Permite cargar un archivo CSV.
4. **Botones de Acción**: Cada modelo tiene diferentes botones de acción que activan operaciones específicas:
   - **Fit**: Ajusta el modelo.
   - **Predict**: Realiza predicciones (deshabilitado hasta que el modelo esté entrenado).
   - **MSE**: Calcula el error cuadrático medio.
   - **Coeficiente R2**: Calcula el coeficiente de determinación para evaluar la precisión del modelo.
5. **Contenedor de Resultados**: Muestra los resultados de las operaciones en diferentes párrafos (`<p>`).

Cada modelo tiene configuraciones y botones específicos según el tipo de análisis que realiza:

#### Ejemplo: Regresión Lineal
Esta sección incluye un `canvas` para mostrar la gráfica de la regresión y botones para cargar datos, ajustar el modelo y obtener predicciones.

#### Ejemplo: Regresión Polinomial
Incluye un campo de entrada numérica (`input type="number"`) para establecer el grado del polinomio.

#### Ejemplo: Árbol de Decisión ID3
Permite cargar archivos de entrenamiento y generar un árbol de decisión.

#### Ejemplo: Red Neuronal
Permite cargar archivos para la configuración de la red, datos de entrenamiento y datos de prueba.

### Scripts

- **Script para Actualizar el Nombre del Archivo Seleccionado**
  Este script JavaScript, que recorre todos los elementos `file-input`, permite actualizar el nombre del archivo seleccionado en la interfaz.

- **Bibliotecas Externas**:
  - **Chart.js**: Para generar gráficos en los elementos `canvas`.
  - **vis-network**: Para visualizar redes de nodos (para el árbol de decisión).
  - **bulma-carousel**: Para manejar el carrusel de la interfaz.
  - **notie**: Para mostrar notificaciones.

- **Scripts Personalizados**: 
  Scripts específicos para cada modelo (`LinearScript.js`, `PolynomialScript.js`, `DecisionTreeScript.js`, y `NeuralNetworkScript.js`), los cuales están enlazados desde la carpeta `/scripts` y los archivos de modelos en la carpeta `/tytusjs`.

### Observaciones y Estilos Personalizados

- Se aplica un estilo personalizado en el encabezado para el contenedor de notificaciones (`.notie-container`) eliminando la sombra.
- También se establecen configuraciones específicas en el `bulmaCarousel` para controlar el desplazamiento y el margen de los elementos del carrusel.

### Conclusión

Este documento HTML construye una interfaz interactiva para pruebas y visualización de modelos de aprendizaje automático, que utiliza varias bibliotecas externas para optimizar la presentación y funcionalidad del proyecto.

# Documentación de `DecisionTreeScript.js`

Este archivo implementa una aplicación de árbol de decisión basada en el algoritmo **ID3**, utilizando **JavaScript** para la carga de datos y la visualización del árbol de decisión. La biblioteca **tytus.js** es utilizada para el manejo de árboles de decisión, y **vis.js** se emplea para la visualización gráfica.

## Variables Globales

- **`trainingData`**: Almacena los datos de entrenamiento cargados desde un archivo CSV.
- **`predictionData`**: Almacena los datos de predicción opcionales, si se carga un archivo de predicción.

## Funciones

### `readCSVID3(file)`
Función asíncrona que lee un archivo CSV y devuelve sus datos en forma de array de filas y columnas.

- **Parámetros**:
  - `file`: El archivo CSV a leer.
  
- **Retorno**: 
  - `Promise`: Devuelve una promesa que resuelve un array bidimensional con los datos CSV.

### `loadTrainingData()`
Carga los datos de entrenamiento a partir de un archivo CSV seleccionado por el usuario. Si el archivo no se selecciona, muestra una alerta.

- **Funcionalidad**: 
  - Usa `readCSVID3` para leer los datos del archivo y asignarlos a `trainingData`.
  - Muestra una alerta de éxito usando `notie` si los datos se cargan correctamente.

### `loadPredictionData()`
Carga opcionalmente los datos de predicción a partir de un archivo CSV.

- **Funcionalidad**:
  - Usa `readCSVID3` para leer el archivo de predicción si está presente y los almacena en `predictionData`.
  - Muestra una alerta de éxito si los datos de predicción se cargan correctamente.

### `generatechart()`
Genera el árbol de decisión ID3 con los datos de entrenamiento y realiza una predicción si existen datos de predicción.

- **Funcionalidad**:
  - Verifica que los datos de entrenamiento estén cargados; en caso contrario, muestra una alerta.
  - Entrena un árbol de decisión ID3 (`DecisionTreeID3`) usando los datos de entrenamiento.
  - Si hay datos de predicción, utiliza el árbol entrenado para realizar una predicción.
  - Devuelve un objeto con el `dotStr` para la visualización y el nodo de predicción (`predictNode`) si está disponible.

- **Retorno**:
  - Un objeto que contiene:
    - `dotStr`: Una representación en formato DOT del árbol.
    - `predictNode`: El nodo de predicción, si existe.

### Evento `predict.onclick`
Controla el evento de clic en el botón de predicción, ejecutando la predicción con los datos cargados y visualizando el árbol.

- **Funcionalidad**:
  - Carga los datos de predicción mediante `loadPredictionData`.
  - Llama a `generatechart` para generar el árbol y, si hay predicción, la muestra en pantalla.
  - Convierte el formato DOT en un gráfico interactivo y lo visualiza en el elemento con id `treed`.

### Evento `btngenerate.onclick`
Controla el evento de clic en el botón de generación de árbol de decisión, cargando los datos de entrenamiento y visualizando el árbol generado.

- **Funcionalidad**:
  - Carga los datos de entrenamiento mediante `loadTrainingData`.
  - Llama a `generatechart` para crear y visualizar el árbol.
  - Si hay predicción disponible, la muestra en pantalla.
  - Convierte el formato DOT en un gráfico interactivo y lo visualiza en el elemento con id `treed`.

## Opciones de Configuración para `vis.js`

Para la visualización del árbol en un gráfico interactivo, se configuran las opciones de **vis.js** para personalizar el diseño y colores de nodos y bordes.

- **Nodos**:
  - `color`: Configuración del color de fondo, bordes, resaltado y hover.
  - `font`: Color de fuente en los nodos.

- **Bordes**:
  - `color`: Color de los bordes y sus variantes en estados de resaltado y hover.
  - `arrows`: Flecha en la dirección de los bordes, escalada.

- **Layout**:
  - Configuración jerárquica con separación de niveles y centralización de los padres.

## Notas adicionales

- La visualización interactiva utiliza `vis.network.convertDot` para convertir la representación en DOT del árbol en un gráfico renderizado en HTML.
- Las alertas se muestran usando la biblioteca `notie` para mejorar la experiencia de usuario en las acciones de carga de archivos y generación del árbol.

# Documentación de `LinearScript.js`

Este archivo implementa un modelo de **Regresión Lineal** en una aplicación web. La interfaz permite cargar datos desde un archivo CSV, ajustar el modelo, realizar predicciones y calcular métricas como el **Error Cuadrático Medio (MSE)** y el **Coeficiente de Determinación (R²)**. Además, se visualizan los datos y el ajuste del modelo en un gráfico.

## Elementos del DOM

- **`fileInput`**: Selector de archivos para cargar el archivo CSV.
- **`fitBtn`**: Botón para ajustar el modelo con los datos cargados.
- **`predictBtn`**: Botón para realizar predicciones usando el modelo ajustado.
- **`mseBtn`**: Botón para calcular y mostrar el MSE.
- **`r2Btn`**: Botón para calcular y mostrar el Coeficiente R².
- **`fitResult`, `predictResult`, `mseResult`, `r2Result`**: Elementos donde se muestran los resultados de los ajustes, predicciones y métricas.

## Variables Globales

- **`xVars`** y **`yVars`**: Arrays que almacenan las variables independientes y dependientes (X y Y) de los datos cargados.
- **`linearInstance`**: Instancia del modelo de regresión lineal.
- **`predict`**: Array donde se almacenan los valores predichos.
- **`linearChart`**: Instancia del gráfico que muestra los datos y la línea de regresión.

## Funciones

### `readCSV(file)`
Lee y procesa un archivo CSV, extrayendo las variables `xVars` y `yVars`.

- **Parámetros**:
  - `file`: Archivo CSV a procesar.
  
- **Retorno**:
  - `Promise`: Devuelve una promesa que resuelve un objeto con `xVars` y `yVars`.

### `fitModel()`
Ajusta el modelo de regresión lineal usando los datos cargados desde el archivo CSV.

- **Funcionalidad**:
  - Verifica que se haya seleccionado un archivo, en caso contrario muestra una alerta.
  - Lee y asigna los datos `xVars` y `yVars`.
  - Ajusta el modelo usando `linearInstance.fit`.
  - Habilita el botón de predicción (`predictBtn`) y muestra una alerta de éxito.

### `predictModel()`
Realiza predicciones usando el modelo ajustado y habilita los botones de métricas (MSE y R²).

- **Funcionalidad**:
  - Usa `linearInstance.predict` para calcular las predicciones basadas en `xVars`.
  - Llama a `renderChart()` para actualizar el gráfico con las predicciones.
  - Muestra una alerta de éxito.

### `calculateMSE()`
Calcula el **Error Cuadrático Medio (MSE)** entre los valores reales y las predicciones, y muestra el resultado.

- **Funcionalidad**:
  - Usa `linearInstance.mserror` para calcular el MSE.
  - Muestra el resultado en `mseResult` y una alerta con el valor de MSE.

### `calculateR2()`
Calcula el **Coeficiente de Determinación (R²)**, una métrica que indica la calidad del ajuste, y muestra el resultado.

- **Funcionalidad**:
  - Usa `linearInstance.coeficientR2` para calcular el R².
  - Muestra el resultado en `r2Result` y una alerta con el valor de R².

### `renderChart()`
Renderiza un gráfico que muestra tanto los datos originales como la línea de regresión generada por el modelo.

- **Funcionalidad**:
  - Crea dos datasets para el gráfico:
    - **Regresión Lineal**: Línea ajustada del modelo.
    - **Datos Originales**: Datos originales del CSV.
  - Utiliza **Chart.js** para renderizar el gráfico y almacenarlo en `linearChart`.
  - Configura opciones visuales como el color de los puntos y la posición de los ejes.

## Event Listeners

- **`fitBtn`**: Ejecuta `fitModel()` al hacer clic para ajustar el modelo.
- **`predictBtn`**: Ejecuta `predictModel()` al hacer clic para realizar predicciones.
- **`mseBtn`**: Ejecuta `calculateMSE()` al hacer clic para calcular el MSE.
- **`r2Btn`**: Ejecuta `calculateR2()` al hacer clic para calcular el R².

## Notas adicionales

- **Alertas**: Se utiliza la biblioteca `notie` para mostrar alertas de éxito o advertencia al usuario en diversas acciones.
- **Validaciones**: Los botones `predictBtn`, `mseBtn` y `r2Btn` están deshabilitados hasta que se cumplan las condiciones necesarias (por ejemplo, ajuste del modelo).
- **Visualización**: `Chart.js` se usa para renderizar el gráfico de dispersión y la línea de ajuste. La gráfica es destruida y recreada cada vez que se actualizan los datos para asegurar que los nuevos datos sean correctamente renderizados.

# Documentación de `NeuralNetworkScript.js`

Este script implementa una interfaz para cargar y procesar datos en una red neuronal, entrenar el modelo y realizar predicciones en una aplicación web. La red neuronal toma configuración desde un archivo y usa datos de entrenamiento y predicción en formato CSV.

## Variables Globales

- **`networkConfig`**: Almacena la configuración de la red neuronal, es decir, la estructura o arquitectura de la red, especificada en el archivo de configuración.
- **`networkTrainingData`**: Datos de entrenamiento para ajustar los pesos de la red neuronal.
- **`networkPredictionData`**: Datos de entrada para realizar predicciones con la red neuronal entrenada.

## Funciones

### `readCSVNetwork(file)`
Lee un archivo CSV y devuelve los datos en un array de arrays, donde cada sub-array representa una fila del archivo.

- **Parámetros**:
  - `file`: Archivo CSV a leer.
  
- **Retorno**:
  - `Promise`: Devuelve una promesa que resuelve un array de arrays de números (datos procesados del archivo CSV).

### `Cargar configuración de red`
Carga la configuración de la red neuronal desde un archivo CSV. La configuración se guarda en `networkConfig`.

- **Eventos**:
  - `change` en el elemento `#network-config-file`: Activa la función para leer el archivo y almacenar su contenido en `networkConfig`.

### `Cargar datos de entrenamiento`
Carga los datos de entrenamiento desde un archivo CSV. Los datos se guardan en `networkTrainingData`.

- **Eventos**:
  - `change` en el elemento `#training-data-file`: Activa la función para leer el archivo y almacenar su contenido en `networkTrainingData`.

### `Cargar datos de predicción`
Carga los datos de predicción desde un archivo CSV. Los datos se guardan en `networkPredictionData`.

- **Eventos**:
  - `change` en el elemento `#prediction-data-file`: Activa la función para leer el archivo y almacenar su contenido en `networkPredictionData`.

### `Entrenar y predecir`
Esta función entrena la red neuronal con los datos de entrenamiento y realiza predicciones usando los datos de predicción.

- **Funcionalidad**:
  - Verifica que los archivos de configuración, entrenamiento y predicción estén cargados.
  - Crea una instancia de la red neuronal usando `networkConfig`.
  - Entrena la red neuronal para cada fila en `networkTrainingData`, dividiendo los datos entre entradas y salidas según la configuración.
  - Realiza predicciones para cada fila en `networkPredictionData`.
  - Muestra las predicciones en el elemento `#nnresultado`.

- **Eventos**:
  - `click` en el botón `#train-and-predict-btn`: Activa el entrenamiento y predicción si se cumplen las condiciones necesarias (archivos cargados).

## Estructura HTML

- **Elementos utilizados en el script**:
  - **`#network-config-file`**: Input de archivo para cargar la configuración de la red.
  - **`#training-data-file`**: Input de archivo para cargar datos de entrenamiento.
  - **`#prediction-data-file`**: Input de archivo para cargar datos de predicción.
  - **`#train-and-predict-btn`**: Botón para ejecutar el entrenamiento y predicción.
  - **`#nnresultado`**: Elemento donde se muestran los resultados de las predicciones.

## Notas Adicionales

- **Alertas**: El script utiliza `notie` para mostrar alertas de éxito o advertencia durante el proceso de carga de archivos, entrenamiento y predicción.
- **Validación**: La función de entrenamiento y predicción verifica que todos los archivos necesarios estén cargados antes de ejecutarse.
- **Resultados**: Las predicciones se muestran en un formato de lista en `#nnresultado`, con dos decimales para cada valor predicho.

# Documentación de `PolynomialScript.js`

Este script permite ajustar un modelo de regresión polinomial con datos cargados desde un archivo CSV, predecir valores basados en el modelo ajustado y calcular métricas de evaluación como el Error Cuadrático Medio (MSE) y el coeficiente R².

## Variables Globales

- **`polyXVars`**: Almacena las variables independientes (X) cargadas desde el archivo CSV.
- **`polyYVars`**: Almacena las variables dependientes (Y) cargadas desde el archivo CSV.
- **`polynomialInstance`**: Instancia del modelo de regresión polinomial.
- **`polyPredict`**: Array de predicciones generadas por el modelo.

## Funciones

### `readPolyCSV(file)`
Lee un archivo CSV, procesa los datos y devuelve las variables independientes y dependientes en arrays separados.

- **Parámetros**:
  - `file`: Archivo CSV que contiene los datos de entrada.
  
- **Retorno**:
  - `Promise`: Devuelve un objeto con dos arrays, `xVars` y `yVars`, que representan las variables independientes y dependientes, respectivamente.

### `fitPolyModel()`
Ajusta el modelo de regresión polinomial a los datos cargados y habilita el botón de predicción.

- **Funcionalidad**:
  - Verifica si se ha seleccionado un archivo CSV y el grado del polinomio.
  - Ajusta el modelo polinomial usando los datos cargados (`polyXVars` y `polyYVars`) y el grado especificado en `polyDegreeInput`.

### `predictPolyModel()`
Genera predicciones basadas en el modelo ajustado y habilita los botones para calcular el MSE y R².

- **Funcionalidad**:
  - Realiza predicciones con los datos de `polyXVars`.
  - Genera el gráfico de regresión polinomial y muestra las predicciones en pantalla.

### `calculatePolyMSE()`
Calcula y muestra el Error Cuadrático Medio (MSE) de las predicciones.

- **Funcionalidad**:
  - Llama al método `getError()` del objeto `polynomialInstance` para obtener el MSE del modelo y lo muestra en `polyMSEResult`.

### `calculatePolyR2()`
Calcula y muestra el coeficiente de determinación (R²) de las predicciones.

- **Funcionalidad**:
  - Llama al método `getError()` del objeto `polynomialInstance` para obtener el valor de R² del modelo y lo muestra en `polyR2Result`.

### `renderPolyChart()`
Dibuja un gráfico de dispersión que muestra tanto los datos originales como la línea de ajuste polinomial.

- **Funcionalidad**:
  - Usa los datos de `polyXVars`, `polyYVars`, y `polyPredict` para generar un gráfico de dispersión que visualiza tanto los puntos originales como la línea de regresión polinomial.
  - El gráfico se actualiza si ya existe uno previo.

## Estructura HTML

- **Elementos utilizados en el script**:
  - **`#polynomial--file`**: Input de archivo para cargar los datos.
  - **`#polynomial-degree`**: Input numérico para especificar el grado del polinomio.
  - **`#polynomial--btn-fit`**: Botón para ajustar el modelo.
  - **`#polynomial--btn-predict`**: Botón para predecir con el modelo ajustado.
  - **`#polynomial--btn-mse`**: Botón para calcular el MSE.
  - **`#polynomial--btn-r2`**: Botón para calcular el coeficiente R².
  - **`#poly-fit-result`**: Elemento para mostrar el resultado del ajuste.
  - **`#poly-predict-result`**: Elemento para mostrar las predicciones.
  - **`#poly-mse-result`**: Elemento para mostrar el valor del MSE.
  - **`#poly-r2-result`**: Elemento para mostrar el valor de R².
  - **`#polynomial--canva`**: Canvas donde se renderiza el gráfico de la regresión polinomial.

## Notas Adicionales

- **Alertas**: Utiliza `notie` para mostrar alertas sobre el estado de los procesos como la carga de datos, ajuste del modelo y cálculo de métricas.
- **Validación**: La función `fitPolyModel` verifica que el archivo CSV y el grado del polinomio estén seleccionados antes de ejecutar el ajuste del modelo.
- **Resultados**: Las predicciones y métricas calculadas se muestran en los elementos designados en el HTML.
