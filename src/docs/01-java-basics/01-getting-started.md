
# Getting Started


1. check java 
2. check python
3. install pyspark
4. install jupyter

### java
To see if java is installed, otherwise install java
```text
java -version
openjdk version "17.0.7" 2023-04-18 LTS
```

### python
To see if python is installed, otherwise install python
```text
python3 --version
Python 3.9.6
```


### pyspark

https://spark.apache.org/docs/latest/api/python/getting_started/install.html#using-pypi

```text
pip3 install pyspark
```
#### Run 
```text
pyspark

...
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 3.4.0
      /_/

Using Python version 3.9.6 (default, Mar 10 2023 20:16:38)
...
```


### jupyter
```text
pip3 install jupyter
```


#### Run

```text
jupyter notebook
```
- A browser will open with a notebook
- Create a New Notebook


```python
import findspark
findspark.init()

import pyspark
import random

sc = pyspark.SparkContext(appName="Pi")
num_samples = 100000000

def inside(p):     
  x, y = random.random(), random.random()
  return x*x + y*y < 1
  
count = sc.parallelize(range(0, num_samples)).filter(inside).count()
pi = 4 * count / num_samples
print(pi)

sc.stop()
```
It will print:  3.14159256
This the Monte Marlo method to calculate the value of PI


### trouble shouting

If `jupyter` does not work, maybe <python>/bin is not on the PATH
You maybe did get a warning after the installation of jupyter

You can add it to the path on Mac Terminal (example)
```text
nano ~/.zshrc

export PATH=/Users/littleworld/Library/Python/3.9/bin:$PATH
```





