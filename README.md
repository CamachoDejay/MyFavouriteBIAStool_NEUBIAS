[![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

# MyFavouriteBIAStool_NEUBIAS
Favorite imaging analysis tools of NEUBIAS members - editor Kota Miura

The following contect works as supporting material for my article **"Jupyter Notebooks: my favourite tool for generating and distributing bioimage analysis pipelines"**


## 1) Python Installation using virtual environments

### Python virtual environments
There are many ways to install Python [e.g.1](https://wiki.python.org/moin/BeginnersGuide/Download) & [e.g.2](https://realpython.com/installing-python/), but in a nutshell, there is something to keep in mind: different projects might need different flavours of Python with different sets of libraries. This is why it is strongly recommended that you manage your Python installations via “virtual environments”. You can think of virtual environments as an isolated set-up of Python that you wish to use including libraries and their versions. They can easily be created, modified and shared. It is for this reason that we suggest an installation workflow that includes the installation of [miniconda](https://docs.conda.io/en/latest/miniconda.html), a tool that can manage multiple virtual environments.

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
## JupyterLab’s web interface
When we launch a Jupyter Notebook, we use the “IPython Kernel” in the background, a library that offers an interactive command line interface. You can think of IPython Kernel as the computer engine that runs the code contained in a Notebook document. ipykernel is installed alongside JupyterLab, and that is why we can use it directly. 

### 2) Starting JupyterLab’s web interface
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

## 7) Importing microscopy images and metadata into python
One critical aspect when handling microscopy images is the import of data from proprietary file formats and the correct handling of image metadata. Here, we can recommend to look at [AICSImageIO](https://github.com/AllenCellModeling/aicsimageio) a library to handle image reading, metadata conversion, and image writing for microscopy images in python. A minimal example can be found in their [quickstart](https://github.com/AllenCellModeling/aicsimageio#quickstart)

| Name and links | Description|
| ------------- | ------------- |
| ZeroCostDL4Mic [Github](https://github.com/HenriquesLab/ZeroCostDL4Mic) [Zenodo](https://doi.org/10.5281/zenodo.5059813)  | Collection of Jupyter Notebooks for Google Colab. Their purpose is to get users started on the use of deep learning for microscopy. It is designed for researchers with little or no coding experience. It includes examples of denoising, segmentation and object detection.  |
| py-clEsperanto [Github](https://github.com/clEsperanto/pyclesperanto)  | Python package of clEsperanto – a multi-language framework for GPU-accelerated image processing. The project is still under heavy development. It includes many Jupyter Notebook examples for segmentation, filtering, and general API examples.  |
| scikit-image [project site](https://scikit-image.org/) [GitHub](https://github.com/scikit-image/scikit-image)  | scikit-image is a collection of algorithms for image processing. These algorithms are the essential building blocks of BIAS workflows. It has great documentation and many examples that can be run interactively in the web browser with the help of binder. |
| as | AS|






