# Tesis-Memristores-Rozenberg
Todos los archivos tienen formato .ipynb  
Descargar todos los archivos y alojar en un mismo directorio.

## Programas:

### Modelo de Rozenberg 5.6i Pyspice.ipynb
Main program: Define los parámetros de los memristores, crea los arreglos espaciales y la señal eléctrica aplicada y resuelve la red durante el ciclo del experimento llamando a las funciones Memristorfunction y PySpicefunction. Exporta los resultados del experimento en una carpeta dentro del directorio (gráfico y archivos csv)  
- tVI.csv exporta el numero de step del experimento (t), el voltaje (V) y la corriente total (I)  
- states.csv exporta para cada step del experimento (t) los valores de resistencia eléctrica de cada memristor que compone la red.  

### PySpicefunction.ipynb
Función pyspice: calcula la caída de tensión en cada nodo de la red de memristores utilizando NGSPICE.

### Memristorfunction.ipynb
Función memristor individual. Permite calcular la variación de resistencia de cada memristor individual y la migración de vacancias por cada estimulo aplicado. Requiere como imput la diferencia de potencial en cada memristor, que se calcula mediante PySpicefunction.ipynb

### Analyzing-memristive-arrays_VEOV.ipynb
Este programa realiza un análisis y reestructura los datos previamente exportados. Exporta diversos gráficos y el archivo Remnant-resistance-state.csv, donde guarda el valor de la resistencia remanente de la red (es decir la resistencia de la red en aquellos puntos donde la tensión aplicada a la red es nula). Este archivo es necesario para poder graficar los mapas de calor utilizando Maps_VEOV_v2. 

### Maps_VEOV_v2.ipynb
Este programa grafica los estados de resistencia remanente (resistencia eléctrica cuando la señal externa de la red es cero) para cada memristor individual de la red como un mapa de calor. Este programa requiere el archivo "states.csv" para graficar los mapas.  
Para poder ejecturar Maps_VEOV_v2.ipynb, se debe crear en el directorio una carpeta llamada /simulations_n/. En esa carpeta se debe copiar el archivo “states.csv” del experimento que se desee graficar, y también dentro de la carpet /simulations_n/ debe crearse una subcarpeta /fig/ donde se guardaran los mapas creados. Una vez hecho esto, se puede ejecutar el programa.  


## Instalacion de PySPICE para Anaconda 3 en Windows:

Para conectar un código en Python con SPICE open source (el NG es uno de ellos) empleamos la herramienta PySPICE.  
Para instalarla, se debe iniciar Anaconda 3, abrir una consola (Jupyter QtConsole) y ejecutar la siguiente instrucción:   

*conda install -c conda-forge pyspice*  

Con esta instruccion se instalan tanto PySPICE como el propio motor de simulación NGSPICE

