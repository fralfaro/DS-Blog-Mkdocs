# Cómo Compartir Datos de Manera Efectiva

<img src="https://raw.githubusercontent.com/fralfaro/DS-Blog/main/docs/blog/posts/2023/img/share.png" width="200" align="center" />

> **Nota**: Este documento representa una adaptación personalizada del repositorio original en inglés de [jtleek/datasharing](https://github.com/jtleek/datasharing).

Esta guía está diseñada para todos aquellos que necesitan colaborar con un estadístico o
científico de datos en el proceso de análisis de
datos. Nuestro público objetivo abarca:

1. Colaboradores que requieren análisis estadísticos o de datos para sus proyectos.
2. Estudiantes o posdoctorados en diversas disciplinas en busca de asesoramiento y consultoría.
3. Estudiantes de estadística junior que desempeñan un papel crucial en la recopilación, limpieza y preparación de conjuntos de datos.

El propósito de esta guía 
es ofrecer pautas y recomendaciones para 
compartir datos de manera eficiente, 
evitando errores comunes y retrasos en la
transición desde la recopilación de datos 
hasta su análisis. 

Sostenemos firmemente la idea de que los
estadísticos deben ser capaces de trabajar con
los datos en cualquier estado en el que se encuentren. 

Es esencial examinar los datos en su estado crudo, 
comprender los pasos involucrados en su procesamiento y
poder identificar fuentes ocultas de variabilidad en el 
análisis de datos. Sin embargo, para muchos tipos de datos, 
los pasos de procesamiento están bien documentados y 
estandarizados. Por lo tanto, la labor de transformar 
los datos desde su forma original a una forma directamente
analizable puede realizarse antes de involucrar a un estadístico.

Esta práctica puede acelerar significativamente el tiempo 
de respuesta, ya que el estadístico no tendrá que ocuparse 
de todos los pasos de preprocesamiento inicialmente.

## Elementos Esenciales para una Colaboración Exitosa

Si deseas asegurar un análisis eficiente y oportuno, es fundamental proporcionar al estadístico 
la siguiente información:

1. **Datos en su Estado Original** (raw data): Esto incluye los datos sin procesar, tal como se recopilaron, sin ningún tipo de transformación o manipulación. Al brindar los datos en su forma bruta, permites al estadístico comprender la fuente y la calidad de la información.
2. **Conjunto de Datos Ordenado** (Tidy Data Set): Un conjunto de datos ordenado sigue los principios del "Tidy Data", lo que significa que se organiza de manera que cada variable se encuentre en una columna y cada observación en una fila. Esta estructura facilita el análisis y la interpretación de los datos de manera efectiva.
3. **Detalles del Conjunto de Datos**: Se debe describir minuciosamente cada variable presente en el conjunto de datos ordenado, incluyendo información sobre los valores que pueden tomar. Proporcionar un libro de códigos es esencial para que el estadístico comprenda la naturaleza de las variables y cómo interpretarlas correctamente.
4. **Lista de Instrucciones** (script): Es crucial suministrar una descripción detallada de los pasos exactos que seguiste para transformar los datos desde su estado original hasta el conjunto de datos ordenado. Esto garantiza la reproducibilidad y una comprensión completa de tu proceso por parte del estadístico.

### Datos en su Estado Original (raw data)

Uno de los elementos fundamentales en cualquier análisis de datos 
es la inclusión de los datos en su forma más "cruda" y original. 
Esto garantiza que la procedencia de los datos se mantenga intacta a
lo largo de todo el proceso de trabajo. Aquí te proporcionamos ejemplos 
de lo que se entiende por datos en su estado más "crudo":

- Un enigmático archivo binario generado por tu máquina de medición.
- Un archivo de Excel sin procesar con 10 hojas de trabajo que has recibido de la empresa con la que colaboras.
- Complejos datos en formato JSON que has extraído al hacer web scraping de la API de Twitter.
- Números ingresados manualmente mientras observabas a través de un microscopio.

Puedes considerar que los datos están en su formato crudo si:

1. No se ha aplicado ningún software a los datos.
2. Los valores de los datos no han sido alterados.
3. No se ha eliminado ninguna parte de los datos del conjunto.
4. Los datos no han sido resumidos o transformados de ninguna manera.

Si realizaste alguna modificación en los datos en bruto, 
estos ya no se consideran en su forma cruda. 
Reportar datos modificados como datos en bruto es una práctica común que 
puede ralentizar significativamente el proceso de análisis, ya que el analista 
a menudo debe realizar un examen minucioso de tus datos para comprender por qué los
datos en su forma cruda parecen inusuales.
(Imagina también cómo impactaría en futuros análisis si llegan nuevos datos). 
Mantener la integridad de los datos en su forma cruda es esencial para un
análisis sólido y confiable.

Claro, te proporcionaré un ejemplo práctico y aplicado en Python que ilustra los principios de datos ordenados (tidy data) de Hadley Wickham. En este ejemplo, trabajaremos con un conjunto de datos de resultados de exámenes médicos para varios pacientes.

**Ejemplo Práctico**

Supongamos que tenemos un conjunto de datos de resultados de exámenes médicos para tres 
pacientes en una clínica. Los exámenes incluyen mediciones de presión arterial (sistólica y diastólica), 
nivel de glucosa y nivel de colesterol. El conjunto de datos se ve de la siguiente manera:

| Paciente | Presion_Sistolica | Presion_Diastolica | Glucosa | Colesterol |
|----------|-------------------|--------------------|---------|------------|
| 1        | 120               | 80                 | 95      | 180        |
| 2        | 130               | 85                 | 105     | 190        |
| 3        | 115               | 75                 | 90      | 170        |

Estos datos están sin procesar, tal como se recopilarían de los pacientes.

### Conjunto de datos ordenado (tidy data set)

Los principios generales de los datos ordenados (tidy data) son presentados por
[Hadley Wickham](http://had.co.nz/) en [este artículo](http://vita.had.co.nz/papers/tidy-data.pdf) y
[este video](http://vimeo.com/33727555). 
Aunque tanto el artículo como el video describen los datos ordenados 
utilizando [R](http://www.r-project.org/), los principios son aplicables de manera más general:

1. Cada variable que mides debe estar en una columna.
2. Cada observación diferente de esa variable debe estar en una fila diferente.
3. Debe haber una tabla para cada "tipo" de variable.
4. Si tienes varias tablas, deben incluir una columna en la tabla que permita unirlas o combinarlas.

La idea detrás de los datos ordenados es 
que los datos se organicen de manera que sea fácil identificar y seleccionar variables, 
así como realizar análisis de manera eficiente. Siguiendo estos principios, 
se logra una estructura de datos que es intuitiva y facilita el trabajo de
los analistas y científicos de datos, ya que no necesitan descifrar la estructura de 
los datos en cada proyecto. También se promueve el uso de nombres descriptivos para las variables,
lo que mejora la comprensión de los datos por parte de otros colaboradores.

**Ejemplo Práctico**

Continuando con el ejemplo, tenemos cuatro variables: Paciente, Presion_Sistolica, Presion_Diastolica,
Glucosa y Colesterol. Así que, creamos 
un conjunto de datos ordenado donde cada una de estas variables tiene su propia columna:

| Paciente | Variable           | Valor |
| -------- | ------------------ | ----- |
| 1        | Presion_Sistolica  | 120   |
| 1        | Presion_Diastolica | 80    |
| 1        | Glucosa            | 95    |
| 1        | Colesterol         | 180   |
| 2        | Presion_Sistolica  | 130   |
| 2        | Presion_Diastolica | 85    |
| 2        | Glucosa            | 105   |
| 2        | Colesterol         | 190   |
| 3        | Presion_Sistolica  | 115   |
| 3        | Presion_Diastolica | 75    |
| 3        | Glucosa            | 90    |
| 3        | Colesterol         | 170   |

Esto es un conjunto de datos ordenado porque cumple con las reglas mencionadas anteriormente.

### Detalles del Conjunto de Datos

Para casi cualquier conjunto de datos, las mediciones que calculas necesitarán ser descritas con más detalle de lo que puedes o debes incluir en la hoja de cálculo. El libro de códigos contiene esta información. Como mínimo, debería contener:

1. Información sobre las variables (¡incluyendo unidades!) en el conjunto de datos que no están contenidas en los datos ordenados (tidy data).
2. Información sobre las elecciones de resumen que hiciste.
3. Información sobre el diseño experimental que utilizaste.

**Ejemplo Práctico**

**Información sobre las Variables:**

En nuestro ejemplo de resultados de exámenes médicos, tenemos los detalles adicionales sobre las variables:

   - **Presion_Sistolica**: Presión arterial sistólica medida en mmHg (milímetros de mercurio).
   - **Presion_Diastolica**: Presión arterial diastólica medida en mmHg.
   - **Glucosa**: Nivel de glucosa en sangre medido en mg/dL (miligramos por decilitro).
   - **Colesterol**: Nivel de colesterol en sangre medido en mg/dL.

Estos detalles son importantes para que otros comprendan las unidades de medida y
la naturaleza de las variables.

**Información sobre las Elecciones de Resumen:**

Si realizaste alguna operación de resumen en los datos, como el cálculo de promedios o medianas, 
debes explicar estas elecciones en el libro de códigos. Por ejemplo, si calculaste el 
promedio de la presión arterial sistólica para resumir los datos, debes mencionarlo y
proporcionar la fórmula utilizada.

* **Promedio de la presión sistólica**: Se calculó como la media de todas las mediciones de presión sistólica en el conjunto de datos.
    * Promedio de la presión sistólica = (Suma de todas las mediciones de presión sistólica) / (Número de pacientes)
* **Mediana de la presión diastólica**: Se calculó como la mediana de todas las mediciones de presión diastólica en el conjunto de datos.
    * Mediana de la presión diastólica = Valor central cuando las mediciones se ordenan de menor a mayor


**Información sobre el Diseño Experimental:**

Se debe incluir detalles sobre cómo se recopilaron los datos y el diseño experimental subyacente. 
Por ejemplo, si los datos se recopilaron de pacientes en un estudio clínico,
debes describir cómo se seleccionaron los pacientes, si hubo aleatorización en los tratamientos, 
y cualquier otro detalle relevante sobre el diseño del estudio.

- **Selección de Pacientes:** Los pacientes fueron seleccionados de un centro de atención médica en el que se atienden personas con afecciones cardiovasculares. La selección de pacientes se realizó de manera no aleatoria, y se incluyeron aquellos que cumplieron con los siguientes criterios de inclusión: diagnóstico de enfermedad cardiovascular confirmado, disponibilidad de datos de presión arterial, niveles de glucosa y colesterol, y consentimiento para participar en el estudio.

- **Aleatorización en Tratamientos:** En este estudio, no se aplicó aleatorización en los tratamientos. Los pacientes recibieron el tratamiento médico habitual según las pautas clínicas establecidas por sus médicos tratantes. Por lo tanto, no se realizaron intervenciones experimentales ni asignaciones aleatorias de tratamientos.

- **Recopilación de Datos:** Los datos se recopilaron mediante la revisión de los registros médicos electrónicos de los pacientes. Se registraron las mediciones de presión arterial sistólica y diastólica, los niveles de glucosa en sangre y los niveles de colesterol en momentos específicos de las consultas médicas de los pacientes.

### La Lista de Instrucciones/Script

Es posible que hayas escuchado esto antes,
pero [la reproducibilidad es un gran tema en la ciencia computacional](http://www.sciencemag.org/content/334/6060/1226).
Esto significa que cuando envíes tu artículo, 
los revisores y el resto del mundo deberían poder replicar exactamente 
los análisis desde los datos crudos hasta los resultados finales. Si estás tratando de
ser eficiente, es probable que realices algunas etapas de resumen/análisis de datos 
antes de que los datos se consideren ordenados.

Lo ideal que debes hacer al realizar el resumen es crear
un script de computadora (en `R`, `Python`, u otro lenguaje) que
tome los datos crudos como entrada y produzca los datos ordenados que estás compartiendo como salida. 
Puedes intentar ejecutar tu script algunas veces y ver si produce la misma salida.

En muchos casos, la persona que recopiló los datos tiene
incentivos para que sean ordenados para un estadístico y acelerar el proceso de colaboración. 
Es posible que no sepa cómo programar en un lenguaje de script.
En ese caso, lo que debes proporcionar al estadístico es algo llamado
[pseudocódigo](http://en.wikipedia.org/wiki/Pseudocode). Debería verse algo como:

1. **Paso 1** - tomar el archivo crudo, ejecutar la versión 3.1.2 del software de resumen con parámetros a=1, b=2, c=3
2. **Paso 2** - ejecutar el software por separado para cada muestra
3. **Paso 3** - tomar la tercera columna del archivo de salida para cada muestra y esa es la fila correspondiente en el conjunto de datos de salida

También debes incluir información sobre qué sistema (Mac/Windows/Linux) utilizaste para el software y 
si lo intentaste más de una vez para confirmar que daba los mismos resultados. Idealmente, deberías hacer que otro estudiante o compañero de laboratorio confirme que puede obtener el mismo archivo de salida que tú.

**Ejemplo Práctico**

Este código se ejecutó en Python 3.8.5 y utiliza las bibliotecas `pandas` y `IPython.display`.
Las dependencias y la versión  de Python están indicadas en los comentarios para mayor claridad.

```python
# Importar las bibliotecas necesarias
import pandas as pd
from IPython.display import display

# Versión de Python utilizada: 3.8.5

# Crear un DataFrame con los datos originales
data = {
    'Paciente': [1, 2, 3],
    'Presion_Sistolica': [120, 130, 115],
    'Presion_Diastolica': [80, 85, 75],
    'Glucosa': [95, 105, 90],
    'Colesterol': [180, 190, 170]
}

df_original = pd.DataFrame(data)

# Crear un nuevo DataFrame en el formato deseado (unstack)
df_unstacked = df_original.set_index('Paciente').stack().reset_index()
df_unstacked.columns = ['Paciente', 'Variable', 'Valor']

# Calcular diferentes estadísticas
estadisticas = df_unstacked.groupby('Variable')['Valor'].describe()

# Mostrar el DataFrame en el formato antiguo   
print("Mostrar el DataFrame en el formato antiguo:")
display(df_original)

# Mostrar el DataFrame en el formato nuevo   
print("\nMostrar el DataFrame en el formato nuevo:")
display(df_unstacked)

# Mostrar las estadísticas básicas
print("\nMostrar las estadísticas básicas:")
display(estadisticas)
```

### Lo que Debes Esperar del Analista

Cuando entregas un conjunto de datos debidamente ordenados, 
disminuye drásticamente la carga de trabajo del estadístico. 
Entonces, con suerte, te responderán mucho más rápido.
Pero la mayoría de los estadísticos cuidadosos verificarán tu procedimiento,
harán preguntas sobre las etapas que realizaste y tratarán de confirmar 
que pueden obtener los mismos datos ordenados que tú, al menos con verificaciones puntuales.

Deberías esperar del estadístico:

1. Un script de análisis que realice cada uno de los análisis (no solo instrucciones).
2. El código de computadora exacto que utilizaron para ejecutar el análisis.
3. Todos los archivos de salida/figuras que generaron.

Esta es la información que utilizarás 
para establecer la reproducibilidad y la precisión de tus resultados.
Cada uno de los pasos en el análisis debe estar claramente explicado y debes 
hacer preguntas cuando no entiendas lo que hizo el analista. Es responsabilidad 
tanto del estadístico como del científico comprender el análisis estadístico. 

Es posible que no puedas realizar los análisis exactos sin el código del estadístico,
pero deberías poder explicar por qué el estadístico realizó cada paso a un compañero de laboratorio o
a tu investigador principal.