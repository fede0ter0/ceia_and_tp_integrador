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

## Limpieza y preparación de los datos

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



## Ingeniería de features

### Análisis de correlaciones

## Selección de features

### Análisis y tratamiento de outliers
### Escalado de features

## Propuestas de modelos

### Random Forest

### Logistic Regression

