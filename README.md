## Download
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

## Virtual Environment ([venv](https://docs.python.org/3/library/venv))

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

## Jupyter Notebook
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
## Error while rendering notebook on github?
* It seems notebook rendering is problem in github. Try reloading few times, if problem still occures please open it via following link:

https://nbviewer.jupyter.org/

## Car Detection Model
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
