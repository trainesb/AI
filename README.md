# AI

## Setup Virtual Enviornment
Install _Virtualenv_
```
pip3 install -U pip virtualenv
```
Create a virtuale enviornment in your project directory
```Python
cd my_project
virtualenv env
```
Activate virtual enviornment
```python
./env/Scripts/activate
```
Upgrade pip
```
pip install --upgrade pip
pip list # show packages installed within the virtual enviornment
```
Exit virtual enviornment
```
deactivate
```

## Install TensorFlow
Choose what package you want to install:
  - ```tensorflow``` - Latest stable release (2.x) for CPU_only
  -```tensorflow-gpu``` - Latest stable release with GPU support _(Ubuntu & Windows)_
  -```tf-nightly``` - Unstable build with GPU support _(Ubuntu & Windows)_
  -```tensorflow==1.15``` - The final version of TensorFlow 1.x
 ```
 pip install --upgrade tensorflow
 ```
 test installation:
 ```
 python -c "import tensorflow as tf;print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
 ```
