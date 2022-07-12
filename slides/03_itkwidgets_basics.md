---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.14.0
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

<!-- #region slideshow={"slide_type": "slide"} -->
# itkwidgets basics

**Prabhu Ramachandran and Matt McCormick**

**SciPy 2022**

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Outline

- **Using itkwidgets's `view`** $\Longleftarrow$
- SciPy **integrations**
- Visualization **parameters**

<!-- #endregion -->


<!-- #region slideshow={"slide_type": "slide"} -->
## Getting started with `view`

<!-- #endregion -->

```python
from itkwidgets import view
```

<!-- #region slideshow={"slide_type": "slide"} -->
### Caveats


* itkwidgets *0.X* works in the Jupyter Notebook, but not JupyterLab
* itkwidgets *1.X* works in JupyterLab, but not all the functionality of 0.X is available at this time
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
### 2D Images
<!-- #endregion -->

```python slideshow={"slide_type": "-"}
from PIL import Image
import numpy as np

image = np.asarray(Image.open('./data/cthead1.png'))
    
view(image)
```

<!-- #region slideshow={"slide_type": "-"} -->
### Exercise

Explore UI for:

- `vmin`, `vmax`
- `cmap`
- Region of interest
- Screenshot
- Fullscreen

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
### 3D Images
<!-- #endregion -->

```python
x, y, z = np.mgrid[-5:5:64j, -5:5:64j, -5:5:64j]
vol = x*x*0.5 + y*y + z*z*2
view(vol)
```

<!-- #region slideshow={"slide_type": "-"} -->
### Exercise

Explore UI for:

- Slicing planes
- Slice views

<!-- #endregion -->

```python slideshow={"slide_type": "slide"}
x, y, z = np.mgrid[-8:8:30j, -8:8:30j, -8:8:30j]
vol = np.sin(x*y*z) / (x*y*z)
view(vol)
```

<!-- #region slideshow={"slide_type": "-"} -->

### Exercise

Explore volume rendering UI for:

- Shadow
- Sample spacing
- Blend mode

<!-- #endregion -->


```python
with open('./data/humeral_distal_epiphysis.npy', 'rb') as f:
    vol = np.load(f)
view(vol)
```

<!-- #region slideshow={"slide_type": "subslide"} -->

### Exercise

Explore volume rendering UI for:

- Gradient opacity
- Opacity transfer function
<!-- #endregion -->


<!-- #region slideshow={"slide_type": "slide"} -->
### Point sets
<!-- #endregion -->

```python
number_of_points = 3000

gaussian_1_mean = [0.0, 0.0, 0.0]
gaussian_1_cov = [[1.0, 0.0, 0.0], [0.0, 2.0, 0.0], [0.0, 0.0, 0.5]]
point_set_1 = np.random.multivariate_normal(gaussian_1_mean, gaussian_1_cov,
        number_of_points)

gaussian_2_mean = [4.0, 6.0, 7.0]
gaussian_2_cov = [[2.0, 0.0, 0.0], [0.0, 2.0, 0.0], [0.0, 0.0, 1.5]]
point_set_2 = np.random.multivariate_normal(gaussian_2_mean, gaussian_2_cov,
        number_of_points)

gaussian_3_mean = [4.0, 0.0, 7.0]
gaussian_3_cov = [[4.0, 0.0, 0.0], [0.0, 1.0, 0.0], [0.0, 0.0, 3.5]]
point_set_3 = np.random.multivariate_normal(gaussian_3_mean, gaussian_3_cov,
        number_of_points)                                          
```

```python slideshow={"slide_type": "slide"}
view(point_sets=[point_set_1, point_set_2, point_set_3])
```

<!-- #region slideshow={"slide_type": "-"} -->

### Exercise

Explore volume rendering UI for:

- Color
- Representation
- Size
<!-- #endregion -->


<!-- #region slideshow={"slide_type": "slide"} -->
### Geometry
<!-- #endregion -->

```python
from mayavi import mlab
mlab.options.offscreen = True

pi = np.pi
cos = np.cos
sin = np.sin
dphi, dtheta = pi / 250.0, pi / 250.0
[phi, theta] = np.mgrid[0:pi + dphi * 1.5:dphi,
                        0:2 * pi + dtheta * 1.5:dtheta]
m0 = 4
m1 = 3
m2 = 2
m3 = 3
m4 = 6
m5 = 2
m6 = 6
m7 = 4
r = sin(m0 * phi) ** m1 + cos(m2 * phi) ** m3 + \
    sin(m4 * theta) ** m5 + cos(m6 * theta) ** m7
x = r * sin(phi) * cos(theta)
y = r * cos(phi)
z = r * sin(phi) * sin(theta)

mesh = mlab.mesh(x, y, z)

view(actors=mesh, rotate=True, ui_collapsed=True)
```

<!-- #region slideshow={"slide_type": "-"} -->
### Exercise

Explore UI for:

- Representation
- Opacity
- Axes
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Outline

- **Using itkwidgets's `view`** 
- SciPy **integrations**  $\Longleftarrow$
- Visualization **parameters**

<!-- #endregion -->


<!-- #region slideshow={"slide_type": "slide"} -->
### Example integration: PyVista

<!-- #endregion -->

```python
import sys
!{sys.executable} -m pip install pyvista
```

```python slideshow={"slide_type": "slide"}
import pyvista as pv
from pyvista import examples

vol = examples.download_knee_full()

view(vol, geometries=vol.contour())
```

<!-- #region slideshow={"slide_type": "slide"} -->
### Available integrations

- NumPy
- mayavi
- ITK
- SimpleITK
- Dask
- VTK
- pyvista
- vido
- pyimagej
- zarr
- xarray
- pytorch
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Outline

- **Using itkwidgets's `view`**
- SciPy **integrations**
- Visualization **parameters** $\Longleftarrow$

<!-- #endregion -->


<!-- #region slideshow={"slide_type": "slide"} -->
### Pass visualization parameter on viewer instantiation

<!-- #endregion -->

```python
with open('./data/humeral_distal_epiphysis.npy', 'rb') as f:
    vol = np.load(f)
    
viewer = view(vol, gradient_opacity=0.9)
viewer
```

<!-- #region slideshow={"slide_type": "fragment"} -->
To change the colormap from the widget user interface, select the desired colormap use the dropdown above the transfer function editor.
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "fragment"} -->
We change the value of the colormap by assigning the `cmap` property to the desired *itkwidgets* colormap string identifier. This is a `list` where elements in the list are colormaps for image components / channels.
<!-- #endregion -->

```python
viewer.cmap = ['gist_earth',]
```

<!-- #region slideshow={"slide_type": "slide"} -->
Or, specify a custom colormap with an *Nx3* NumPy array.

The colormap is specified with a series of `[red, blue, green]` values ranging from 0.0 to 1.0.

For example, to manually create a grayscale colormap:
<!-- #endregion -->

```python slideshow={"slide_type": "-"}
colormap = np.array([[0.0, 0.0, 0.0],
                     [1.0, 1.0, 1.0]])
viewer = view(vol, gradient_opacity=0.9, cmap=colormap)
viewer
```

```python
viewer.cmap
```

<!-- #region slideshow={"slide_type": "slide"} -->
Or, specify a custom [`matplotlib.colors.LinearSegmentedColormap`](https://matplotlib.org/api/_as_gen/matplotlib.colors.LinearSegmentedColormap.html#matplotlib.colors.LinearSegmentedColormap) from [matplotlib](https://matplotlib.org/tutorials/colors/colormaps.html#sphx-glr-tutorials-colors-colormaps-py).
<!-- #endregion -->

```python
import matplotlib

print(type(matplotlib.cm.autumn))

view(vol, gradient_opacity=0.9, cmap=matplotlib.cm.autumn)
```

<!-- #region slideshow={"slide_type": "slide"} -->
### Exercise

Create a color map from NumPy arrays that goes from black to blue.
<!-- #endregion -->

```python
# Solution code
```

```python
# %load solutions/03_colormap.py
```
