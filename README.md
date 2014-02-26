# zeroSR1 toolbox

The zeroSR1 toolbox implements the algorithm from 'A quasi-Newton proximal splitting method' by 
Stephen Becker and Jalal Fadili, which appeared in [NIPS 2012](http://nips.cc/). The paper is available at [arXiv 1206.1156](http://arxiv.org/abs/1206.1156).

Briefly, the algorithm follows the standard proximal-gradient method, but allows a scaled prox. This enables us to use a limited-memory SR1 method (similar to L-BFGS).

The algorithm solves problems of the form min\_x f(x) + g(x) where f is differentiable (more precisely, with a Lipschitz gradient) and g is one of the following (see the paper):

Available "g" | Cost for input of size "n"
------------- | -------------
l1 norm | O( n log n)
non-negativity constraints | O( n log n)
box constraitns | O( n log n )

The algorithm compares favorably with other methods, including [L-BFGS-B](http://www.mathworks.com/matlabcentral/fileexchange/35104-lbfgsb-l-bfgs-b-mex-wrapper).

This toolbox currently implements in the following languages

* Matlab

We also strive to make it compatible with Octave. Further releases may target these languages:

* Python
* R
* C++

# Installation
For Matlab, there is no installation necessary. Every time you run a new Matlab session, run the `setup_zeroSR1.m` file and it will add the correct paths.

# Structure
In each folder, see they `Contents.m` file for more information
## Algorithms
This includes the zeroSR1 algorithm as well as implemenations of FISTA and other proximal-gradient methods

## Proxes
The scaled diagonal+ rank1 prox operators for various "g" functions

## SmoothFunctions
These are pre-made wrappers for the various smooth "f" functions. The files here with the `_splitting` suffix are intended for use with any method that requires forming the augmented variable "x\_aug = (x\_pos, x\_neg)". For example, this approach is used when using L-BFGS-B (which only allows box constraints, such as x\_pos >= 0,  x\_neg <= 0) to solve the LASSO problem.

## Utilities
Helper files

## Tests
Verify the algorithm and proxes are working correctly. This uses [CVX](http://cvxr.com/cvx) to verify; if this is not installed on your system, then it relies on precomputed solutions stored in a subdirectory.

## Experiments
Recreate tests of several algorithms, or do something more interesting than the scripts in `tests`

## Authors
The original authors are Stephen Becker and Jalal Fadili. Further contributions are welcome.
