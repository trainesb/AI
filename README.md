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
 
 ## [Datasets](https://github.com/tensorflow/datasets) 
 Install tensorflow_datasets
 ```
 pip install --upgrade tensorflow_datasets
 ```
 dataset class archetecture:
 ```
     tfds.core.DatasetInfo(
        name='mnist',
        version=1.0.0,
        description='The MNIST database of handwritten digits.',
        homepage='http://yann.lecun.com/exdb/mnist/',
        features=FeaturesDict({
            'image': Image(shape=(28, 28, 1), dtype=tf.uint8),
            'label': ClassLabel(shape=(), dtype=tf.int64, num_classes=10)
        },
        total_num_examples=70000,
        splits={
            'test': <tfds.core.SplitInfo num_examples=10000>,
            'train': <tfds.core.SplitInfo num_examples=60000>
        },
        supervised_keys=('image', 'label'),
        citation='"""
            @article{lecun2010mnist,
              title={MNIST handwritten digit database},
              author={LeCun, Yann and Cortes, Corinna and Burges, CJ},
              journal={ATT Labs [Online]. Available: http://yann. lecun. com/exdb/mnist},
              volume={2},
              year={2010}
            }
      """',
  )
 ```
Usage
```
import tensorflow_datasets as tfds
import tensorflow as tf

# tfds works in both Eager and Graph modes
tf.compat.v1.enable_eager_execution()

# See available datasets
print(tfds.list_builders())

# Construct a tf.data.Dataset
ds_train = tfds.load(name="mnist", split="train", shuffle_files=True)

# Build your input pipeline
ds_train = ds_train.shuffle(1000).batch(128).prefetch(10)
for features in ds_train.take(1):
  image, label = features["image"], features["label"]
```
