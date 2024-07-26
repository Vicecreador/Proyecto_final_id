# Proyecto_final_id
En este escrito se van a comparar diferentes modelos para poder predecir ventas en la industria farmacéutica. Este análisis se establecerá a partir de un dataset previamente modificado para englobar las ventas diarias en 8 grupos de fármacos, atendiendo a su función farmacológica, y evitar así datos confidenciales.

Los 8 grupos de fármacos en los que han quedado distribuidos los 57 fármacos iniciales, así como su nominación en este proyecto son los siguientes:

M01AB - Anti-inflammatory and antirheumatic products, non-steroids, Acetic acid derivatives and related substances
M01AE - Anti-inflammatory and antirheumatic products, non-steroids, Propionic acid derivatives
N02BA - Other analgesics and antipyretics, Salicylic acid and derivatives
N02BE/B - Other analgesics and antipyretics, Pyrazolones and Anilides
N05B - Psycholeptics drugs, Anxiolytic drugs
N05C - Psycholeptics drugs, Hypnotics and sedatives drugs
R03 - Drugs for obstructive airway diseases
R06 - Antihistamines for systemic use


Para este análisis se va a utilizar Prophet, una herramienta específicamente creada para la previsión de datos de series temporales. Esta herramienta tiene como base un modelo aditivo en el que las tendencias no lineales se ajustan con la estabilidad anual, semanal y diaria. Se ha escogido Prophet para este análisis en concreto porque, en comparación con otros modelos clásicos parecidos, como ARIMA, Prophet ha demostrado en otros estudios que es más eficaz prediciendo las ventas a largo plazo. En un ambiente como la industria farmacéutica, donde estar actualizado frecuentemente supone un esfuerzo económico considerable, esto es especialmente beneficioso. También se ha escogido por su capacidad para analizar eficientemente los valores atípicos de un conjunto de datos.

En lo referente al proyecto, se ha comenzado por hacer un análisis EDA del dataset, seguido de una representación gráfica de las series temporales individualizadas de cada uno de los fármacos. Al notar una posible estacionalidad en los datos, se realiza una prueba de Dickey-Fuller aumentada. Esta prueba tuvo como resultado que todas los grupos de fármacos presentaban series de tiempo estacionarias. Se estudia también la estacionalidad de cada grupo de fármacos, así como los “outliners” usando un boxplot que presenta las tendencias por día de la semana.

Se comparó la evolución de las ventas de los fármacos a lo largo de 6 años usando para su representación los datos de 365-d rolling means. Usando así la media del último año en cada valor para poder tener una representación con un mayor suavizado de datos, una reducción del ruido estacional y una mejor visión de las tendencias a largo plazo. Después se compara con los datos sin aplicar una media de los datos más recientes del dataset y su tendencia a un nivel reciente.

Se utiliza Prophet para realizar un modelo de predicción de ventas de fármacos, empezando por los grupos M01AB, N02BE, N05C y R06. M01AB por ser el caso prototípico para representar a la mayoría de los demás, N02BE por representar las mayores ventas, N05C por representar las menores ventas, y R06 por representar una mayor variabilidad con respecto a las ventas por fecha. Se han usado los datos diarios, semanales y mensuales para comprobar cual era más fiable en cada caso. Se han medido los errores en la medida en forma de tres métricas. El MAE o error absoluto medio, el MSE o error cuadrático medio, y el RMSE o Error medio con raíz cuadrada. Todos los modelos han dado errores aceptables, sobre todo en el uso de valores mensuales, lo que confirma la utilidad de los modelos.
