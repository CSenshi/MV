### Table of Contents
* **[Setup](#Setup)**
* **[Car Classifier](#carclassifier)**
* **[HomeWork](#HomeWork)**

<a name="Setup"></a>

# Setup 

  #### Download
  * Currently using submodule [keras-YOLOv3-model-set](https://github.com/david8862/keras-YOLOv3-model-set)
    ```bash
    # Clone this repository
    git clone git://github.com/CSenshi/MV.git

    # Change directory to repository
    cd MV

    # Download keras submodule
    # destination directory: $(pwd)/YOLO
    git submodule update --init --recursive
    ```

  #### Virtual Environment ([venv](https://docs.python.org/3/library/venv))

  * Create venv
    ```bash
    python3 -m venv ./venv
    ```

  * Activate venv
    ```bash
    source venv/bin/activate
    ```

  * Install
    ```bash
    sudo apt install python3-opencv
    pip install Cython
    pip install -r requirements.txt
    ```

  * Deactivate venv
    ```bash
    deactivate
    ```

  #### Jupyter Notebook
  * Download Weights
    ```bash
    # change direcotry to keras-yolo submodule
    cd YOLO

    # Download Weights
    wget -O weights/yolov3-tiny.weights https://pjreddie.com/media/files/yolov3-tiny.weights

    # Convert to teras weights
    python  tools/model_converter/convert.py \
            cfg/yolov3-tiny.cfg \
            weights/yolov3-tiny.weights \
            weights/yolov3-tiny.h5
    ```

  * Run Jupyter Notebook
    ```bash
    jupyter notebook
    ```
  #### Error while rendering notebook on github?
  * It seems notebook rendering is problem in github. Try reloading few times, if problem still occures please open it via following link: <br>     https://nbviewer.jupyter.org/

<a name="carclassifier"></a>

# Car Classifier
script [detect_car_color.ipynb](detect_car_color.ipynb) is responsible for clasifying each car's pictures as interior or exterior. 

* Model used: [YOLO_np](https://github.com/david8862/keras-YOLOv3-model-set/blob/25bcf6bcc3187a6199b34dd46a00d916334ba656/yolo.py#L46)
* Wrapper function used: [predict()](https://github.com/david8862/keras-YOLOv3-model-set/blob/25bcf6bcc3187a6199b34dd46a00d916334ba656/yolo.py#L122)

Before running script:
```bash
  ...
  ├── 45976134
  ├── 45976135
  │   ├── 1.jpg
  │   ├── 2.jpg
  │   ├── 3.jpg
  │   ├── 4.jpg
  │   ├── 5.jpg
  │   ├── 6.jpg
  │   └── 7.jpg
  ├── 45976136
  ...
```

After script execution:
```bash
...
├── 45976134
├── 45976135
│   ├── exterior
│   │   ├── 2.jpg
│   │   ├── 5.jpg
│   │   ├── 6.jpg
│   │   └── 7.jpg
│   └── interior
│       ├── 1.jpg
│       ├── 3.jpg
│       └── 4.jpg
├── 45976136
...
```


<a name="HomeWork"></a>

# HomeWork
As for homework I took 3 exercises to work on
1. [Doors](detect_door_type.ipynb)
2. [Car Category](detect_car_type.ipynb)
3. [Car Color](detect_car_color.ipynb)

For all of those exerises I wrote one generic script that would work on all the given problems, with slight changes. As for model I created new model class that is subclass of `nn.Module` and as for base model I used `resnet18`.

  * Why Resnet?
  
    As for base model I had to choose between many models, but finally decided to choose between 3 models: Resnet, VGG, Densnet. I tried all of those model and results showed that VGG performs poorly (expected better results), so i had to throw it away. as for Densnet it is great model, but it was taking a lot of time, but model result wasn't as different as elapsed time for each model. So I choose to stay with model that takes small time (RESNET).
 
  * Why 18 layers?
  
    Resnet comes with 18, 34, 50, 101 and 152 layers. As results showed prediction is getting better only after 50 layers, but as it was in modeling, there is downside of time. It takes a lot of time than resnet 18, but for 34 layer it didn't act as good as i expeted. So after many tests I decided to stick with Resnet model with 18 layers, which is enough for given problems
