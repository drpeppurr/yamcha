# yamcha
Yet Another Model for Chemistry Happening in the Air (YAMCHA): a Python-Based Box Model

YAMCHA is a python-based box model loosely based on an old one written in a commerical software, Igor. More details about the old version, as well as a tutorial can be found here:
https://sites.google.com/view/wangsiyuan/models

This box model solves the initial value problem defined by a (complex) chemical system, using an ordinary differential solver (ODE), with a major focus on chemistry in the atmosphere. Chemistry in the atmosphere involves tens thousands of chemical reactions across multiple phases (e.g. gases, aerosols, droplets), therefore is often extremely still mathematically.

YAMCHA has several features:
- Built-in support for KPP (Kinetic PreProcessor) format from the Master Chemical Mechanism (MCM, https://mcm.york.ac.uk/MCM/). MCM is a near-explicit chemical mechansim that is widely considered as a benchmark mechanism.
- Flexible mechanism parser: users can manually type in all the chemical reactions if they wish. The parser can recognize generic rate expressions.
- Derivatives that are needed for ODE solvers are automatically generated.
- Jacobian matrix is also automatically generated, which makes the model as fast as a (conventional) ODE can do.
- A detailed tutorial is provided, covering several key concepts in atmospheric chemistry as well.

The ODE solver in SciPy is used here, which is a general purpose ODE solver package that has the Backward Diffentiation Formula (BDF) option that is suitable for still problems. This is certainly not as faster as some modern solvers out there.

Note that the KPP format has several *flavors*, e.g., the KPP files used in GEOS-Chem or WRF-Chem may look somewhat different from the KPP files generated from MCM. Currently other KPP *flavors* are not fully supported but will expand to cover more KPP in the future, especially the KPP format in GEOS-Chem and the mechanism file in CESM/CAM-Chem.
