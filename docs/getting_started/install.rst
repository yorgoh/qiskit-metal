Installing Qiskit Metal
=======================

Requirements
------------

Qiskit supports Python 3.6 or later. However, both Python and Qiskit are
evolving ecosystems, and sometimes when new releases occur in one or the other,
there can be problems with compatibility.

If you're having trouble installing or using Qiskit after updating Python, check
the `Qiskit Package metadata <https://pypi.org/project/qiskit/>`__ for
**Programming Language** to see which specific versions of Python are supported.

We recommend installing `Anaconda <https://www.anaconda.com/download/>`__, a
cross-platform Python distribution for scientific computing. Jupyter,
included in Anaconda, is recommended for interacting with Qiskit.

Qiskit is tested and supported on the following 64-bit systems:

*	Ubuntu 16.04 or later
*	macOS 10.12.6 or later
*	Windows 7 or later



Install Qiskit Metal from Source
--------------------------------

We recommend using Python virtual environments to cleanly separate Qiskit from
other applications and improve your experience.

Metal can either be installed using a [conda environment](https://docs.conda.io/en/latest/miniconda.html) 
or a Python virtual environment, as described below.

1. Clone the Qiskit Metal repository.

.. code:: sh

   git clone https://github.com/Qiskit/qiskit-metal.git

2. Cloning the repository creates a local folder called ``qiskit-metal``.

.. code:: sh

   cd qiskit-metal

3. Set up your local environment and instal.

The most reliable way to set up a qiskit_metal environment is to build one from scratch using the provided conda environment specification file `environment.yml`.
To do so, execute these commands in the top-level of the repository:

.. code:: sh

   conda env create -n <env_name> environment.yml
   conda activate <env_name>
   python -m pip install -ve .

For convenience, you can also try to install directly in an existing environment such as the `base` environment, if it is relatively up to date.
To install `qiskit_metal` and its depenencies into an existing environment named `<env_name>`, execute these commands in the top-level of the repository:

.. code:: sh

   conda env update -n <env_name> environment.yml
   conda activate <env_name>
   python -m pip install -ve .

*Notes on using conda*

It is possible that you may run into version issues in the above if previously installed packages conflict with the requirements of qiskit_metal.

.. note::

    Every time you intend to develop code using this environment, you MUST first run the command: `conda activate <env_name>`.  See what a [conda environment is](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

To use the new environment inside jupyter lab you will need to follow these additional steps right after the above:

.. code:: sh

   conda install ipykernel
   ipython kernel install --user --name=<any_name_for_kernel>

To use a Python virtual environment instead, execute these commands in the top-level of the repository:

.. code-block:: sh

   python -m venv <virtual_env_path>
   source <virtual_env_path>/bin/activate
   python -m pip install -U pip
   python -m pip install -r requirements.txt -r requirements-dev.txt -e .

