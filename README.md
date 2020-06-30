## Download
* Currently using submodule keras-YOLOv3-model-set
  ```bash
  git clone git://github.com/CSenshi/MV.git
  cd MV
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
* Run Jupyter Notebook
  ```bash
  jupyter notebook
  ```