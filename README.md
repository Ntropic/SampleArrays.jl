# SampleArrays.jl

[![Build Status](https://github.com/Ntropic/SampleArrays.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/Ntropic/SampleArrays.jl/actions/workflows/CI.yml?query=branch%3Amain)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**SampleArrays.jl** provides a data structure, `Samples`, for statistical data storage and analysis in Julia, with built-in methods to compute key statistics such as the mean, standard deviation, variance, upper- and lower standarddeviations.

### Key Features:
- **Built-in Statistical Methods**:
  - `mean`, `std`, `var`, `min`, `max`: Compute the mean, standard deviation, variance, minimum and maximum values.
  - `lower_std`, `upper_std`: Calculate standard deviations for values below or above the mean.
  - `val`: Access the vectors of sample values 
- **Create Arrays of Samples**:
  - Arrays of `Samples` inherit the properties of `Samples`.
    - Append data on a single element using `A[1,1] += value` or `A[1,1] = [value1, value2, ...]`.
    - Manipulate slices of the array at once using `A[:, 1] += value` or `A[:, 1] += [value1, value2, ...]`.
    - Rescale a slice using `A[:, 1] *= c` or `A[:, 1] /= c`.
    - Append arrays & slices using `A[:,1] + B[:,1]` or `A[:, 1] += B[:,1]`.
## Installation

To install the package, run:
```julia
using Pkg
Pkg.add("SampleArrays")
``` 

## Usage
``` julia
using SampleArrays 
A = SampleArray(2, 2; type = Float64)
A[1, 1] += 1.0
A[:, 1] .+= 2.0
A[1, :] .+= 3.0
println(A[1, 1].vals) # prints [1.0, 2.0, 3.0]
println(A[1, 1].mean) # prints 2.0
println(A[:, 1].std) # prints [0.816496580927726, NaN]
```
This functionality allows us to eaily store samples for every entry of an array, without having to worry about the storage of those samples. 

## Author 
Michael Schilling