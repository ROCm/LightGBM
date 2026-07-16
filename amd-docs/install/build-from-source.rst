.. meta::
   :description: Build LightGBM with ROCm support from source for AMD GPUs
   :keywords: amd, rocm, finance, financial, fintech, algorithm, gpu, install, setup, env, docker, package, contribute, develop, build, pip, make

************************************
Build LightGBM on ROCm from source
************************************

Prerequisites
=============

Before proceeding, ensure that you have installed a supported ROCm version,
operating system, and Python environment that are compatible with the ROCm
Finance libraries. Verify that your system includes a supported AMD Instinct
GPU. For guidance, see `ROCm finance installation prerequisites
<https://rocm.docs.amd.com/projects/rocm-finance/en/latest/install/prerequisites.html>`__.

For a consistent and streamlined setup experience, it's recommended to use
a ROCm development environment Docker container. See `Install ROCm Finance
<https://rocm.docs.amd.com/projects/rocm-finance/en/latest/install/install.html>`__
for instructions.

Build from source
=================

1. Clone the `<https://github.com/AMD-Ecosystem/LightGBM>`__ source code from GitHub.

   .. code-block:: shell

      git clone --recurse-submodules https://github.com/AMD-Ecosystem/LightGBM/

2. Create and activate a Python virtual environment.

   .. code-block:: shell

      python -m venv lightgbm_build
      source lightgbm_build/bin/activate

3. Configure the ``build`` directory and CMake -- make sure you're using CMake version
   3.8 or greater.

   .. code-block:: shell

      export CMAKE_PREFIX_PATH=/opt/rocm
      export CMAKE_CXX_COMPILER=hipcc
      cmake -DUSE_ROCM=1 -B build -S . -D CMAKE_PREFIX_PATH=/opt/rocm

4. Build the executable binary.

   .. code-block:: shell

      cd build
      make -j

   You should see the LightGBM executable built and placed just outside the ``build`` directory.

   .. code-block:: shell

      cd ..

5. Build the exectuable binary with unit tests.

   .. code-block:: shell

      export CMAKE_PREFIX_PATH=/opt/rocm
      export CMAKE_CXX_COMPILER=hipcc
      cmake -DUSE_ROCM=1 -DBUILD_CPP_TEST=ON -B build -S . CMAKE_PREFIX_PATH=/opt/rocm
      cd build
      cmake --target testlightgbm -j

   To run the unit tests, use:

   .. code-block:: shell

      cd ..
      ./testlightgbm

6. Build and install the Python module.

   .. code-block:: shell

      export CMAKE_PREFIX_PATH=/opt/rocm
      pip install --upgrade pip
      pip install --upgrade --force-reinstall numpy pandas scikit-learn scipy setuptools matplotlib cloudpickle pytest psutil joblib pyarrow dask cffi
      ./build-python.sh bdist_wheel --rocm
      pip install dist/amd_lightgbm*.whl

7. Verify the installation.

   .. code-block:: shell

      pip show -v amd_lightgbm

   .. dropdown:: Example output

      .. code-block:: shell-session

          Name: amd_lightgbm
          Version: 4.6.0.99
          Summary: ROCm Port of LightGBM Python-package
         ... [output truncated]
