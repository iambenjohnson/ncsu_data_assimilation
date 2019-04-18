Running DART-ROMS on RENCI. CNAPS example
============


**1) Clone the repo**

```bash
    git clone https://github.ncsu.edu/rhe/Data-Assimilation.git
```

**2) Go inside the ROMS directory**

We are currently using a ROMS version from May 2018.

.. code-block:: bash
 	cd Data-Assimilation/ROMS_May2018/

**3) Set the MY_ROOT_DIR path in build_Mao_renci.bash**

.. code-block:: bash
	vi build_Mao_renci.bash

this path

.. code-block:: bash
export     MY_ROOT_DIR=/scratch/rhe/cnaps/Data-Assimilation/ROMS_May2018

**4) Load necessary libraries**

.. code-block:: bash
	source /home/rhe/loadall.csh

**5) Build ROMS for EAKF**

The EAKF configuration is set in the ``useast.h`` file

.. code-block:: bash
	./build_Mao_renci.bash
