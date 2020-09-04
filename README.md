
## R Computation Package
To build the package click on Build->Clean and Rebuild.   This is also available Build tab typically to right pane in R Studio. 

The R directory contains the files with functions in the library.   For example, R/CalcPosteriorProbsBinom.R contains the function that is called from the Shiny app.  

You may find the following functions in the BASS package helpful when developing the Calculation package

AddFunctionToPkg( strFunctionName, strFunctionDescription = "", strPkgDir = "" ) - Add a new function named strFunctionName to a package.  This function creates a file names R/strFunctionName.R
and adds a test function in the file tests/testthat/test-strFunctionName.R to be used with the testthat package.


For a function to be available to the user that installs the package it must have a #' @export in the line above the function name like the following

```{r,  eval=FALSE}
#' @export
ExampleFunction <- function()
{
    return( -1) 
}
```



For an example of how to create a test using testthat see the tests/testthat/test-CalcPosteriorProbsBinom.R file.   

If you create a file with a function the best practice is to create a test for the function.  If the file name is FileXX.R then there should be a file in tests/testhat/test-FileXX.R that provides the tests for the function.  To facilitate the creation of this file and the test you can execute the following command in the working directory set to the project directory (the default when you open the R Studio project file).

```{r,  eval=FALSE}
#' @export
usethis::use_test( "FileXX")
```

The command above will create the tests/testhat/test-FileXX.R file with an example test in it.

To execute all tests in the project, execute the following code
```{r,  eval=FALSE}
#' @export
devtools::test()
```

The results should be similar to the following

```{r,  eval=FALSE}
Testing _CALCULATION_PACKAGE_NAME_
√ |  OK F W S | Context
√ |   2       | Test - CalcPosteriorProbsBinom.R

== Results =====================================================================
OK:       2
Failed:   0
Warnings: 0
Skipped:  0

:)
```

