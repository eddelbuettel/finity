# finity

Package for testing whether a given moment of the distribution of a given sample is finite or not.

# Details

For heavy-tailed distributions with tail exponent a, only moments of order < a are finite. The tail
index and heavy- tailedness are is notoriously difficult to ascertain. But the finiteness of moments
(including fractional moments) can be tested directly. This package does that following the test
suggested by Trapani (2016).

# Building and installing

```
R CMD build finity
R CMD INSTALL finity_0.1.tar.gz
```
In the install command, ```finity_0.1.tar.gz``` should be replaced with the correct filename of the archive (in particular with the correct version number).

The shell commands can alternatively be run from the R interpreter as ```system("R CMD build finity")``` etc.

# Building the pdf manual

```
Rscript -e 'setwd("finity");roxygen2::roxygenize();roxygen2::roxygenize()'
R CMD Rd2pdf finity
```

Alternatively, ```roxygen2::roxygenize()``` can be executed twice from the R interpreter before building the pdf with ```R CMD Rd2pdf finity```.

It is important to execute ```roxygenize()``` twice since the help files for the individual functions are only created the second time.

It may be necessary to remove automatically generated tags
```
\packageDESCRIPTION{finity}
\packageIndices{finity}
```
from the ```description{}``` section of the help file ```man/finity-package.Rd``` that are introducted by ```roxygenize()```.

# How to perform the finite moment test

```
library(stabledist)
library(finity)

# Generate test data
rvs <- rstable(50000000, 1.9, 0.5, 1, 0, pm = 0)

# Perform the test
result <- finite_moment_test(rvs, 2)
```
