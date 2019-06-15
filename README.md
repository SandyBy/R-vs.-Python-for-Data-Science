# R vs. Python for Data Science

<img src = https://raw.githubusercontent.com/matloff/R-vs.-Python-for-Data-Science/master/Images/Rlogo.png width = "100" />

<img src = https://raw.githubusercontent.com/matloff/R-vs.-Python-for-Data-Science/master/Images/python-logo.png width = "300" />

### Norm Matloff, Prof. of Computer Science, UC Davis; [my bio](http://heather.cs.ucdavis.edu/matloff.html)


Hello!  This Web page is aimed at shedding some light on the perennial
R-vs.-Python debates in the Data Science community.  As a professional
computer scientist and statistician, I hope to shed some useful light on
the topic.  I have potential bias &mdash; I've written 4 R-related books,
and currently serve as Editor-in-Chief of the *R Journal* &mdash; but I hope
this analysis will be considered fair and helpful.

## Elegance

*Clear win for Python.* 

This is subjective, of course, but having
written (and taught) in many different programming languages, I really
appreciate Python's greatly reduced use of parentheses and braces:

``` python
if x > y: 
   z = 5
   w = 8
```

vs.

``` r
if (x > y)
{ 
   z = 5
   w = 8
}
```

Python is sleek!

## Learning curve

*Huge win for R.*  

This is of particular interest to me, as an educator.  I've taught a
number of subjects -- math, stat, CS and even English As a Second
Language -- and have given intense thought to the learning process for
many, many years.

To even get started in Data Science with Python, one must learn a lot of
material not in base Python, e.g., NumPy, Pandas and matplotlib. These
libraries require a fair amount of computer systems sophistication.

By contrast, matrix types and basic graphics are built-in
to base R.  The novice can be doing simple data analyses within minutes.

Python libraries can be tricky to configure, even for the systems-savvy,
while most R packages run right out of the box.

## Available libraries for Data Science

*Slight edge to R.*

[CRAN](https://cran.r-project.org/) has over 14,000
packages. [PyPI](https://pypi.org/) has over 183,000,
but it seems thin on Data Science.

For example, I once needed code to do fast calculation of
nearest-neighbors of a given data point.  (NOT code using that to do
classification.) I was able to immediately find not one but two packages
to do this.  By contrast, just now I tried to find nearest-neighbor code
for Python and at least with my cursory search in PyPi, came up
empty-handed; there was just one implementation that described itself as
simple and straightforward, nothing fast.

The following searches in PyPI turned up nothing: log-linear model;
Poisson regression; instrumental variables; spatial
data; familywise error rate; etc.

This is not to say no Python libraries exist for these things; I am
simply saying that they are not easily found in PyPI, whereas it is easy
to find them in CRAN.

The fact that R has a canonical package structure is a big advantage.

## Machine learning

*Slight edge to Python here*. 

The R-vs.-Python debate is largely a statistics-vs.-CS debate, and since
most research in neural networks has come from CS, available software
for NNs is mostly in Python.  RStudio has done some excellent work in
developing a Keras implementation, but so far R is limited in this
realm.

On the other hand, random forest research has been mainly pursued by the
stat community, and in this realm I'd submit that R has the superior
software.  R also has excellent packages for gradient boosting.

I give the edge to Python here because for many people, machine learning
means NNs.

## Statistical correctness

*Big win for R*.  

In my book, *the Art of R Programming*, I made the
statement, "R is written *by* statisticians, *for* statisticians," which
I'm pleased to see pop up here and there on occasion.  It's important!

To be blunt, I find the machine learning people, who
mostly advocate Python, often have a poor understanding of, and in
some cases even a disdain for, the statistical issues in ML.  I was
shocked recently, for instance, to see one of the most prominent ML
people, state in his otherwise outstanding book that standardizing the
data to mean-0, variance-1 means one is assuming the data are Gaussian
&mdash; absolutely false and misleading.

## Parallel computation

*Let's call it a tie.*  

Neither the base version of R nor Python have good support for multicore
computation.  Threads in Python are nice for I/O, but parallel
computation using them is impossible, due to the infamous Global
Interpreter Lock.  Python's multiprocessing package is not a good
workaround, nor is R's 'parallel' package.  External libraries
supporting cluster computation are OK in both languages.

Currently Python has better interfaces to GPUs.

## C/C++ interface

*Slight win for R.*

Though there are tools like swig etc. for interfacing Python to C/C++,
as far is I know there is nothing remotely as powerful as R's Rcpp for
this at present.  The Pybind11 package is being developed.

In addition, R's new ALTREP idea has great potential for enhancing
performance and usability.

On the other hand, the Cython and PyPy variants of Python can in some
cases obviate the need for explicit C/C++ interface in the first place;
indeed some would say Cython IS a C/C++ interface.

## Object orientation, metaprogramming

*Slight win for R*.

For instance, though functions are objects in both languages, R takes
that more seriously than does Python.  Whenever I work in Python, I'm
annoyed by the fact that I cannot print a function to the terminal,
which I do a lot in R.

Python has just one OOP paradigm.  In R, you have your choice of several
(S3, S4, R6 etc.), though some may debate whether this is a good thing.

Given R's magic metaprogramming features (code that produces code),
computer scientists ought to be drooling over R.  But most CS people are
unaware of it.

## Language unity

*Horrible loss for R*.

Python is currently undergoing a transition from version 2.7 to 3.x.
This will cause some disruption, but nothing too elaborate.

By contrast, R is rapidly devolving into two mutually unintelligible
dialects, ordinary R and the Tidyverse.  I, as a seasoned R programmer,
cannot read Tidy code, as it calls numerous Tidyverse functions that I
don't know.  Conversely, as one person in the Twitter discussion of this
document noted (approvingly), "One can code in the Tidyverse while
knowing very little R."

Note that, in using the term "Tidyverse," I am not including
pre-existing projects by Hadley Wickham, e.g. ggplot2 (which I use a
lot) and dplyr.  Instead, I am referring to things such as tibbles and
pipes.  I am especially concerned about the plethora of 
extra functions Tidyverse advocates burden students with learning, on
top of rudimentary base R.  These functions are unnecssary, as most can
be done simply in base R.

Though advocates claim it works well in teaching beginning programmers,
there has been no study of this claim, and I think the perceived success
is psychological, a Bandwagon Effect.  On the contrary, I believe it is
quite the opposite, i.e. using the Tidyverse makes things more difficult
for learners without prior programming background.  As noted, the
students are being asked to learn a much larger volume of material,
which is clearly bad pedagogy.  See also ["The Tidyverse
Curse"](https://www.r-bloggers.com/the-tidyverse-curse), in which the
author says *inter alia* that he uses "only" 60 Tidyverse functions --
60!  

Again, I am certainly not saying one should only use base R; on the
contrary, see my point above that CRAN is a major advantage of R.
But the Tidyverse should be considered advanced R, not for beginners,
just as is the case for most complex CRAN packages.

The Tidyverse is a vigorous promotional effort by a commercial entity
that has come to dominate the R world, RStudio.  I know and admire the
people at RStudio, *but a commercial entity should not have such undue
influence on an open-source project.*  

For instance, consider the lightning-fast **data.table** package. Rather
than welcoming it as a hugely valuable contribution to R, RStudio has
treated it as a competitor, downplaying it and promoting their own
product, dplyr.  This is simply not healthy for an open-source language.

In addition, all this is causing tension between some leaders in the two
camps.  All this does not augur well for the future of the language.

## Linked data structures

*Win for Python.*

Not a big issue in Data Science, but it does come up in some contexts.

Classical computer science data structures, e.g. binary trees, are easy
to implement in Python.  It is not part of base R, but can be done in
various ways, e.g. the datastructures package, which wraps the
widely-used Boost C++ library.

## Online help

*Big win for R.*

To begin with, R's basic **help()** function is much more informative
than Python's.  It's nicely supplemented by **example()**.  And most
important, the custom of writing vignettes in R packages makes R a
hands-down winner in this aspect.

## R/Python interoperability

RStudio is to be commended for developing the reticulate package, to
serve as a bridge between Python and R.  It's an outstanding effort, and
works well for pure computation.  But as far as I can tell, it does not
solve the knotty problems that arise in Python, e.g. virtual
environments and the like.

At present, I do not recommend writing mixed Python/R code.

## Learning R and Python

I have a [quick tutorial on R for
non-programmers](http:github.com/matloff/fasteR), an evolving project. I
also have a book, *the Art of R Programming*, NSP, 2011.

I have a [tutorial on
Python](http://heather.cs.ucdavis.edu/FastLanePython.pdf), for
those with a strong programming background.

## Thanks

This document has benefited from various reader comments, notably from
Dirk Eddelbuettel, as well as Paul Hewson, Bob Muenchen and Inaki Ucar.
