[![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

# Jupyter Notebooks for Generating and Distributing Bioimage Analysis Workflows

The following contect works as supporting material for my article [**"Jupyter Notebooks for Generating and Distributing Bioimage Analysis Workflows"**](https://analyticalscience.wiley.com/do/10.1002/was.0004000374), which is part of the 
My Favorite Image Analysis Tool series, by Neubias Members - editor Kota Miura


## 1) Python & JupyterLab Installation using virtual environments

The Jupyter Notebook is available as a part of JupyterLab, so my recommendation is to install JupyterLab as it is the latest generation of the Jupyter project. While JupyterLab is itself a useful development environment, other Integrated Development Environments have great support for Jupyter Notebooks and allow for customization and ease of use, such as [PyCharm](https://www.jetbrains.com/help/pycharm/jupyter-notebook-support.html) and [VSCode](https://code.visualstudio.com/docs/datascience/jupyter-notebooks).

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

The managing of environments is an interesting topic in its own right and good documentation can be found at the [anaconda site](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).

## 7) Importing microscopy images and metadata into python
One critical aspect when handling microscopy images is the import of data from proprietary file formats and the correct handling of image metadata. Here, we can recommend to look at [AICSImageIO](https://github.com/AllenCellModeling/aicsimageio) a library to handle image reading, metadata conversion, and image writing for microscopy images in python. A minimal example can be found in their [quickstart](https://github.com/AllenCellModeling/aicsimageio#quickstart)

## 8) Python resources for bioimage analysis
Here I point at a few key resources and libraries that I believe are a great starting point, followed by a more comprehensive table of resources:

### The Image.sc Forum
A scientific community forum for discussing image analysis software: [link to the Forum](https://forum.image.sc/). Many bioimage analysts and developers are available at the forum and it is a great place to ask Python BIAS-related questions.
### scikit-image 
A collection of algorithms for image processing written in Python [project site](https://scikit-image.org/). It has great documentation, implementation examples, and an active community that can be reached via its website, or the Image.sc forum.

### The Napari community
[Napari](https://napari.org/stable/) is a fast, and interactive multi-dimensional image viewer for Python. It has a fast-evolving and engaging community of users and developers which can be reached via the Image.sc forum. Further, Napari’s functionality can be extended via the use and development of [plugins](https://www.napari-hub.org/).

### py-clEsperanto 
A multi-language framework for GPU-accelerated image processing [GitHub site](https://github.com/clEsperanto/pyclesperanto). It also includes a Napari plugin that allows exporting Python Jupyter Notebooks of the implemented workflow, which is great for learning to code py-clEsperanto workflows. Developers and users can be reached via the Image.sc forum.

| Name and links | Description|
| ------------- | ------------- |
| scikit-image [project site](https://scikit-image.org/) [GitHub](https://github.com/scikit-image/scikit-image)  | scikit-image is a collection of algorithms for image processing. These algorithms are the essential building blocks of BIAS workflows. It has great documentation and many examples that can be run interactively in the web browser with the help of binder. |
| py-clEsperanto [Github](https://github.com/clEsperanto/pyclesperanto)  | Python package of clEsperanto – a multi-language framework for GPU-accelerated image processing. The project is still under heavy development. It includes many Jupyter Notebook examples for segmentation, filtering, and general API examples.  |
| AICSImageIO [GitHub](https://github.com/AllenCellModeling/aicsimageio) [Zenodo](https://doi.org/10.5281/zenodo.7407014)  | Python library for image reading, metadata conversion and image writing for microscopy images in pure Python. It has an extensive [documentation](https://allencellmodeling.github.io/aicsimageio/index.html) |
| ome-zarr-py [GitHub](https://github.com/ome/ome-zarr-py) | Python library for reading and writing multi-resolution images stored as Zarr filesets, according to the OME-NGFF specification. |
| Napari [Main-site](https://napari.org/stable/) [Tutorials](https://napari.org/stable/tutorials/index.html) | Napari is a fast, and interactive multi-dimensional image viewer for Python. Due to its integration with the Python ecosystem Napari can be easily coupled to BIAS and machine learning workflows. Further, they host a series of tutorials containing many useful minimal examples. |
| Image.sc forum [Main-site](https://forum.image.sc/) | Scientific community forum for discussing image analysis software. Many bioimage analysts and developers are available at the forum and it is a great place to ask Python BIAS-related questions. |
| Bio-image Analysis Notebooks [Main-site](https://haesleinhuepf.github.io/BioImageAnalysisNotebooks/intro.html) [Zenodo](https://doi.org/10.5281/zenodo.5894792)   | Collection of Jupyter Notebooks written in Python for beginners interested in analysing 3D images. It is writer for biologists with little coding experience. It also contains links to many other resources such as videos, other guides, and Python libraries. |
| NEUBIAS Academy @HOME: Interactive Bioimage Analysis with Python and Jupyter. [GitHub](https://github.com/guiwitz/neubias_academy_biapy) [Zenodo](https://doi.org/10.5281/zenodo.5122158)  | Introductory course to bioimage processing with Python and Jupyter. The GitHub repository contains a series of Jupyter Notebooks that can be used via binder, Google Colab, or via local installation. The course material also includes a recording of the lecture available on YouTube. |
| Web-book Introduction to Bioimage Analysis [Main-site](https://bioimagebook.github.io/index.html) | This book covers main ideas of image analysis in a practical way. It is written for biologist with little BIAS or coding experience. The book contains many examples written in Python or in the ImageJ macro language. |
| IAFIG-RMS Python for Bioimage Analysis Course [GitHub](https://github.com/RMS-DAIM/Python-for-Bioimage-Analysis) | Course from the Image Analysis Focused Interest Group of the Royal Microscopical Society (IAFIG-RMS). This is the supporting material of a week-long course on BIAS. The target audience is biologists and analysts with some experience of basic microscopy and image analysis. Most topics are supported via practical Jupyter Notebooks. |
| Image Analysis Training Resources by NEUBIAS [Main-site](https://neubias.github.io/training-resources/index.html) | This material is mainly aimed at helping bioimage analysis trainers when designing courses. Moreover, the material presents many minimal examples written in Python (and other languages) that are very useful for beginner and advanced analysts alike. |
| Bio-image Analysis with Python[GitHub](https://github.com/BiAPoL/Bio-image_Analysis_with_Python) | Lecture materials "Bio-image analysis, biostatistics, programming and machine learning for computational biology" at the Center of Molecular and Cellular Bioengineering (CMCB) |
| ZeroCostDL4Mic [Github](https://github.com/HenriquesLab/ZeroCostDL4Mic) [Zenodo](https://doi.org/10.5281/zenodo.5059813)  | Collection of Jupyter Notebooks for Google Colab. Their purpose is to get users started on the use of deep learning for microscopy. It is designed for researchers with little or no coding experience. It includes examples of denoising, segmentation and object detection.  |
| CSBDeep [GitHub](https://github.com/CSBDeep/CSBDeep) | Python package providing a toolbox for content-aware restoration of fluorescence microscopy images (CARE), based on deep learning via Keras and TensorFlow |
| Stardist [GitHub](https://github.com/stardist/stardist)| Deep learning alorithm for detecting nucleous or other start-convex objects in microscopy images |
| Cellpose [GitHub](https://github.com/MouseLand/cellpose) | Generalist algorithm for cellular segmentation with human-in-the-loop capabilities. |
| Open Application Development (OAD) by ZEISS microscopy [GitHub](https://github.com/zeiss-microscopy/OAD) | ZEN blue offers various features for automating microscopy workflows and image analysis via Python. This repository contains many Jupyter Notebook examples. |







