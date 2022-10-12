# Practica Gravimetrica

Las mediciones de gravedad de la superficie de la Tierra no son óptimas para el estudio e interpretación de estructuras geológicas , ya que varios efectos se superponen y encubren las anomalias buscadas.De ahí la importancia de la separación y eliminación de estos de estos efectos indeseables de la gravedad medida, esto es fundamental para la gravimetría aplicada despues de las mediciones.A esto se le llama corrección/reducción de gravedad.
Las anomalías que se ven en esta práctica son:
- Anomalía Aire Libre
- Anomalía de Bouguer

La finalidad de la obtención de estas anomalías es ver la distribución de las masas.Los valores de las anomalías representan la frontera del geoide, estas fronteras implican dos
condiciones:
- La gravedad debe ser referida al geoide
-  Se deben remover las masas que estén fuera del geoide
Por tanto, estas correcciones y anomalías pretenden quitar lo que hay entre el geoide y lo que existe
encima o debajo de la parte topográfica, considerando una placa totalmente horizontal.
Cuando se quitan, las desplazamos debajo del nivel mar, lo cual la estación de gravedad (punto de
medición) es reducida desde la superficie hasta el geoide.

## Datos proporcionados

![image](https://user-images.githubusercontent.com/99137141/190489676-96e398df-dd4e-4ef2-98e8-c8e06a832637.png)

Teniendo en cuenta que "GRAV." es la gravedad observada 

## Fórmulas a utilizar 
 
 Lo primero a calcular es la Anomalía de Aire Libre
 
 ![image](https://user-images.githubusercontent.com/99137141/190489372-012a8d02-96a2-4a65-b166-1ebf3f5a14f6.png)

Donde:

- g_{obs } = gravedad observada 
- C_{gAl } = Correción por Aire Libre
- g_{\phi } = gravedad teórica

La fórmula a utilzar para obtener la corrección por Aire Libre es la siguiente:

![image](https://user-images.githubusercontent.com/99137141/190494905-360ec9e7-233f-42df-afac-3e278aae99fc.png)

Donde:
- \Delta h = la diferencia de alturas de la estación gravimetrica observada y la esatción gravimetrica fija
- altura de la esatción gravimetrica fija = 2332.724
- la altura de la estación observada es la elevación que aparece en los datos proporcionados

Para el cálculo de la gravedad teórica se uso la siguiente fórmula:

![image](https://user-images.githubusercontent.com/99137141/190496422-fdd1bd49-aeab-41ce-a3b8-e922953254f6.png)

Donde:
- \phi = es la latitud en radianes

La segunda Anomalía calcular es la de Bouguer:

![image](https://user-images.githubusercontent.com/99137141/190499680-ac0ce6ce-f7e8-4fc8-b6d7-2c28ab6875f6.png)

Donde:
- /Delta g_{obs} = gravedad observada
- C_{Al} = Corrección por Aire Libre
- C_{gb} = Corrección de Bouguer
- g_{\phi } = gravedad teórica

Para la correción de Bouguer se usará la siguiente fórmula:

![image](https://user-images.githubusercontent.com/99137141/190500821-67beb354-7057-4c80-b2f4-a07b4a29f784.png)

Donde:
- \rho = a la densidad de la corteza terrestre 

![image](https://user-images.githubusercontent.com/99137141/190501037-a0f9d05d-b407-4c66-a92e-f13296cc85e5.png)

Para hacer los cálculos con las misma unidades se tranformará la experesión anrterior

![image](https://user-images.githubusercontent.com/99137141/190501322-fa30592b-28bf-419c-a157-708947f18c79.png)

- \Delta h = la diferencia de alturas de la estación gravimetrica observada y la esatción gravimetrica fija
## Interpolación 


Las herramientas de interpolación IDW (distancia inversa ponderada) y Spline se conocen como métodos determinísticos de interpolación porque están basados directamente en los valores medidos o en fórmulas matemáticas específicas que determinan la suavidad de la superficie resultante. Hay una segunda familia de métodos de interpolación que consta de métodos geoestadísticos, como kriging, que está basado en modelos estadísticos que incluyen la autocorrelación, es decir, las relaciones estadísticas entre los puntos medidos. Gracias a esto, las técnicas de estadística geográfica no sólo tienen la capacidad de producir una superficie de predicción, sino que también proporcionan alguna medida de certeza o precisión de las predicciones.

Kriging presupone que la distancia o la dirección entre los puntos de muestra reflejan una correlación espacial que puede utilizarse para explicar la variación en la superficie. La herramienta Kriging ajusta una función matemática a un número específico de puntos o a todos los puntos dentro de un radio especificado, para determinar el valor de salida para cada ubicación. Kriging es un proceso que tiene varios pasos, entre los que se incluyen, el análisis estadístico exploratorio de los datos, el modelado de variogramas, la creación de la superficie y (opcionalmente) la exploración de la superficie de varianza. Este método es más adecuado cuando se sabe que hay una influencia direccional o de la distancia correlacionada espacialmente en los datos. Se utiliza a menudo en la ciencia del suelo y la geología.

### La fórmula de kriging

El método kriging es similar al de IDW en que pondera los valores medidos circundantes para calcular una predicción de una ubicación sin mediciones. La fórmula general para ambos interpoladores se forma como una suma ponderada de los datos:

![image](https://user-images.githubusercontent.com/99137141/195413670-829afec3-ca3f-4a93-af05-c5ec58575b07.png)

Donde: 
- Z(S_{i}) = el valor medio en la ubicación n.°i
- \lambda_{i} = un peso desconocido para el valor medio en la ubicación n.°i
- s_{0} = la ubicación de la predicción 
- N = el número de valores medidos

Con el método kriging, las ponderaciones están basadas no sólo en la distancia entre los puntos medidos y la ubicación de la predicción, sino también en la disposición espacial general de los puntos medidos. Para utilizar la disposición espacial en las ponderaciones, la correlación espacial debe estar cuantificada. Por tanto, en kriging ordinario, el peso, λi, depende de un modelo ajustado a los puntos medidos, la distancia a la ubicación de la predicción y las relaciones espaciales entre los valores medidos alrededor de la ubicación de la predicción.

Para fines de esta práctica, graficaremos los datos de las anomalias, así como aplicar una interpolación para cada una de ellas y el producto final nos de un archivo tipo raster con "countours" o "brakelines" para definir las curvas de nivel de los valores de las anomalías.

### Variografía

El ajuste de un modelo, o modelado espacial, también se conoce como análisis estructural o variografía. En el modelado espacial de la estructura de los puntos medidos, puede comenzar con un gráfico del semivariograma empírico, computado con la siguiente ecuación para todos los pares de ubicaciones separados por una distancia h:

Semivariogram(distanceh) = 0.5 * average((valuei – valuej)2)
La fórmula implica calcular la diferencia cuadrada entre los valores de las ubicaciones asociadas.

En la imagen a continuación se muestra la asociación de un punto (en color rojo) con todas las demás ubicaciones medidas. Este proceso continúa con cada punto medido.

![image](https://user-images.githubusercontent.com/99137141/195416770-42d01b96-c3c8-42f9-ac26-9dd9cb0caed6.png)
