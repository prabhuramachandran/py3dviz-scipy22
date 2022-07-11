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
## Pythonic 3D visualization: Some useful features

### Part 2

**Prabhu Ramachandran and Matt McCormick**

**SciPy 2022**

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Outline

- **`itkwidgets` noteboook backend for `mayavi`** $\Longleftarrow$

- `itkwidgets` on *JupyterLite*

- *TensorBoard* and deep learning

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
### Mayavi on Jupyter

Use either the `'ipy'` or `'itk'` backends.  The `'ipy'` mode also relies on off-screen support but is the default and most powerful of the options.  It also does not require WebGL support in your browser.

For the default `'ipy'` backend, one also requires to have `ipywidgets` and `ipyevents` installed.

The `'itk'` backend is entirely client-side, and requires that you have `'itkwidgets'` installed.
<!-- #endregion -->

```python slideshow={"slide_type": "slide"}
# Always start with this.
from mayavi import mlab
mlab.init_notebook()
```

```python slideshow={"slide_type": "slide"}
s = mlab.test_contour3d()
scp = mlab.pipeline.scalar_cut_plane(s)
s.module_manager.scalar_lut_manager.show_scalar_bar = True
s
```

<!-- #region slideshow={"slide_type": "fragment"} -->
Note that if all goes well, you should be able to interact with the above just as you would with a typical Mayavi UI widget.  You should be able to interact with the camera, with the cut plane widget and with the scalar bar.|
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
Note that you will need to create a new figure if you want a different visualization.  In the following we show the same figure as above, note that interacting with one will automatically update the other as they are the same figure.
<!-- #endregion -->

```python slideshow={"slide_type": "fragment"}
mlab.gcf()
```

<!-- #region slideshow={"slide_type": "fragment"} -->
Note that unlike the other backends, if you call `mlab.clf()`, it will clear all the widgets for that particular figure -- since they are all the same.
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
### itk backend

When initializing the notebook, use the itk backend.
<!-- #endregion -->

```python slideshow={"slide_type": "fragment"}
mlab.init_notebook('itk')
```

```python slideshow={"slide_type": "slide"}
mlab.figure()
# Note the use of the figure here to create a new visualization.
s = mlab.test_points3d()
s
```

```python slideshow={"slide_type": "slide"}
mlab.clf()
mlab.test_contour_surf()
```

```python slideshow={"slide_type": "slide"}
mlab.clf()
s = mlab.test_mesh_sphere()
s
```

```python slideshow={"slide_type": "slide"}
mlab.clf()
mlab.test_contour3d()
```

<!-- #region slideshow={"slide_type": "slide"} -->
## Outline

- `itkwidgets` noteboook backend for `mayavi`

- **`itkwidgets` on *JupyterLite*** $\Longleftarrow$

- *TensorBoard* and deep learning

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Outline

- `itkwidgets` noteboook backend for `mayavi`

- `itkwidgets` on *JupyterLite*

- ***TensorBoard* and deep learning** $\Longleftarrow$

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Demo of script recording



<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Custom UIs

<center>
<img width="90%" src="MEDIA/m2/lorenz_ui1.png"/>
</center>

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Custom UIs

- 130 loc for the UI
- Uses traits/traitsui
- Declarative UI
- See ETS tutorial this afternoon

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Notebook support

- Both server-side and client side possible
- Use `mlab.init_notebook`
- Different backends: `'ipy'` or `'itk'`

<!-- #endregion -->
