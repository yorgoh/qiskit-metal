# Qiskit Metal [![](https://badges.frapsoft.com/os/v1/open-source.png?v=103)](https://github.com/Qiskit/qiskit-metal) [![](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/Qiskit/qiskit-metal)
>  Quantum hardware design and analysis

![Welcome to Qiskit Metal!](docs/images/zkm_banner.png 'Welcome to Qiskit Metal')

## Early Access
https://qiskit.org/metal/

This is the unpolished, early-access quantum chip design software. We are so excited for you to join us in making Metal work for scientists and engineers around the world.

##### Get help: Slack
Use the [Slack channel (Join here!)](https://join.slack.com/share/zt-jjgzilxu-1u2FGivroQi64fHajpTWiw) to communicate with other developers and early-access participants. (Troubleshooting: If the Slack invitation has expired, request one by opening a GitHub issue.)

## Installation
#### Steps 1-3 show you how to set up on your local device. It should take ~10 minutes to set up Metal.
*For your own sanity, it is recommended to read this document in its entirety before proceeding.*

<a href="https://www.youtube.com/watch?v=sYVDtnJb-ZM&ab_channel=Qiskit">
 Click for Installation YouTube Video <br>
</a>


### 1. Download Qiskit Metal Code

To allow for each updates and contributions you will need to `git clone` this repository's main branch.

##### Option 1: Command line shell (with git already installed and configured):
``` sh
git clone https://github.com/Qiskit/qiskit-metal.git
```
##### Option 2:  GUI
Download [GitHub Desktop GUI](https://desktop.github.com/) and refer to these [notes](https://help.github.com/en/desktop/contributing-to-projects/cloning-a-repository-from-github-to-github-desktop).


### 2. Download/Install Conda
Install [Conda](https://docs.Conda.io/projects/Conda/en/latest/user-guide/install/), a python environment manager.


### 3. Setup Locally

#### 1. Open the correct folder
To create the Conda environment and install Metal, you must be in the `qiskit_metal` folder you just cloned.

For the terminal or command line, `cd` into qiskit_metal.

For Github desktop, you can open the qiskit_metal folder from the menu Repository -> Open In....



#### 2. Create Conda Environment

Run the commands below to create and activate a new environment with name `<env_name>` with all the necessary library dependencies found in `environment.yml`

```
conda env create -n <env_name> environment.yml
conda activate <env_name>
```

#### 3. Install Qiskit Metal in Conda Environment
Run the commands below to install Metal in your activated Conda environment.

```
python -m pip install -ve .
```

#### 4. Jupyter
Technically optional, but all tutorials for Metal are all written in Jupyter Notebooks and so it is highly encouraged you use Jupyter

*`Jupyter Notebooks` should already be installed for you by Conda.*

##### 1. Add Conda Environment to Jupyter
*Make sure you're still in your <env_name> activated environment*
```
conda install ipykernel
ipython kernel install --user --name=<env_name>
```
This will create a kernel from <env_name> Conda environment that you can choose to use in Jupyter Notebooks

##### 2. Launch Jupyter

```
jupyter notebook
```
This should open your browser to Jupyter

##### 3. Run Notebook
Navigate to a jupyter notebook you wish to run. For example, `qiskit_metal/TUTORIAL/1 Start Here/1.1 Flashy Quick Demo of Metal.ipynb`


Once the notebook is open, be sure to click on the `kernel` tab and `change kernel` to the <env_name> environment you already created.

Then click the `cell` tab and click `run all`

#### 5 Using Metal
Open the TUTORIAL folder in Jupyter Notebooks and start playing with Metal.

#### 5.5 Developer Setup (Optional)
If you are planning to contribute to the qiskit metal codebase, you'll want to use these instructions to [setup developer workspace](/docs/NEW_DEVELOPER_SETUP.md)


#### Notes:

* Remember the period (".") at the end of the third command.
* **Important**: Remember to `Conda activate <env_name>` if you intend to use qiskit-metal.  See what a [Conda environment is](https://docs.Conda.io/projects/Conda/en/latest/user-guide/tasks/manage-environments.html)
* Check the *Common Issues* section at the bottom of these README if you run into problems.
* Please contact us on slack if you run into issues

You can already use qiskit-metal through jupyter notebook.
However, if you prefer using jupyter lab, you will need to execute a couple of extra steps.


### Alternative Setup (no Conda) - not recommended:
*On Windows, the Conda environment is strongly recommended because Shapely is difficult to install directly via pip.*
##### Virtual environment setup

**On Windows, do this first:** It is recommended that you first install `Visual C++ 14.0`, it is required for a successful install of `gdspy`.

If you do not have `Visual C++ 14.0` installed you will be notified to install it when `gdspy` attempts to install.
You can do this by downloading and installing [C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/).
Be sure to select the latest versions of `MSVCv142 - VS 2019 C++ x64/x86 build tools` and `Windows 10 SDK` in the installer as suggested in [this wiki](https://wiki.python.org/moin/WindowsCompilers) referenced by the gdspy documentation.

To use a Python virtual environment, execute these commands in the top-level of the repository:

```
python -m venv <virtual_env_path>
source <virtual_env_path>/bin/activate
python -m pip install -U pip
python -m pip install -r requirements.txt -r requirements-dev.txt -e .
```

where `<virtual_env_path>` is where you want the Python virtual environment to be installed.
On Windows, replace `source <virtual_env_path>/bin/activate` with `.\<virtual_env_path>\Scripts\activate`.

Finally, if you are planning to develop the qiskit metal codebase, you'll want to use these instructions to [setup developer workspace](/docs/NEW_DEVELOPER_SETUP.md)





## Common Metal Issues
#### Installation hints

Here are some things to consider when setting up a development environment:

* If using a virtual environment, make sure `pip` is up to date. In initial environment testing, PySide2 is installable with only the latest version of `pip`.

* Add the path of your qiskit-metal folder to your PATH


#### pyqode/pyside
Please be aware that the environment.xml and requirements.txt each use a different `pyside` version. This is done for Windows OS users to prevent a ipython kernel crash caused by the installation of a library incompatible with `pyqode`.

For other OS users, this setup might cause `pyqode.qt` to be upgraded automatically after it is first installed. If you still observe `pyqode`-related errors, try forcing the upgrade of the pyqode.python library with `pip install pyqode.python --upgrade`.

If Windows users continue to experience GUI or other issues, try rerunning `python setup.py install` or creating a new, pristine Conda environment as per above instructions. Pay particular attention to the python version, which must remain 3.7.8 for as long as qiskit-metal utilizes pyqode.

#### Jupyter Lab
If you can not start Jupyter Lab in the new environment.

Based on: https://anaConda.org/Conda-forge/jupyterlab
Install Jupyter lab by
```
Conda install -c Conda-forge jupyterlab
```
Then change directory to top level of repository.
```
python -m pip install -e .
```

#### qutip
`qutip` may have issues finding your path if using VSCode, resulting in a `KeyError: 'physicalcpu'`. If the error occurs, please add your PATH to VSCode's settings as follows.


 ##### Windows:
 Open Windows Command Prompt and type in
 ```
 $Env:Path
 ```
Copy the resulting output. Example: `"PATH": "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"`
Then open the applicable settings.json in your VS Code. (See how to open command palette [here](https://code.visualstudio.com/docs/getstarted/tips-and-tricks). Search "settings" and click Open Workspace Settings (JSON)). Paste:
```
 "terminal.integrated.env.windows": {
        "PATH": "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
        }
```

##### MacOs:
 Open Terminal and type in
 ```
echo $PATH
 ```
Copy the resulting output. Example: `"PATH": "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"`
Then open the applicable settings.json in your VS Code. (See how to open command palette [here](https://code.visualstudio.com/docs/getstarted/tips-and-tricks). Search "settings" and click Open Workspace Settings (JSON)). Paste:
```
    "terminal.integrated.env.osx": {
        "PATH": "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
        }
```

## Docs and how to use

[Conda User Guide](https://docs.Conda.io/projects/Conda/en/latest/user-guide/tasks/manage-environments.html)

[Python Setup and Usage](https://docs.python.org/3/using/)

[Python Language Reference](https://docs.python.org/3/reference/index.html)

[Python How-To's](https://docs.python.org/3/howto/index.html)

[Python Tutorials](https://docs.python.org/3/tutorial/index.html)

[Python Style Guide](https://www.python.org/dev/peps/pep-0008/)

[Metal Docs](/docs)

[Docstring cheat sheet](/docs/docstring_cheat_sheet.md)


## Authors and Citation

Qiskit Metal is the work of [many people](https://github.com/Qiskit/qiskit-metal/pulse/monthly) who contribute to the project at different levels. Metal was conceived and developed by Zlatko Minev at IBM, then co-led with Thomas McConkey. If you use Qiskit, please cite as per the included [BibTeX file](https://github.com/Qiskit/qiskit/blob/master/Qiskit.bib).For icon attributions, see [here](/qiskit_metal/_gui/_imgs/icon_attributions.txt).


## License

[Apache License 2.0](LICENSE.txt)
