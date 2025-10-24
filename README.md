# IITCHS Base

[![IITCHS stable documentation](https://img.shields.io/badge/docs-stable-blue)](https://mit-ll-trusted-autonomy.github.io/iitchs/)

A high-level planner for coordinating large, heterogeneous teams of autonomous agents.

## Overview

Inter- and Intra- Team Coordination From High Level Specifications (IITCHS) Code Base is a software package that allows a single human operator to deploy teams of self-coordinating, heterogeneous, autonomous robotic platforms using high-level specifications.
There is an increasing focus on developing autonomous teams of agents that can cooperate together. This work can roughly be divided into two paradigms: Swarms and Teams. Swarms typically involve large numbers of agents performing behaviors. The swarm as a whole tends to be robust to agent attrition, however swarms typically only contain homogeneous agents and perform relatively simple behaviors or tasks. Teams on the other hand are often composed of fewer heterogeneous agents. Teams typically carry out more complex behavior, but tend to not be robust to agent failure. 

IITCHS Code Base combines the best attributes of both Swarms and Teams. It enables one human operator to supervise and control large heterogeneous teams performing complex behaviors and dynamic tasks, while still being robust and resilient to agent failures and attrition. IITCHS Code Base takes in high-level objectives from a human operator and then automatically decomposes these objectives into precise, low-level plans to be executed by the autonomous robots on the heterogeneous team. In making these plans it takes into account the environment the agents are working in and the differing capabilities of individual team members. The human supervisor only needs to worry about the high-level objectives of the problem at hand without needing to figure out all details of the solution. 

IITCHS is designed to perform well on problems that

* Involve agents with differing sensors or capabilities
* Have complex time and location constraints
* Require plans that will be executed on the order of hours to days


IITCHS may not be the best match for problems that

* Require rapidly changing plans in highly uncertain environments
* Require solutions on the order of subseconds to seconds

# Install
```bash
git clone --recursive git@github.com:wpi-automata/iitchs.git
conda env create -f environment.yml
conda activate iitchs_base
./setup_conda_env_vars.sh
conda deactivate
conda activate iitchs_base
```

# Install catl
(partial instructions from https://github.com/wasserfeder/catl)
```bash
mkdir -p src/catl/lib
cd src/catl/lib
wget 'https://www.antlr.org/download/antlr-4.13.0-complete.jar'
pip install antlr4-python3-runtime==4.13.0
```

*ignore the next classpath instructions, already handeled in script setup_cona_env_vars.sh*

if not already installed, install Java. openjdk 11 old but tested.
```bash
sudo apt install openjdk-11-jdk
```

```bash
cd src/catl/catl
antlr4 -Dlanguage=Python2 catl.g4
```

# Install PyTeLo
(partial instructions from https://github.com/wpi-automata/PyTeLo_SMT)
```bash
mkdir -p src/pytelo/lib
cd src/pytelo/lib
wget 'https://www.antlr.org/download/antlr-4.13.0-complete.jar'
pip install scipy
pip install gurobipy
```

*ignore the next classpath instructions, already handeled in script setup_cona_env_vars.sh*

```bash
cd src/pytelo/stl
antlr4 -Dlanguage=Python3 stl.g4
cd src/pytelo/mtl
antlr4 -Dlanguage=Python3 mtl.g4
cd src/pytelo/wmtl
antlr4 -Dlanguage=Python3 wmtl.g4
cd src/pytelo/wstl
antlr4 -Dlanguage=Python3 wstl.g4
```

# Install Gurobi

The actual install was handled in the environment.yml, but you need to set up your license file to handle large models

* make an academic account: https://www.gurobi.com/features/academic-named-user-license/
* once you get an account and choose a license type, a window will pop up showing: "grbgetkey \<license key\>"
* in your activated conda env, run that copied command `grbgetkey <license key>`
* save the license, gurobi.lic, is in your /home/\<user\> folder

# Test Install

**Run Benchmarks**
```bash
python benchmarks/benchmark_scripts/run_benchmarks.py
```
**Visualize Results**
```bash
python benchmarks/plotting_scripts/correlation_plots.py -p=output/last_run/
```
# Update Git submodules
To pull in the most recent code from the branches defined in .gitmodules, run `git submodule update --remote`

# Debug Tips
* Model too large for size-limited license: https://support.gurobi.com/hc/en-us/articles/360051597492-How-do-I-resolve-a-Model-too-large-for-size-limited-Gurobi-license-error

# Citation Information

<!--Please use the following DOI reference number, published on Zenodo, when citing this software:-->

<!--\[INSERT HERE WHEN WE HAVE PUBLIC GITHUB REPO URL\]-->

If you use this code in your work, please consider citing the following papers:

[Scalable and Robust Algorithms for Task-Based Coordination From High-Level Specifications (ScRATCHeS)](https://ieeexplore.ieee.org/document/9663414)

[![Scalable and Robust Algorithms for Task-Based Coordination From High-Level Specifications (ScRATCHeS)](https://img.shields.io/badge/DOI-10.1109%2FTRO.2021.3130794-blue)](https://doi.org/10.1109/TRO.2021.3130794)

```
@article{Leahy2021ScalableAR,
  title={Scalable and Robust Algorithms for Task-Based Coordination From High-Level Specifications (ScRATCHeS)},
  author={Kevin J. Leahy and Zachary T. Serlin and Cristian Ioan Vasile and Andrew Schoer and Austin Jones and Roberto Tron and Calin A. Belta},
  journal={IEEE Transactions on Robotics},
  year={2021}
}
```

# Distribution and Disclaimer Statements

DISTRIBUTION STATEMENT A. Approved for public release. Distribution is unlimited.

© 2021 MASSACHUSETTS INSTITUTE OF TECHNOLOGY

    Subject to FAR 52.227-11 – Patent Rights – Ownership by the Contractor (May 2014)
    SPDX-License-Identifier: BSD-3-Clause

This material is based upon work supported by the Under Secretary of Defense for 
Research and Engineering under Air Force Contract No. FA8702-15-D-0001. Any 
opinions, findings, conclusions or recommendations expressed in this material 
are those of the author(s) and do not necessarily reflect the views of the Under 
Secretary of Defense for Research and Engineering.

The software/firmware is provided to you on an As-Is basis
