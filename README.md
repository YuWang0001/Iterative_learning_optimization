# Iterative-learning-robust-optimization

## Repository content

The repository contains the Matlab code that allows to generate the examples' results, for the paper "*Iterative learning robust optimization - with application to medium optimization of CHO cell cultivation in continuous monoclonal antibody production*" by Yu Wang, Mirko Pasquini, Véronique Chotteau, Håkan Hjalmarsson and Elling W. Jacobsen.

In particular the repo has two folders:
1. **motivating_example_code** : code to generate the numerical results for the motivating example (Sections 2, 5.1 and 6.2)
2. **bio_example_code** : code to generate the numerical results for the large scale example on robust medium optimization of CHO cell cultivation in continuous monoclonal antibody (mAb) production (Section 5.2)

### motivating_example_code
The folder contains two scripts that can be executed "stand-alone" without any other dependencies:
* **motivating_example_script_parametric_uncertainties.m** : generate numerical results of Sections 2 and 5.1;
* **motivating_example_script_all_uncertainties.m** : generate numerical results of Section 6.2.

### bio_example_code

The folder contains all the code necessary to generate the results of the medium optimization example of Section 5.2. Please add the entire folder with its subfolder to the Matlab environment for a correct execution. 

#### Execution quick instructions
The user has two choices:
1. Run the file **main.m** : This will execute the entire simulation from loading the model data, up to the two batches of experiment.
*(Note: takes around 10 hours on Intel(R) Core(TM) i7-8650U CPU @ 1.90GHz 2.11 GHz, with 16gb installed ram and Matlab version R2018a)*;
2. Run the file **plot_results.m** : This will load the results of the simulations stored in the file **result.mat** and generate all the plots.

#### Model description data
There are 3 Excel files in the folder, which contains the description of the large scale model:
* **LargeM_d vs RedM_final.xlsx** : contains the maximal rates, kinetic order and reaction code, for all the macroreactions (as described in [1]);
* **activation_inhibition_coefficients_mod.xlsx** : contains the matrix of activation and inhibition parameters, as well as the maximal rates, for all the macroreactions in an easier format for the subsequent functions;
* **Amac_matrix_corrected.xlsx** : contains the macroreaction stoichiometric matrix.

## General dependencies
The code has some dependencies that should be resolved in order for it to be executed:
* **YALMIP**  : the SOCP problem (15) in the paper is formulated and solved using YALMIP [2], which should be installed to execute the code;
* **Solvers** : the SOCP corrently uses Gurobi [3] as a solver, which should therefore be installed to execute the code. An alternative would be to use Mosek [4], but this requires changing the YALMIP option accordingly, i.e. from ` options = sdpsettings('solver','gurobi')`
to ` options = sdpsettings('solver','mosek')` in the function `ConstraintsViolationAvoidanceStep` in the file **RobustOptimizationSingleStep.m**.

## References

[1] Hagrot, Erika, et al. "*Novel column generation-based optimization approach for poly-pathway kinetic model applied to CHO cell culture.*" Metabolic engineering communications 8 (2019): e00083.

[2] Löfberg, Johan. "*YALMIP: A toolbox for modeling and optimization in MATLAB.*" 2004 IEEE international conference on robotics and automation (IEEE Cat. No. 04CH37508). IEEE, 2004.

[3] Gurobi Optimization, L.. (2023). *Gurobi Optimizer Reference Manual.*

[4] MOSEK ApS (2019). *The MOSEK optimization toolbox for MATLAB manual.* Version 9.0.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
