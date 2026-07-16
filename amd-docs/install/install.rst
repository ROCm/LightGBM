.. meta::
   :description: Install LightGBM with ROCm support for AMD GPUs
   :keywords: amd, rocm, finance, financial, fintech, algorithm, gpu, install, setup, env, docker, pip, package, quick, start, lib

*************************
Install LightGBM with pip
*************************

.. _lightgbm-install-prerequisites:

Prerequisites
=============

Before proceeding, ensure that you have installed a supported ROCm version,
operating system, and Python version that are compatible with the ROCm Finance
libraries. Verify that your system includes a supported AMD Instinct GPU. For
guidance, see `AMD Finance installation prerequisites
<https://rocm.docs.amd.com/projects/rocm-finance/en/latest/install/prerequisites.html>`__.

For a consistent and streamlined setup experience, it's recommended to use
a ROCm development environment Docker container. See `Install ROCm Finance
<https://rocm.docs.amd.com/projects/rocm-finance/en/latest/install/install.html>`__
for instructions.

Install using pip
=================

Install the ROCm-enabled LightGBM library from the AMD-hosted PyPI repository.

.. tab-set::

   .. tab-item:: ROCm 7.0.2
      :sync: rocm7

      .. code-block:: shell

         pip install amd_lightgbm --extra-index-url=https://pypi.amd.com/rocm-7.0.2/simple

   .. tab-item:: ROCm 6.4.4
      :sync: rocm6

      .. code-block:: shell

         pip install amd_lightgbm --extra-index-url=https://pypi.amd.com/rocm-6.4.4/simple

Verify your installation
------------------------

Use ``pip show`` to verify your installation:

.. code-block:: shell

   pip show -v amd_lightgbm

.. dropdown:: Example output

   .. code-block:: shell-session

      Name: amd_lightgbm
      Version: 4.6.0.99
      Summary: ROCm Port of LightGBM Python-package
      ... [output truncated]

After installing LightGBM, import and use the library. For example:

.. code-block:: python

   import lightgbm as lgb
   import numpy as np
   rng = np.random.default_rng()
   data = rng.uniform(size=(500, 10))  # 500 entities, each contains 10 features
   label = rng.integers(low=0, high=2, size=(500, ))  # binary target
   train_data = lgb.Dataset(data, label=label)
