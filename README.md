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

Siempre podemos buscar en internet algun dataset ya etiquetado, para esto hay paginas como [**Open Images Dataset**](https://storage.googleapis.com/openimages/web/visualizer/index.html?set=train&type=detection&c=%2Fm%2F01m2v) que es de google y dispone de muchas imagenes ordenadas por clases.

Sin embargo hay muchas clases que no se encuentran, por ejemplo en el caso que usaremos, que son drones, lo que haremos es buscar en google imagenes de drones en situaciones naturales, y las guardatemos en nuestra maquina.

Ahora usaremos una herramienta de etiquetado para etiquetar dichas imagenes en este caso usaremos [**Label Studio**](https://labelstud.io/).

![](https://www.google.com/imgres?imgurl=https%3A%2F%2Frepository-images.githubusercontent.com%2F192640529%2F970b6900-817b-11eb-9f57-adf3f87c6ff9&imgrefurl=https%3A%2F%2Fgithub.com%2Fheartexlabs%2Flabel-studio&tbnid=AP9NTGMQ_ZnSOM&vet=12ahUKEwju2OykpMv6AhViTUEAHZYnBHEQMygBegUIARC5AQ..i&docid=tlkZyAZPq9EDDM&w=2629&h=1521&q=label%20studio&ved=2ahUKEwju2OykpMv6AhViTUEAHZYnBHEQMygBegUIARC5AQ)

</details>