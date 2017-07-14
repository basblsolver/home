# Motivation for the solver
While bilevel programming problem (BPP) has been studied for a long time, the few software codes that are currently available are mainly limited to special subclasses. 
 - The bilevel solver in `YALMIP` (language for advanced modeling and solution of convex and nonconvex optimization problems) [51] is restricted to convex quadratic inner problems, but convexity is not a requirement on the outer problem. 
 - Similarly, `BIPA` (BIlevel Programming with Approximation methods), a software based on a trust-region method for nonlinear bilevel programming problems, requires function to be convex in y for each fixed value of x. 
 - The `EMP` (Extended Mathematical Programming) tool in `GAMS` (General Algebraic Modeling System) automatically creates an MPEC (Mathematical Program with Equilibrium Constraints) by expressing the lower level optimization problem via its Karush-Kuhn-Tucker (KKT) optimality conditions and finds a solution of the MPEC, not of the bilevel program. If the lower level program is nonconvex, the optimal solution of a bilevel problem may not even be a stationary point of the reduced single-level optimization problem. Thus this solver is limited to bilevel problems with a convex inner problem that meets a constraint qualification.
- To handle general bilevel problems that do not adhere to the simplifying assumptions required by these deterministic solvers, two evolutionary-based algorithms, that have been implemented in `MATLAB`, are available (http://www.bilevel.org/).
To address the lack of general deterministic bilevel solvers, we introduce the first implementation of our bilevel solver capable of handling very general (BPP) problems. The solver presented here, Branch-And-Sandwich BiLevel algorithm (`BASBL`), is based on this latter work. It is implemented within the open-source `MINOTAUR` toolkit.

## Command-line interface
`BASBL` is based on command line interface and used over a terminal. The `BASBL` output below is obtained for the bilevel model [mb_1_1_05](https://github.com/basblsolver/test-problems/wiki/mb_1_1_05) using the outer tolerance 1e-3 and the inner tolerance 1e-5.

```
================================================================================
2015-12-18        Branch-And-Sandwich BiLevel solver: BASBL v0.1        00:27:35
================================================================================
mb_1_1_05: Obj. val. and solution |   No of solved subp. | No of el.|  Time(s) |
--------------------------------------------------------------------------------
Iter    Fopt    fopt  (Xopt, Yopt)   ILB IUB  LB  UB  OVF   L  Li    GAMS  BASBL
--------------------------------------------------------------------------------
   0    7.96   -0.50        (1,-1)     1   1   1   1    1   1   0    0.50   0.50
   1    7.96   -0.50        (1,-1)     3   3   3   2    3   2   0    1.15   1.18
   2    0.00    0.00         (0,0)     5   5   5   4    7   2   1    1.89   1.98
   3    0.00    0.00         (0,0)     7   7   7   5    9   2   0    2.46   2.63
   4    0.00    0.00         (0,0)     9   9   9   5    9   1   2    2.92   3.18
   5    0.00    0.00         (0,0)    11  11  11   5    9   0   0    3.35   3.71
--------------------------------------------------------------------------------
 BASBL Status: 		 *** Successful termination! ***
   Solution: F = 0.000, f = 0.000 at (x, y) = (0.000, 0.000)
================================================================================
```

## Usage
```
`BASBL` solver is still under active design and development and not feature complete
or ready for consumption by anyone other than software developers.
```
# Manual

`BASBL` solver's manual is described on [manual-wiki-page](https://github.com/basblsolver/manual/wiki).

Manual-wiki's **Table of Contents**:

* [Introduction](https://github.com/basblsolver/manual/wiki/Introduction)
* [Running BASBL](https://github.com/basblsolver/manual/wiki/Running-BASBL)
* [BASBL Output](https://github.com/basblsolver/manual/wiki/BASBL-Output)
* [BASBL Options](https://github.com/basblsolver/manual/wiki/BASBL-Options)

# Test Problems

Description of nonconvex bilevel test problems in `AMPL` format, compatible with `BASBL v0.1` is provided on [bilevel-test-problems](https://github.com/basblsolver/test-problems/wiki) wiki-page. This __wiki__ provides:
  * [Errata List](https://github.com/basblsolver/test-problems/wiki/Errata-List) for test problems taken from [(Mitsos and Barton, 2007)](https://www.researchgate.net/publication/228455291_A_test_set_for_bilevel_programs).
  * [Summary](https://github.com/basblsolver/test-problems/wiki/Summary) of the bilevel test problems.
  * The formulation of the problems and brief analysis of the feasible set and how the optimal solution can be obtained. 
  * Helpful illustrations of the objective functions and geometry of the problems (see example below for the model [mb_1_1_05](https://github.com/basblsolver/test-problems/wiki/mb_1_1_05)).

Outer problem   | Inner problem | 
--------------- | ---------------- |
<img src="https://github.com/basblsolver/test-problems/wiki/images/mb_1_1_05_outer.jpg" width="400">  | <img src="https://github.com/basblsolver/test-problems/wiki/images/mb_1_1_05_inner.jpg" width="400">

### Citation

If you use this library, please cite the following sources: 

* Remigijus Paulavicius et al.. (2016). A library of nonconvex bilevel test problems with the corresponding AMPL input files. Zenodo. [![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.44997.svg)](http://dx.doi.org/10.5281/zenodo.44997)

```
@misc{remigijus_paulavicius_2016_44997,
  author       = {Remigijus Paulavicius and
                  Polyxeni-M. Kleniati and
                  Claire S. Adjiman},
  title        = {{A library of nonconvex bilevel test problems with 
                   the corresponding AMPL input files}},
  month        = jan,
  year         = 2016,
  doi          = {10.5281/zenodo.44997},
  url          = {http://dx.doi.org/10.5281/zenodo.44997}
}
```
* Mitsos, A. and Barton, P.I. [A Test Set for Bilevel Programs](https://www.researchgate.net/publication/228455291_A_test_set_for_bilevel_programs) _Tech. Report_, Massachusetts Institute of Technology, 2007.

```
@misc{mitsos2007test,
  title     = {A test set for bilevel programs},
  author    = {Mitsos, Alexander and Barton, Paul I},
  year      = {2007},
  publisher = {Technical report, Massachusetts Institute of Technology}
}
```

### Important Notice

Kindly note, that this is a growing collection of nonconvex bilevel problems meant as a resource
for researchers in the field, including problem statement, analysis, solution(s) and input file(s). 
__We welcome contributions and corrections to this resource!__ 

# References

  * __Branch-and-Sandwich: a deterministic global optimization algorithm for optimistic bilevel programming problems. Part I: Theoretical development__

Journal Article published 10 Jan 2014 in Journal of Global Optimization volume 60 issue 3 on pages 425 to 458. http://dx.doi.org/10.1007/s10898-013-0121-7

**Authors**: Polyxeni-Margarita Kleniati, [Claire S. Adjiman](http://www.imperial.ac.uk/people/c.adjiman "Prof Claire S. Adjiman Homepage")

:page_facing_up: **BibTeX** entry:
```
@article{Kleniati2014:Theory,
  title     = {Branch-and-Sandwich: a deterministic global optimization algorithm for
               optimistic bilevel programming problems. Part I: Theoretical development},
  author    = {Kleniati, Polyxeni-Margarita and Adjiman, Claire S},
  journal   = {Journal of Global Optimization},
  volume    = {60},
  number    = {3},
  pages     = {425--458},
  year      = {2014},
  publisher = {Springer}
}
```

  * __Branch-and-Sandwich: a deterministic global optimization algorithm for optimistic bilevel programming problems. Part II: Convergence analysis and numerical results__

Journal Article published 10 Jan 2014 in Journal of Global Optimization volume 60 issue 3 on pages 459 to 481. http://dx.doi.org/10.1007/s10898-013-0120-8 

**Authors**: Polyxeni-M. Kleniati, [Claire S. Adjiman](http://www.imperial.ac.uk/people/c.adjiman "Prof Claire S. Adjiman Homepage")

:page_facing_up: **BibTeX** entry:
```
@article{Kleniati2014:NumericalResults,
  title     = {Branch-and-Sandwich: a deterministic global optimization algorithm for
               optimistic bilevel programming problems. Part II: Convergence analysis
               and numerical results},
  author    = {Kleniati, Polyxeni-M and Adjiman, Claire S},
  journal   = {Journal of Global Optimization},
  volume    = {60},
  number    = {3},
  pages     = {459--481},
  year      = {2014},
  publisher = {Springer}
}
```

  * __A generalization of the Branch-and-Sandwich algorithm: From continuous to mixed-integer nonlinear bilevel problems__

Journal Article published Jan 2015 in Computers & Chemical Engineering volume 72 on pages 373 to 386. http://dx.doi.org/10.1016/j.compchemeng.2014.06.004

**Authors**: Polyxeni-M. Kleniati, [Claire S. Adjiman](http://www.imperial.ac.uk/people/c.adjiman "Prof Claire S. Adjiman Homepage")

:page_facing_up: **BibTeX** entry:
```
@article{Kleniati2015:Generalization,
  title     = {A generalization of the Branch-and-Sandwich algorithm: From continuous
               to mixed-integer nonlinear bilevel problems},
  author    = {Kleniati, Polyxeni-M and Adjiman, Claire S},
  journal   = {Computers \& Chemical Engineering},
  volume    = {72},
  pages     = {373--386},
  year      = {2015},
  publisher = {Elsevier}
}
```

# Contact

| Support or Contact |                  |
| ------------------ | ---------------- | 
<img src="https://github.com/basblsolver/manual/raw/master/images/BASBL-logo-2nd-version.png" width="200"> | Having trouble with `BASBL` solver? Contact: @basblsolver |
