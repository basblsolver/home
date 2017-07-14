| Table of Contents |                  |
| ----------------- | ---------------- | 
<ul><li>[Motivation](#motivation)</li><li>[Why BASBL?](#why-basbl)<ul><li>[CLI](#command-line-interface)</li><li>[Usage](#usage)</li></ul></li><li>[Manual](#manual)</li><li>[Test Problems](#test-problems)<ul><li>[Citation](#citation)</li></ul></li><li>[References](#references)</li><li>[Contact](#contact)</li></ul> | <img src="https://github.com/basblsolver/manual/raw/master/images/BASBL-logo-landscape.png" width="570">

----

# Motivation
Solving _nonlinear_ bilevel problems to global optimality is a long-standing challenge in optimization theory. 
Special cases of bilevel problems, such as problems of _linear_ (_quadratic_) – _linear_ (_quadratic_) type, have been studied extensively and many algorithms have been proposed in the literature ([Dempe, 2002](http://dx.doi.org/10.1007/b101970); [Floudas and Gounaris, 2009](http://dx.doi.org/10.1007/s10898-008-9332-8)). However, the general nonconvex form is very challenging and only recently the first deterministic method to solve a general class of nonconvex problems to global optimality was proposed by ([Mitsos et al., 2008](http://dx.doi.org/10.1007/s10898-007-9260-z)). This class includes problems in which the outer and inner problems may contain nonconvex functions, provided that the inner problem does not contain equality constraints. Another algorithm, __Branch-and-Sandwich__, was proposed by [Kleniati and Adjiman (2014a)](http://dx.doi.org/10.1007/s10898-013-0121-7,[b)](http://dx.doi.org/10.1007/s10898-013-0120-8) to find the global solution of problems in which the outer and inner problems may contain nonconvex functions and include equality constraints, with the provision that a constraint qualification holds for the inner problem. This restriction was lifted in later work ([Kleniati and Adjiman, 2015](http://dx.doi.org/10.1016/j.compchemeng.2014.06.004)), in which the algorithm was also extended to include binary variables in the outer and inner problems.

# Why BASBL?

**B**ranch-**A**nd-**S**andwich **B**i**L**evel `BASBL` solver is a [MINOTAUR](https://wiki.mcs.anl.gov/minotaur/index.php/MINOTAUR) `C++` solver for nonlinear bilevel problems, based on the [MINOTAUR](https://wiki.mcs.anl.gov/minotaur/index.php/MINOTAUR) framework.
`BASBL` is based on the recent Branch-and-Sandwich algorithm (see [References](#references) section for the underlying theory), which is guaranteed to solve a broad class of bilevel problems to global optimality within epsilon convergence in finite time. Moreover, `BASBL` is enhanced with several new techniques: 

* reduction of overhead of the UB procedure;
* alternative ways to calculate tighter bounds;
* alternative choices for branching and node selection. 

Finally, `BASBL` solver's project is active therefore, more extensions and enhancements will be added soon!

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
