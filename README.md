# Ising Model Simulation

**Authors:**  Cecilie S. Rønnestad & Vaitian L. Marianayagam

Numerical simulation of the two-dimensional Ising model using the Metropolis Monte Carlo algorithm.
The project investigates thermodynamic properties and phase transitions by sampling energy and
magnetisation across a range of temperatures. The simulation is implemented in C++ with Python scripts for statistical analysis
and visualization of results.

## Repository structure

- `src/` – C++ implementation of the Ising model and Monte Carlo solver  
- `include/` – header files  
- `python/` – Python scripts for post-processing and visualization  
- `results/` – simulation output files (not tracked in Git)

## Build and run

**Build**
```bash
g++ src/ising_model.cpp src/utils.cpp -I include -fopenmp -o ising_model.exe
```

**Run**
```bash
./ising_model.exe <min temperature> <max temperature> <#temp-steps> <lattice length> <initial config [o/u]> <store samples [true/false]> <MCMC cycles> <burn-in cycles>
```

Outputs a file named "L\<lattice length\>_N\<MCMC_cycles\>_\<#temp_steps\>values.txt", containing temperature, mean epsilon, mean m, heat capacity per spin, magnetic susceptility per spin, epsilon squared and m squared for every temperature, in that order. If store samples is set to true and min temperature is equal to max temperature, it will also output a file containing MCMC-cycles done, epsilon, running mean epsilon, heat capacity until current cycle and magnetic susceptibility until current cycle, for every MCMC-cycle done, in that order.

## Analysis and visualization in Python

Python scripts for analysis are located in the `python/` directory:

### `compare.py`  
  Reads file containing MCMC-cycles done, epsilon, running mean epsilon, heat capacity until current cycle and magnetic susceptibility until current cycle, for every MCMC cycle done, and plots the wanted quantity and its analytical solution.

### `plot_burn_in.py`  
  Reads four files containing MCMC-cycles done, epsilon, running mean epsilon, heat capacity until current cycle and magnetic susceptibility until current cycle, for every MCMC-cycle done, and plots epsilon and mean epsilon for the four different files in the same plot.

### `distribution.py`  
  Plots histogram approximating pdf of epsilon of the $20 \times 20$ Ising-lattice.

### `plot_values.py`  
  Reads files containing temperature, mean epsilon, mean m, heat capacity per spin, magnetic susceptility per spin, epsilon squared and m squared for different temperatures, and plots one of the quantities against temperature. Also performs secound order fitting of the data, and plots the fit.


### `critical_point.py`  
  Estimates critical temperature at $L \rightarrow \infty$, and makes a plot of it.






