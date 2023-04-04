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
