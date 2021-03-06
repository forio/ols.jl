ols.jl
======

Julia type for multiple (multivariate) regression using OLS. Performs least squared regression on linear equations of multiple independent variables

Author: Adam Savitzky

Ported from the Python implemented by Vincent Nijs
http://www.scipy.org/Cookbook/OLS?action=AttachFile&do=get&target=ols.0.2.py

OLS can be used on the following types of equations:
```julia
y = a1 * x1 + a2 * x2 + ... + an * xn
Y = AX + E
```

# Input
```julia
y = dependent variable
y_varnm = string with the variable label for y
x = independent variables, note that a constant is added by default
x_varnm = list of variable labels for the independent variables
```

# Usage
```julia
## Instantiate a new ols type
reg = ols(y, x, "y", ["x1", "x2", "x3"])
println("Coefficientss: $(reg.b)")
println("R-Squared: $(reg.R2)")
println("F-Statistic: $(reg.F)")
summary(reg)
```

All available output:
 * b::Array{Float, 1} - Coefficients that minimize squared error
 * nobs::Int - Number of observations
 * ncoef::Int - Number of coefficients
 * df_e::Int - Degrees of freedom in error
 * df_r::Int - Degrees of freedom in result
 * er::Array - Error vector
 * sse::Float - Sum of the squared errors
 * se::Array{Float, 1} - Standard Error (deviation)
 * t::Array{Float} - T-statistic vector (one for each xi)
 * #p::Array - T-statistic p-value (not implemented)
 * R2::Float - R-Squared
 * R2adj::Float - Adjusted R-Squared (based on how many dof)
 * F::Float - F-statistic (one for each xi)
 * #Fpv::Float - F-statistic p-value (not implemented)