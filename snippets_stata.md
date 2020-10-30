## linreg
regress Y X X2

## seed
set seed 123

## save data
saveold filepath.dta, replace

## use dataset
use filepath.dta # then data browse or in script
insheet using "C:\stata\carsdata.dta"

## run script (do)
do filepath.do

## correlation
corr Y x1 x2

## covariance
cov Y X, covariance

## instrumental variables / two stage least squares tsls
ivregress 2sls Y (X = Z Q)

## graphing
twoway (scatter Y x1) (lfit Y x1) ///
	title(text without quotes)

any line in .do file gets printed out

* this is a comment which gets printed when running a script or runs a command?

## variables
gen colname=ln(X)

set varname number

set obs 5000

* regress Y x1 x2 x3

## other script things
clear all # clears vars
pause # waits a little
compress # compresses data types

## drop data
drop col1 col2

## replace
replace col2=val if col1>val2

## distributions dists
gen x1=rnornal(mean,std)  so must sqrt variance!

## panel data

## fixed effects
xtreg Y x1 x2, fe

## random effects
xtreg Y x1 x2, re

## discrete model non-linear
probit Y X1 X2

f(y, Xb) = 1/(1+exp(-Xb))                 if y = 1
         = exp(-Xb)/(1+exp(-Xb))          if y = 0

