# preCICE adapter for MBDyn #

## Installation ##
No installation configured, instead include folder in PYTHONPATH
```
export PYTHONPATH=$PYTHONPATH:<path-to-adapter>
```

Dependencies:
*    MBDyn with Python interface, develop branch for python 3 support
*    preCICE and preCICE/python-bindings, version 2 or higher
*    OpenFOAM-adapter for preCICE

## MBDyn installation ##
```
git clone https://public.gitlab.polimi.it/DAER/mbdyn.git
cd mbdyn
git checkout develop
CPPFLAGS=-I/usr/include/suitesparse PYTHON_VERSION=3 ./configure --enable-python=yes
make
sudo make install
```

Dependencies:
*    UMFPACK (Part of libsuitesparse-dev in Ubuntu repository.)

## How to use it

Add mbdyn executable path to $PATH
```
export PATH=$PATH:/usr/local/mbdyn/bin
```

Add the Python interface path to $PYTHONPATH
```
export PYTHONPATH=$PYTHONPATH:/usr/local/mbdyn/libexec/mbpy
```

Requires, see example folder:
*   pyhton script for calling adapter
*   config file and mesh file currently only support gmsh-files version 2 with ascii format

Note: Meshes with large number of nodes can lead to desync of socket stream and mbdyn api failing. Workaround implemented by setting sleep timer before reading in mbdyn script, set in [input.py  `__force_coupling_str`](https://github.com/Hag3nL/mbdyn-adapter/blob/master/mbdynAdapter/input.py#L290).

## Acknowledgements
This project has received funding from the European Union’s Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement No 642682 (AWESCO).
