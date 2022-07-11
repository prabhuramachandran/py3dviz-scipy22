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
## Pythonic 3D visualization: Introduction

**Prabhu Ramachandran and Matt McCormick**

**SciPy 2022**

<!-- #endregion -->


<!-- #region slideshow={"slide_type": "slide"} -->
## 3D visualization in Python

- Visualization vs. Rendering
- Visualization is more
- Not as straightforward as 2D visualization

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## The various options

- Python library or standalone application
- VTK based, lower-level OpenGL/WebGL based
- Desktop-based or Web-based
- Client-side or server-side rendering
- Mature or experimental
- Optimal use of hardware acceleration etc.
- Advanced features: large data, parallel rendering, ...

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Our focus

- VTK based tools: Mayavi and itkwidgets

- Fully open source: BSD license, Apache 2.0 license

- Mayavi
   - Mature (first in 2001, rewritten in 2006)
   - Fully scriptable
   - Full-fledged UI
   - Easy to build UIs
   - Basic jupyter notebook support
   - Problem: busy (lazy?) lead developer

- itkwidgets
   - First release 2018, rewrite pre-releases currently available
   - Excellent client-side support
   - Current: Jupyter, ipywidgets
   - Problem: interactive 3D data exploration
   - Future: Generic web platform support, flexible rendering, customizable UI
   - Accessible, flexible, sustainable
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## Mayavi features

- Visualization of scalar, vector, tensor data
- Basic volume rendering
- Pythonic API
- Supports variety of datasets: structured and unstructured
- Full UI with automatic script recording

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
## itkwidgets features

- Visualize 2D and 3D images, point sets, and geometry, e.g. meshes, in Jupyter
- Integrates with other Python packages, e.g. NumPy, Dask, vtk-based
- Exquisite volume rendering
- Label image segmentation 2D and 3D rendering
- Innovative, powerful opacity transfer function / window / level widget
<!-- #endregion -->


<!-- #region slideshow={"slide_type": "slide"} -->
## When to use what?

- Mayavi
  - Exploration locally
  - Powerful UI useful for exploration
  - Desktop UIs/dialogs
  - Supports itkwidgets for remote viz.

- itkwidgets:
  - Excellent for client side
  - Powerful widget support
  - Plays well with everyone
  - Imaging focus
<!-- #endregion -->
