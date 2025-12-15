.. meta::
   :description: Use LightGBM with ROCm support on AMD GPUs
   :keywords: amd, rocm, finance, financial, fintech, algorithm, gpu

**********************
LightGBM documentation
**********************

Use LightGBM on ROCm for GPU-accelerated gradient boosting on AMD Instinct
GPUs, enabling scalable performance for financial modeling tasks with large,
imbalanced, and categorical datasets.

LightGBM uses histogram‑based splitting and leaf‑wise tree growth to achieve
rapid convergence on datasets with many categorical features (such as
employment type or verification status) without requiring one‑hot encoding. It
maintains a low memory footprint and handles sparsity effectively, making it
well‑suited to credit risk and scoring workloads. GPU acceleration can provide
2x to 5x performance gains through optimized histogram computation; however, care is
needed to avoid overfitting without parameters such as ``min_data_in_leaf``.

ROCm enablement accelerates LightGBM on AMD Instinct GPUs with optimized
kernels and efficient memory handling, delivering meaningful performance gains
over CPU‑only baselines, especially for finance pipelines rich in categorical
data.

LightGBM is part of the `AMD ROCm Finance toolkit
<https://rocm.docs.amd.com/projects/rocm-finance/en/latest/>`__.

The ROCm-Finance LightGBM source code is hosted on GitHub at
`<https://github.com/ROCm/LightGBM/>`__.

ROCm-Finance LightGBM documentation is organized into the following categories:

.. grid:: 2
   :gutter: 3

   .. grid-item-card:: Install

      * :doc:`/install/install`
      * :doc:`/install/build-from-source`

   .. grid-item-card:: Reference

      * `Python quick start (upstream) <https://lightgbm.readthedocs.io/en/v4.6.0/Python-Intro.html>`__
      * `Python API (upstream) <https://lightgbm.readthedocs.io/en/v4.6.0/Python-API.html>`__

   .. grid-item-card:: Tutorial

      * `Examples (GitHub) <https://github.com/ROCm/rocm-finance/tree/main/examples/lightgbm>`__
