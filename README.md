# Gravitational Search Algorithm

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](www.google.com)

This is the official repo of GSA( Gravitational Search Algorithm) python package. Gravitational Search Algorithm is a nature inspired algorithm for optimisation problem. The package offers a modular way to use GSA in your project.

  - Includes Custom Fitness Function support
  - Includes Custom Initial Population Support

## How to install
```sh
$ pip install GSA
```
## Requirements

* Python - Python standard library package
* Numpy - A python package for mathematical computation with arrays

## Sample Codes
###  Importing

```sh
$ import numpy as np
$ from GSA import Search
```
### Implementing Gravitational Search

```sh
$ params={'init_pop':2,
        'sol_dim':[2,2],
        'seed':0,
        'no_of_iter':10,
        'G0':1,
        'rj':1,
        'ri':1,
        'epsilon':0.001,
        'alpha':5,
        'type':'min',
        'Data':[nrr,Label],
        'custom':myfitness,
        'custom_solution':[[0,0,0,0],[1,1,1,1]]
        'sol_range':(-3,3)
        }
$ print(Search.init(params))
```
### Parameters
#### init_pop (required)
The initial Population of random solutions. Its value>=2
#### sol_dim (required)
It is an list of two integers k and d where k*d is dimension of the solution particle.
#### seed (optional)
The seed value for various random generators. Default value random.
#### no_of_iters (required)
The number of iteration for which the GSA algorithm will run to find the optimised solution
#### G0 (required)
The Initial Gravitational Constant G0.
#### rj,ri (optional)
The random coefficients of field and velocity equations. Default value 1. 
#### epsilon (optional)
Used to control the maximum force between two particle at same position. Its the additional factor added to denominator to prevent division by zero in case of same location of two points. Default value 0.001.
#### alpha (optional)
It is the decay rate of Gravitational Constant G with goes from G0 to 0 in all n iterations. Default Value 10.
#### type (requied)
The type of problem ie., either minimisation of maximisation. Use 'min' and 'max' strings.
#### Data (required)
1. If using prebuit fitness function (ie.,not  defining custom parameter) that can be used for clustering. The Data is a list where
   * Data[0] : Coordinates of All points in d dimension
   * Data[1] : Labels of All points of Data[0]
2. If using custom fitness function whatever you provide as value to 'Data' key will be passed as an argument for custom fitness function along with Solution Particle.
#### custom (optional)
It is used to define custom fitness function having following prototype. Pass the function name as the value.
```sh
$ def myfunc(Data,Solution) # Solution will have dimension k*d
```
Example Function:
```sh
$ def myfitness(Data,Solution):
    Points = Data[0]
    label = Data[1]
    fitness = 0
    for i in range(len(Points)):
        cluster_no = label[i]
        centroid = Solution[cluster_no]
        fitness += distance(Points[i], centroid) ** 2
    return fitness

```
#### custom_solution (optional)
Used to provide Custom initial population which otherwise will be generated randomly. The size should be (init_pop,k*d)
#### sol_range (required)
A tuple of minimum and maximum limit of values a solution can have. It should be inclusive range of all data points.

### Development

Want to contribute? Great!
Fork this repo, make your changes and send a pull request. 
Or send an email to
Developer's Email :deepanshu4929@gmail.com
Feel Free to raise issues.
### Todos

 - Adding more modularity
 - Increasing support for more purposes.

License
----

MIT


**Free Software, Hell Yeah!**
