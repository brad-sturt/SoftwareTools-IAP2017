# Optimization, Julia, and JuMP

This class is an introduction to mathematical optimization, along with the programming language Julia and the JuMP library.

Julia is a "high-level, high-performance dynamic programming language for technical computing", and JuMP is a library that allows us to easily formulate optimization problems and solve them using a variety of solvers.

## Preassignment - Install Julia and IJulia

The first step is to install a recent version of Julia. The current version is 0.5.0\. Binaries of Julia for all platforms are available [here](http://julialang.org/downloads/).

IJulia is the Julia version of IPython/Jupyter, that provides a nice notebook interface to run julia code, together with text and visualization.

Please follow the instructions [here](https://github.com/stevengj/julia-mit#installing-julia-and-ijulia) to install Julia and set up IJulia.

## Preassignment - Install the Gurobi and JuMP in Julia

Installing packages in Julia is easy with the Julia package manager. Just open Julia and enter the following command:

```jl
julia> Pkg.add("JuMP")
```
to install JuMP. We will also need a linear programming (LP) and integer programming (IP) solver. We can use Cbc, an open-source offering:

```jl
julia> Pkg.add("Cbc")
```

## Preassignment - Solving a simple LP

Let's try a simple LP! Enter the following JuMP code in Julia.

```jl
using JuMP, Cbc

m = Model(solver=CbcSolver())
@variable(m, 0 <= x <= 2 )
@variable(m, 0 <= y <= 30 )

@objective(m, Max, 5x + 3*y )
@constraint(m, 1x + 5y <= 3.0 )

print(m)

status = solve(m)

println("Objective value: ", getobjectivevalue(m))
println("x = ", getvalue(x))
println("y = ", getvalue(y))
```

## Questions?

Email huchette@mit.edu.
