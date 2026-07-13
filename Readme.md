# NumPy Mastery

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.26%2B-013243?logo=numpy&logoColor=white)
![Notebooks](https://img.shields.io/badge/Notebooks-6-orange?logo=jupyter)
![Tests](https://img.shields.io/badge/Tests-pytest-green?logo=pytest)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

A structured, hands-on repository documenting my path to NumPy proficiency, from first principles to a production-style image processing pipeline built with **zero external math libraries**.

---

## What's in here
 
```
numpy-mastery/
├── notebooks/                        # 6 annotated learning notebooks
│   ├── 01_array_creation.ipynb
│   ├── 02_indexing_slicing.ipynb
│   ├── 03_operations_broadcasting.ipynb
│   ├── 04_linear_algebra.ipynb
│   ├── 05_statistics_random.ipynb
│   └── 06_performance_tricks.ipynb   # coming soon
│
├── exercises/                        # 50+ graded problems (Easy → Hard)
│   ├── ex01_creation.ipynb
│   ├── ex02_indexing.ipynb
│   ├── ex03_operations.ipynb
│   ├── ex04_linear_algebra.ipynb
│   ├── ex05_statistics.ipynb
│   └── solutions/                    # Full worked solutions for each module
│       ├── sol01_creation.ipynb
│       ├── sol02_indexing.ipynb
│       ├── sol03_operations.ipynb
│       ├── sol04_linear_algebra.ipynb
│       └── sol05_statistics.ipynb
│
└── project/                          # Capstone: image processing pipeline
    ├── filters.py                    # Convolution: Sobel, Gaussian, Laplacian
    ├── transforms.py                 # Rotate, resize, flip, crop
    ├── pipeline.py                   # Composable | operator chain
    ├── demo.ipynb                    # Visual before/after walkthrough
    ├── benchmarks.ipynb              # NumPy vs naive Python speed tests
    └── tests/                        # pytest suite (35 tests)
```
 
---

---

## Notebooks overview

| # | Notebook | Key concepts |
|---|----------|-------------|
| 01 | Array Creation | `arange`, `linspace`, `zeros/ones/full`, dtypes, memory layout |
| 02 | Indexing & Slicing | Basic, 2-D, fancy indexing, boolean masking, `np.where` |
| 03 | Operations & Broadcasting | Arithmetic, aggregation with `axis`, all 3 broadcasting rules |
| 04 | Linear Algebra | `@` operator, `linalg.solve`, SVD, eigendecomposition |
| 05 | Statistics & Random | Descriptive stats, the modern `default_rng` API, Monte Carlo |
| 06 | Performance | Strides, views vs copies, vectorisation patterns, `np.save` |

---

## Capstone project — Image Processing Pipeline

An image processing library written in **pure NumPy** — no OpenCV, no PIL, no scipy.

### Features implemented

- **Filters**: Gaussian blur, Sobel edge detection (x/y/magnitude), Laplacian, sharpen, emboss
- **Transforms**: bilinear resize, arbitrary rotation, horizontal/vertical flip, centre crop
- **Pipeline**: composable `|` operator to chain operations, optional timing
- **Benchmarks**: head-to-head timing vs plain Python loops on the same operations

```python
from project.pipeline import Pipeline
from project.filters import gaussian_blur, sobel_magnitude
from project.transforms import rotate, resize

result = (
    Pipeline(image)
    | gaussian_blur(sigma=1.5)
    | rotate(angle=15)
    | sobel_magnitude()
    | resize(target=(256, 256))
).run()
```

### Sample outputs

| Original | Gaussian blur | Sobel edges | Rotated |
|----------|--------------|-------------|---------|
| *(see demo.ipynb)* | | | |

---

## Quick start

```bash
git clone https://github.com/<your-username>/numpy-mastery
cd numpy-mastery
pip install -r requirements.txt
jupyter notebook notebooks/01_array_creation.ipynb
```

**Requirements**: `numpy`, `matplotlib`, `pytest`, `jupyter`

---

## Skills demonstrated

- Vectorised computation, no Python loops where NumPy can do the job
- Broadcasting across N-dimensional arrays
- Memory-efficient operations via views and stride tricks
- Linear algebra from first principles (regression, SVD, eigenvalues)
- Statistically correct random number generation with the modern Generator API
- Clean, tested, documented Python code

---

## Running the tests

```bash
cd project
pytest tests/ -v
```

---

*Built as part of a structured AI/ML engineering curriculum.*
