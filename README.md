# NBTesting

[![Build Status](https://travis-ci.org/cstjean/NBTesting.jl.svg?branch=master)](https://travis-ci.org/cstjean/NBTesting.jl)

[![Coverage Status](https://coveralls.io/repos/cstjean/NBTesting.jl/badge.svg?branch=master&service=github)](https://coveralls.io/github/cstjean/NBTesting.jl?branch=master)

[![codecov.io](http://codecov.io/github/cstjean/NBTesting.jl/coverage.svg?branch=master)](http://codecov.io/github/cstjean/NBTesting.jl?branch=master)

NBTesting is a simple utility for writing tests in your
[IJulia](https://github.com/JuliaLang/IJulia.jl) notebooks, alongside other plots and
computations. How it works:

1. [Add tests to your notebook](test/Water_Analysis.ipynb) using `Base.Test`, or your
favorite testing framework.
2. Use `NBTesting.nbtest("Water_Analysis.ipynb")` to run the notebook's code and
tests. It will create and execute a file called
[`NBTest_Water_Analysis.jl`](test/NBTest_Water_Analysis.jl).
3. (Optional) Track this `.jl` file with git if all tests are successful.

`nbtest` will mostly run the notebook code as is, but it provides [a few ways to
control which code gets executed when](test/Water_Analysis.ipynb), and a `verbose=...`
option for printing the headers (on by default - see `?nbtest` for details). The code is
wrapped inside a module called `NBTest_[Notebook name]`, to isolate it from the current
environment, and to make it easier to inspect the state of variables if a test fails.

NBTesting borrows code from [NBInclude.jl](https://github.com/stevengj/NBInclude.jl), by
Steven G. Johnson.