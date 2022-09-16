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
Para fines de esta práctica, graficaremos los datos de las anomalias, así como aplicar una interpolación para cada una de las anomalías y el producto final nos de un archivo tipo raster con "countours" o "brakelines" para definir las curvas de nivel de los valores de las anomalías.

