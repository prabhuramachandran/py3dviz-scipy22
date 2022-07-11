# Pythonic 3D visualization

This repository contains the material for the tutorial at SciPy 2022 conducted
by Prabhu Ramachandran and Matt McCormick.


This tutorial will introduce the participants to 3D visualization using tools
that are written with rendering support from VTK library (https://vtk.org/).
We start the workshop with Mayavi (https://github.com/enthought/mayavi) then
some [itkwidgets](https://github.com/InsightSoftwareConsortium/itkwidgets)
Mayavi is an Open Source, Python package for general purpose 3D visualization
and provides a very Python-friendly API. itkwidgets are interactive Jupyter
widgets to visualize images, point sets, and meshes.  Mayavi makes use of VTK,
and itkwidgets supports VTK data structures and supports VTK-based rendering.

The tutorial will provide an overview of 3D visualization in Python.  Then, we
will introduce Mayavi, itkwidgets, and VTK and what they can offer for the
scientist/researcher. The tutorial wil cover mechanisms, behavior, benefits,
and requirements of client-side and server-side rendering.  We will then use
the `mayavi.mlab` module to quickly produce visualizations that are useful
for scientists and engineers with a minimum of effort. This will cover several
basic visualizations. We then move on to exploring VTK datasets and how they
may be easily created using NumPy arrays and quickly visualized with Mayavi.


We will then explore visualizing the data on a Jupyter notebook followed by
the creation of custom ipywidget Jupyter applications for large images and
meshes with the itkwidgets package along with Mayavi. We will explore the
generation of graphical applications from Python dashboarding and Jupyter
notebook system. We will learn how to use 3D visualization to improve deep
learning model development.



## Installation instructions

Attendees should have a computer with any Python version > 3.6. We primarily
require that you have Mayavi and itkwidgets installed.

### Installation with pip

You will need Python versions < 3.10 if you are intending to install via pip
as VTK wheels do not exist for Python 3.10.x. If you must, you will need to
use conda.

Installation should be relatively simple

```
$ pip install numpy vtk pyqt5
$ pip install mayavi
```
If for some reason pyqt5 gives you problems, you can also try the following:

```
  $ pip install pyside2
```

We also require jupyter and itkwidgets for the workshop so please also install the
following:

```
  $ pip install jupyter ipywidgets ipyevents itkwidgets
```

### Installation with conda

To install Mayavi and itkwidgets with conda try the following:

```
$ conda create -n py3dviz python=3.8
$ conda activate py3dviz  # or source activate mayavi
$ conda install -c conda-forge numpy jupyter ipywidgets ipyevents mayavi itkwidgets
```

As of June 16th, 2022, this will install python-3.8.13, Mayavi-4.7.4 and
itkwidgets-0.32.


In case we have a new release after these which may be necessary as the latest
release will incorporate better interactions between Mayavi and itkwidgets. If
the version on conda-forge is not updated in time before the tutorial, you can
do the following to obtain the latest versions. We remove the mayavi from
conda as it is an older version.

```
$ pip install -U mayavi itkwidgets
```


## Testing your installation

Try the following:

```
$ ipython

In []: %gui qt
In []: from mayavi import mlab
In []: mlab.test_plot3d()
```

This should produce a window that is interactive and usable without any
tracebacks or exceptions.
