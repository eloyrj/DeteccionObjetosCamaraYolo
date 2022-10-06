# Detección de objetos usando yolov5

<details open>
<summary>Instalación</summary>

Clonar el repositorio e instalar [requirements.txt](https://github.com/ultralytics/yolov5/blob/master/requirements.txt) usando
[**Python>=3.7.0**](https://www.python.org/), ademas de 
[**PyTorch>=1.7**](https://pytorch.org/get-started/locally/).
Recomendado el uso de [**Anaconda**](https://www.anaconda.com/products/distribution) (en este proceso estara presente aunque no es necesario)


```bash
git clone https://github.com/ultralytics/yolov5  # clonación del repositorio
cd yolov5

conda create -n deteccionObj python=3.7 #Creación de un ambiente usando python 3.7 en anaconda.
conda activate deteccionObj #activación del ambiente de anaconda

pip install -r requirements.txt  # Instalacion de los requisitos.
```

</details>

<details open>
<summary>Entrenamiento</summary>

Para entrenar la IA necesitamos antes un pull de imagenes etiquetadas.

Siempre podemos buscar en internet algún dataset ya etiquetado, para esto hay paginas como [**Open Images Dataset**](https://storage.googleapis.com/openimages/web/visualizer/index.html?set=train&type=detection&c=%2Fm%2F01m2v), que pertenece a Google y dispone de numerosas imágenes ordenadas por clases.

Sin embargo, hay muchas clases que no se encuentran presentes en estas páginas, como por ejemplo el caso que nos concierne: drones. Lo que haremos es buscar en Google imágenes de drones en situaciones naturales, y las guardaremos en nuestra maquina.

Ahora usaremos una herramienta de etiquetado para etiquetar dichas imágenes. En este caso, usaremos [**Label Studio**](https://labelstud.io/).

![](https://repository-images.githubusercontent.com/192640529/970b6900-817b-11eb-9f57-adf3f87c6ff9)

Una vez las imágenes estén etiquetadas, tendremos que colocar las imágenes y las etiquetas separadas en datos de entrenamiento y de validación.

De esta forma:

- images
    - train
    - val
-  labels
    - train
    - val

Ahora necesitaremos crear un archivo .yaml en el que definamos tanto las clases de nuestro entrenamiento como las rutas de los distintos datos

```yalm
# Train/val/test sets as 1) dir: path/to/imgs, 2) file: path/to/imgs.txt, or 3) list: [path/to/imgs1, path/to/imgs2, ..]
path: ../yolov5-master/data/datasets/p2  # direccion del dataset
train: images/train  # train images (relative to 'path') 128 images
val: images/val  # val images (relative to 'path') 128 images
test:  # test images (optional)

# Classes
names:
  0: dron
```

Una vez ya hemos preparado todos los datos toca entrenar. Para ello usaremos la clase **train.py**.

```bash 
python train.py --weights '' --cfg models/yolov5m.yaml --data data/drones.yaml
```

donde:
- data = el .yaml configurado previamente
- cfg = tipo de entrenamiento que haremos, podemos aceder a 5 con distintas configuraciones.
  ![](https://github.com/ultralytics/yolov5/releases/download/v1.0/model_comparison.png)
- weights = un peso de un entrenamiento anterior al cual se le añadan los datos nuevos con extension .pt.

</details>

<details open>
<summary>Ejecución</summary>
Si la ejecucion va a ser con el dataset que trae yolov5 por defecto que contiene 80 clases distintas deberas usar

```bash 
python detect.py --source 0 #para usar la cam
                          img.jpg  # imagen
                          vid.mp4  # video
                          screen  # screenshot
                          path/  # directory
                          'path/*.jpg'  # glob
                          'https://youtu.be/Zgi9g1ksQHc'  # YouTube
                          'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```
Si usted a entrenado su popio dataset entonces debera decirlo usando --weights.

```bash 
python detect.py --source 0 --weights /dir/to/peso.pt
```
</details>