[![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

# MyFavouriteBIAStool_NEUBIAS
Favorite imaging analysis tools of NEUBIAS members - editor Kota Miura

The following contect works as supporting material for my article **"Jupyter Notebooks: my favourite tool for generating and distributing bioimage analysis pipelines"**


## 1) Python Installation using virtual environments

### 1.1) Installing miniconda: 
Miniconda is a free minimal installer for conda. The latest installation instructions can be found at:
https://docs.conda.io/en/latest/miniconda.html  

Once installed you should have access to the “Anaconda Prompt”. To test your installation, simply open the Anaconda Prompt, and then write the command:
```
> Python
```
This should open Python in your terminal. Notice the “>>>” in the prompt. To exit Python you can run the command:
```
>>> quit()
```
### 1.2) Create a virtual environment that will be used to install Jupyter Lab. 
**Note** that we will use python 3.9 to be compatible with Napari. Go to the Anaconda Prompt and run the command:
```
> conda create -y -n jupyter-env -c conda-forge python=3.9
```
### 1.3) Activate environment
Once the virtual environment with the name jupyter-env is created, then you can activate it to install the desired packages.
```
> conda activate jupyter-env
```
**Note** how the terminal now starts with (jupyter-env)
### 1.4) Install JupyterLab 
Now we install JupyterLab in the environment using
```
> conda install -c conda-forge jupyterlab
```
### 1.5) Make virtual environment available to JupyterLab
To make our current environment (kernel) available to JupyterLab we use:
```
> ipython kernel install --user --name=jupyter-env
```

## 2) Starting JupyterLab’s web interface
Starting JupyterLab is very simple. 
### 2.1) Open the anaconda prompt
Open the anaconda prompt and navigate to the desired folder. Below is an example using an empty folder named “jlab” in my “Documents” folder. 
```
> cd Documents/jlab
```
### 2.2) Activate appropiate environment
Make sure you have activated the ```jupyter-env``` environment (see above installation procedure). Then run the command:
```
> jupyter lab
```
A web browser should open with the address: http://localhost:8888/lab

## 3) Creating a new Jupyter Notebook
You can find great documentation on [how to create Notebooks using JupyterLab](https://jupyterlab.readthedocs.io/en/stable/user/notebook.html). Bellow is a minimal example:

3.1) Go to the JupyterLab web interface. 

3.2) Go to File > New > Notebook

3.3) Select the Kernel we have created: ```jupyter-env```

3.4) Go to File > Save Notebook to rename your file as desired: e.g., ```Example.ipynb```

## 4) Notebook Cells
A Notebook’s cell can contain either live code, or documentation information in the form of formatted text via [Markdown](https://daringfireball.net/projects/markdown/), see for example Figure 02 of the manuscript. To start exploring Notebook Cells write the following on the first cell of your example notebook:
```
[ ] print(‘Hi bioimage analyst’)
```
Then you can use “ctr + enter” to run the current cell. 

## 5) Simple BIAS Python setup
A bare Jupyter Notebook is not going to take us very far if we try to solve a BIAS problem. To follow the examples depicted in Figures 1-3 of the article we must install ```scikit-image```, which is a collection of algorithms for image processing written in Python, ```matplotlib``` for creating figures, and ```pandas``` to handle tabular data.

5.1) Go to the Anaconda Prompt

5.2) Activate the jupyter-env
```
> conda activate jupyter-env
```

5.3) Install scikit-image, matplotlib, and pandas by

```
> conda install -c conda-forge scikit-image matplotlib pandas
```
5.4) Go to the desired path, and start JupyterLab
```
> jupyter lab
```

## 6 Sharing your virtual environment with others

6.1) Activate the environment to export, e.g. our Jupyter.env
```
> conda activate Jupyter-env
```
6.2) Export the active environment to a file
```
> conda env export > environment.yml
```
6.3) Email a copy of this file together with the Notebook file.

6.4) Instruct your collaborator to create the environment locally from the environment.yml file via:
```
> conda env create -f environment.yml
```