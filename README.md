## setup an auto-sklearn environment with conda

### General info to conda vs pip
Compared to a pip virtual env, a conda environment has the advantage that you can install python packages AND packages for other languages within one virtual environment. Furthermore, some packages are solely available for conda and some only for pip. By creating a conda environment you can install and use both package manager (pip and conda).
Pip is preinstalled in conda environments, so you don’t need to install it


### Set up your conda environment
Before you can create a conda environment you need to install miniconda on your system. https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html

The following commands applies to Linux systems. I don't have any experience with conda on Windows.

If you have installed miniconda, you can create your virtual environment with the following command:
```
$ conda create --name myenv python=3.7 (or higher version)  
```  

#### _The following is based on the installation manual of autosklearn ( see https://automl.github.io/auto-sklearn/master/installation.html#installation )_

You need a C++ Compiler. Almost all Linux distros come with GCC installed. Check whether GCC is installed on your system by entering the following command from the command line.
```
$ g++ -v
```

If you don’t have a C++ compiler and you like to use GCC install it according to https://gcc.gnu.org/install/

When you have a C++ compiler,  install SWIG
```
$ conda install -c anaconda swig
```
Then install the quite specific dependencies via
```
$ curl https://raw.githubusercontent.com/automl/auto-sklearn/master/requirements.txt | xargs -n 1 -L 1 pip3 install
```

install autosklearn
```
$ pip install auto-sklearn
```

### Adding conda environments to Jupyter notebooks
Adding conda environment as kernels can be tricky. I ended up with the following commands, which reliably add the environments as kernels to JNs

Activate the conda environment
```
§ conda activate myenv
```
In the environment, to work in jupyter notebook install ipykernel:
```
$ conda install -c anaconda ipykernel
```

In the environment give the command:
```
$ python -m ipykernel install --user --name mykernel
```
