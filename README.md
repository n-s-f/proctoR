# proctor
Lightweight & flexible test runner for R.

### Why proctor?

The language standard testing framework for R is [testthat](https://github.com/hadley/testthat). Testthat is a great framework for package developers, but it is restrictive in other contexts. Most relevantly, it requires all tests to be part of a package and is tightly coupled to the [devtools](https://github.com/devtools/hadley) package.

Proctor is designed data munging scripts or statistical analyses that there is no good reason to turn into packages but you still want to test. Proctor allows you to write tests immediately for any R script, with zero boilerplate.

### Installation
Start R with `sudo R`
```.R
# If you don't have devtools installed yet:
> install.packages('devtools')

# Then:
> library('devtools')
> devtools::install_github('n-s-f/proctor')
```

### Running Tests

Proctor tests are run from the command line.

```.bash
# Run all tests in current directory including subdirectories
$ proctor

# Run all tests in some_directory including subdirectories
$ proctor some_directory
```

Proctor finds any files that match `test\w*.R$`, and then runs any functions in those files that match `^test|test$`.

**NOTE**: There are a few sample tests in `tests/` which can be run as described above.

### Writing Tests
An proctor test might look like:
```.R
test_addition = function() {
  sum = 1 + 1
  proctor::assert_equal(sum, 3)
}
```

### TODO
- More informative and better formatted output
- Fixtures (setup, teardown, etc)
- Make use of testthat assertions
- Statistical tests
