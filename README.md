# YAMCHA: Yet Another Model for Chemistry Happening in the Air
### **A Python-Based Chemical Box Model**

YAMCHA is a python-based box model loosely based on an old one written in a commerical software, Igor. More details about the old one (iChamber), as well as a tutorial can be found here:
https://sites.google.com/view/wangsiyuan/models

This box model solves the initial value problem defined by a (complex) chemical system, using an ordinary differential solver (ODE), with a major focus on chemistry in the atmosphere. Chemistry in the atmosphere involves tens thousands of chemical reactions across multiple phases (e.g. gases, aerosols, droplets), therefore is often extremely still mathematically.

### **YAMCHA has several features:**
- Built-in support for KPP (Kinetic PreProcessor) format from the Master Chemical Mechanism (MCM, https://mcm.york.ac.uk/MCM/). MCM is a near-explicit chemical mechansim that is widely considered as a benchmark mechanism.
- Flexible mechanism parser: users can manually type in all the chemical reactions if they wish. The parser can recognize complex chemical reactions (e.g. with non-1 stoichiometric yields) and generic rate expressions.
- Derivatives that are needed for ODE solvers are automatically generated. This is key because it's unrealistic for humans to write the derivatives which is often very complex.
- Jacobian matrix is also automatically generated, which makes the model as fast as a (conventional) ODE can do. This is also important since the Jacobian matrix is even more complicated.
- A detailed tutorial is provided, covering several key concepts in atmospheric chemistry as well.

### **A few notes:**
- The ODE solver in SciPy is used here, which is a general purpose ODE solver package that has the Backward Diffentiation Formula (BDF) option that is suitable for still problems. This is certainly not as faster as some modern solvers out there. I have also experimented several other options. numba/numbaLSODA showed some promising potentials but not quite there yet.
- KPP has several *flavors*, e.g., the KPP files used in GEOS-Chem or WRF-Chem may look somewhat different from the KPP files generated from MCM. Currently other KPP *flavors* are not fully supported but I will expand the parser to cover more KPP types in the future, especially the KPP format in GEOS-Chem and the mechanism file in CESM/CAM-Chem.
