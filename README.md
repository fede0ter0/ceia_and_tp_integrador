# Trabajo Integrador

### Integrantes del grupo
María Alejandra Del Porto - alejandradelporto@gmail.com<br>
Juan Ignacio Munar - juanimunar@gmail.com<br>
Federico Otero - fede.e.otero@gmail.com<br>

A modo explicativo, trataremos de ser breves y didácticos. Vamos a abundar en imágenes y tablas, tratando de explicar lo que en la notebook puede verse implementado en detalle.

## Selección del dataset

El dataset elegido contiene mediciones meteorológicas efectuadas en distintas ciudades y fechas de Australia, como se puede ver en esta captura de pantalla:

<img width="952" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/2b58b46d-88f7-436f-b1ce-455ebb03a718">

El objetivo es poder predecir si lloverá al día siguiente, es decir, el valor de la variable target **RainTomorrow (Yes / No)**

## EDA

Nuestro Análisis Exploratorio Inicial nos permite entender cada variable del dataset.

<img width="781" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/f560ebc2-86f4-4744-bd28-09153d51ef32">

Luego de esto, analizamos cada variable según su categoría.

### Análisis de features numéricas

### Análisis de variables (input/output) categóricas 

### Análisis de la variable compuesta

## Ingeniería de features

Comenzamos ahora a intervenir en nuestro dataset. Lo primero que haremos será un análisis y tratamiento de los valores nulos o faltantes.

### Análisis de los valures nulos

Esta es la imagen que se nos presenta al ver los valores nulos del dataset en crudo.

<img width="405" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/b0601206-7562-4d56-8f69-4671b82e89bb">

Estos nos permite filtrar algunas variables y pensar los siguientes pasos.

<img width="307" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/3afd59f9-109a-4fc4-821d-ba633feec3fd">

Finalmente, cuando asignamos valores a los nulos restantes, veremos que

<img width="330" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/5cee81e7-4d91-4b2e-b050-21fe2bd739d2">

### Imputación de valores faltantes en variables numéricas

Para hacer este paso, nos apoyamos en los análisis de las distribuciones de las variables numéricas, de modo que podemos ver si las mismas son normales o presentan oblicuidades muy marcadas.

Finalmente, nos queda

<img width="292" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/fc324b18-8181-4747-af5a-49d173a4aa77">

## Transformación de variables

En este paso, vamos a transformar algunas variables para lograr mejor performance en los modelos que se probarán. La técnica de transformación o encoding dependerá del análisis de la variable en cuestión.

### WindGustDir

Se decidió reemplazar la dirección del viento expresada categóricamente (sureste, noreste, centroeste, etc.) por el ángulo que forma el mismo expresado en radianes, de modo que se convirtió de categórica en numérica continua.

### Location

Se aplicó un encoding binario para no agregar demasiadas columnas.

### Date

Se decidió reemplazar la fecha Date (yyyy-mm-dd) por el mes, ya que como sabemos las temperaturas a lo largo del año suele ser cíclicas. Luego se transformó de categórica nominal con un onehotencoding.

### RainToday y RainTomorrow

Estas dos variables son boolenas (Yes/No), de modo que con una columna que tome los valores (0,1) alcanza para codificarlas.

## Análisis de correlaciones

### Análisis de colinealidad entre features numéricas


<img width="850" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/71f135be-8e37-4d8d-b51c-cf0d86621e7b">

### Análisis de Kendall entre las features y la variable target

<img width="912" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/c9ecf486-ba7d-4948-863e-2e86e501e088">

### Análisis X<sup>2</sup> y de Información Mutua (MI) para la relación entre las features categóricas y la variable target.

**X<sup>2</sup>**

<img width="892" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/8b6ed8ac-a832-4088-afdd-97f3e2037c2d">

**MI**

<img width="894" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/4a3d890c-f1f2-4cf0-9a17-0569d94194c5">

## Selección de features

<img width="909" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/35108398-f8ea-4ada-8df6-cb2d01394e31">

### Análisis y tratamiento de outliers

En base a visualizar algunas métricas sobre outliers y las distribuciones de sus variables:

<img width="896" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/27ac0148-8f39-43d5-a829-acc8eebef0a8">

<img width="884" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/18266e83-8a57-4608-900b-17a90abefbf7">

<img width="889" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/d838e4ff-a874-4142-81d1-8e4253734cda">

<img width="892" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/e6dcc1eb-bbd8-4aeb-b441-4c15c6cfff4e">

A partir desto decidimos tratar el outlier de manera distintas en el caso de las variables gaussianas (normales) y en el caso de las no gaussianas.

La estrategia utilizada es la poda, ya que resulta sencilla y eficiente para este caso donde disponemos de un tamaño grande de muestras.

### Escalado de features

Normalizamos las features numéricas como último paso de la etapa de preprocesmiento de los datos.
Veremos ahora dos propuestas sencillas de modelos a testear, que pueden funcionar bien para nuestro dataset de pocas columnas y variables categóricas (tanto features como la target a predecir).

## Propuestas de modelos

### Separación de los datos

Se utilizó una función sencilla de _sci-kit learn_, donde se separó en train-test (80%-20%) con un valor de _random_state_.

### Random Forest

El score obtenido, luego de tratar de tunear los hiperparámetros, es de **87,11%**:

<img width="684" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/e2523121-01a9-4f9c-a5c3-287fe1424a91">

![image](https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/cc65dd9e-6c70-47e6-9e60-c9e71a04df60)

Podemos probar estrategias de cross validation para tener un entrenamiento más balanceado de los datos

<img width="831" alt="image" src="https://github.com/fede0ter0/ceia_and_tp_integrador/assets/109430776/246a0302-fa75-4e2a-b3b2-ee1b415d708f">

### Logistic Regression


