# 📄📊 Swizz

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Docs](https://img.shields.io/badge/docs-available-blue)](https://anonymous-ml-author.github.io/swizz-anonymous/)
[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![Built for Papers](https://img.shields.io/badge/built%20for-AI%20papers-ff69b4)](https://anonymous-ml-author.github.io/swizz-anonymous/)


![Logo](https://drive.usercontent.google.com/download?id=1q5wLiKynM4l-gRIbCLi40KXRS2FJhplM)

**Swizz** is a Python library for generating **publication-ready visualizations**, **LaTeX tables**, and **subfigure layouts** with minimal code and consistent style.
[**Check out the live docs**](https://anonymous-ml-author.github.io/swizz-anonymous/) for examples and usage.

Built for AI/ML researchers, it's designed to make NeurIPS/ICLR/CVPR-style figures effortless — no more LaTeX hacks and style mismatches. Focus on your results, not your rendering.

If you use Swizz in your research, please consider citing it using:
```bibtex
@software{XXXX,
  author = {XXXX},
  license = {MIT},
  month = apr,
  title = {{Swizz: Publication-ready plots and LaTeX tables for ML papers}},
  url = {https://github.com/XXXX/swizz},
  version = {0.1.0},
  year = {2025}
}
```

---

## 🚀 Features

- 🧾 Auto-generated **LaTeX tables** from your data
- 📊 One-liner **plotting functions**
- 🧩 Easy **layout builders** for stacked, grid, and subfigure formats
- 📚 Expanding **Jupyter Book** documentation with live examples

---

## 📦 Installation

Via PyPi:
```bash
pip install swizz
```

By cloning the repository:
```bash
git clone git@github.com:XXXX/swizz.git swizz
cd swizz
pip install .
```

---

## 📁 Project Structure

| Module            | Description                                                    |
|-------------------|----------------------------------------------------------------|
| `swizz.table`  | Table generators                                               |
| `swizz.plot`   | Plotting utilities built on Seaborn & Matplotlib               |
| `swizz.layout` | Layout builders for stacked / side-by-side images              |

---

## 🧪 Examples

**Multi-level table example:**

```python
from swizz.table import table

complex_df = ...

latex_string = table(
    "grouped_multicol_latex",
    df=complex_df,
    row_index="Model",
    col_index=["Split", "Budget"],
    groupby="Task",
    value_column="score",
    highlight="min",
    stderr=True,
    caption="Combinatorial optimization results",
    label="tab:combo_results"
)
```
![Complex Table](https://drive.usercontent.google.com/download?id=1xILtGjBgZkw46XNuXH5zHntFFi5vKQaS)

**Simple bar chart example:**

```python
from matplotlib import pyplot as plt
from swizz import plot

data_dict = ...

# Style map for each metric (hatch patterns for filling)
style_map = {
    "Accuracy": '',
    "Precision": '\\',
    "Recall": 'x'  # Cross hatch pattern for Recall
}

plot("general_bar_plot", data_dict, style_map=style_map, save="bar")
plt.show()
```
![Bar Chart](https://drive.usercontent.google.com/download?id=1jaIVf8Wl2Zp7He3Dt610CvaV1FEobObL)

**Complex nested layouts:**

```python
from swizz.layouts.blocks import Row, Col, LegendBlock, Label
from swizz.layouts import render_layout
from matplotlib import pyplot as plt

plot1, plot2, plot3 = ...

nested_layout = Col([
    Row([
        LegendBlock(labels=["Accuracy", "Precision", "Recall"], ncol=3, fixed_width=0.35),
        LegendBlock(labels=["Forward KL", "Reverse KL"], ncol=2)
    ], fixed_height=0.08, spacing=0.15),
    Row([
        Col([
            plot3,
            Label("(a) Bar chart", align="center", fixed_height=0.05),
        ]),
        Col([
            plot1,
            Label("(b) Line plot 1", align="center", fixed_height=0.05),
            plot2,
            Label("(c) Line plot 2", align="center", fixed_height=0.05)
        ], spacing=0.07)
    ], spacing=0.1),
], spacing=0.02)

fig = render_layout(nested_layout, figsize=(10, 8))
plt.show()
```
![Complex Layout](https://drive.usercontent.google.com/download?id=1wyP6AQe24AGgQe216o1BifDyi_0yBHiH)

---

## 🛠️ Roadmap

- [ ] Add more plot types (confusion, UMAP, attention, histograms, etc.)
- [ ] Add Manim integrations for dynamic plot videos and function evolutions, etc.
- [ ] Add more tables
- [ ] W&B / MLflow integration

---

## 🤝 Contributing

Contributions are very welcome! See `CONTRIBUTING.md` for setup and module structure.

---
