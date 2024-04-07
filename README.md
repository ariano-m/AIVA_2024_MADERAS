# AIVA_2024_MADERAS

Desarrolladores de VisionaryAI:
 - Adrián Riaño Martínez
 - Irene García Rubio

## Índice
1. [Introducción](#id1)
2. [Base de datos](#id2)
3. [Despliegue](#id3)


## Introducción <a name="id1"></a>
La empresa **El Bosque de Juguetes** se dedica a realizar juguetes de maderas de forma manual. Para ello, obtiene una tabla de madera, toma una foto y con un software dibuja las piezas de un tamaño predefinido.
El trabajador se enfrenta a que el proceso manual requiere mucho tiempo y considera que la automatización le reportará más beneficios por el aumento de producción. Por tanto, en este proyecto, se propone el diseño de un sistema de visión artificial que sea capaz de reconocer los defectos en las tablas de madera y decida la posición de las piezas a obtener. 
Uno de los requerimientos del cliente se trata de que el sistema trabaje sobre un aplicación móvil, ya que es la herramienta que utiliza. Con este motivo, se plantea una arquitectura cliente-servidor. El cliente (móvil) tomará una foto, y la aplicación se conectará al servidor para enviarle la imagen. Después, el servidor realizará los cálculos y devolverá el resultado al cliente.

El sistema desarrollado para resolver esta necesidad se conoce como **ToyWoodVision** y se encargará de su implementación la compañía **VisionaryAI**.

## Base de datos <a name="id2"></a>
La base de datos proporcionada por el cliente es una recopilación de 79 imágenes de tablones de madera sobre fondo negro. Aunque la iluminación parece constante, hay un cierto número de imágenes que presentan una tonalidad de madera más oscura.

![](https://github.com/ariano-m/AIVA_2024_MADERAS/blob/main/dataset/MuestrasMaderas/36.png)
![](https://github.com/ariano-m/AIVA_2024_MADERAS/blob/main/dataset/MuestrasMaderas/37.png)

Parte de la solución a implementar consiste en detectar los nodos o grietas que pueda presentar la madera.
- Los nodos se definen como el área de tejido leñoso resultante de la huella dejada por el desarrollo de una rama.
- Las grietas son la separación de las fibras (corte o hendidura) en dirección longitudinal.

![](https://github.com/ariano-m/AIVA_2024_MADERAS/blob/main/dataset/MuestrasMaderas/25.png)

## Despliegue <a name="id3"></a>
### Preparación del entorno
```
git clone https://github.com/ariano-m/AIVA_2024_MADERAS.git
cd AIVA_2024_MADERAS
```
### Instalar requisitos

- Se ha de disponer de Python 3.10.
- Un listado de las librerías utilizadas y de sus versiones se puede encontrar en [requirements.txt](https://github.com/ariano-m/AIVA_2024_MADERAS/blob/main/requirements.txt).

Para instalarlas únicamente para este proyecto se puede crear un entorno virtual con el siguiente comando:
```
python -m venv venv
```
Para activar el entorno virtual se a de ejecutar el archivo _activate_.

En Unix o MacOS, ejecuta:
```
source venv/bin/activate
```
En Windows, ejecuta:
```
venv\Scripts\activate.bat
```
Para instalar los requisitos del proyecto:
```
pip install -r requirements.txt
```
Asegurarse de que el directorio actual está en el path de python.

En Unix o MacOS, ejecuta:
```
export PYTHONPATH="${PYTHONPATH}:/my/other/path"
export PYTHONPATH=$PYTHONPATH:'pwd'
```
En Windows, ejecuta:
```
set PYTHONPATH=%PYTHONPATH%;C:\My_python_lib
```

### Lanzar programa
Primero se ha de estar en la carpeta del proyecto donde se situa main.py. 

Esta se encuentra en _AIVA_2024_MADERAS/bin/server/system/main.py_.
```
cd bin/server/system/
```
El comando para ejecutar el sistema y que este nos devuelva una imagen con las piezas colocadas sería el siguiente:
```
python.exe <ruta donde se encuentra el main.py> --img_path <ruta de la imagen>
```
Un ejemplo, si nos encontramos en la carpeta _system_:
```
python.exe main.py --img_path ../../../dataset/MuestrasMaderas/10.png
```

### Lanzar test
Al igual que la anterior vez, se ha de ir a la carpeta donde se encuentran los test.
En este caso es _AIVA_2024_MADERAS/bin/server/tests_.
```
cd bin/server/tests
```
El comando para ejecutar el test sería el siguiente:
```
python.exe <ruta donde se encuentra el test.py> <ruta del modelo (opcional dependiendo del test)> <ruta de la imagen>
```
Un ejemplo, si nos encontramos en la carpeta _system_:
Para el test_system:
```
python.exe test_system.py ../../../dataset/MuestrasMaderas/10.png
```
Pata el test_model:
```
python test_model.py ../models/Yolo_Training2/weights/best.pt ../../../dataset/MuestrasMaderas/62.png
````
