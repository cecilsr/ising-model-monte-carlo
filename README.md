# Ising Model Simulation

**Authors:**  Cecilie S. Rønnestad & Vaitian L. Marianayagam

Numerical simulation of the two-dimensional Ising model using the Metropolis Monte Carlo algorithm.
The project investigates thermodynamic properties and phase transitions by sampling energy and
magnetization across a range of temperatures. The simulation is implemented in C++ with Python scripts for statistical analysis
and visualization of results.

## Repository structure

- `src/` – C++ implementation of the Ising model and Monte Carlo solver  
- `include/` – header files  
- `python/` – Python scripts for analysis and visualization  

## Build and run

**Build**
```bash
g++ src/ising_model.cpp src/utils.cpp -I include -fopenmp -o ising_model.exe
```

**Run**
```bash
./ising_model.exe <min temperature> <max temperature> <#temp-steps> <lattice length> <initial config [o/u]> <store samples [true/false]> <MCMC cycles> <burn-in cycles>
```

The simulation outputs a file named `L<lattice_length>_N<MCMC_cycles>_<N_temp_steps>values.txt`,
containing the following quantities for each temperature, in order:
temperature, mean epsilon, mean magnetization, heat capacity per spin,
magnetic susceptibility per spin, epsilon squared and m squared.

If `store_samples` is set to `true` and `min temperature` is equal to `max temperature`,
an additional file is generated containing per-cycle values for epsilon,
running mean epsilon, heat capacity and magnetic susceptibility.


## Analysis and visualization in Python

Python scripts for analysis are located in the `python/` directory:

### `compare.py`  
  Reads file containing MCMC-cycles done, epsilon, running mean epsilon, heat capacity until current cycle and magnetic susceptibility until current cycle, for every MCMC cycle done, and plots the wanted quantity and its analytical solution.

### `plot_burn_in.py`  
  Reads four files containing MCMC-cycles done, epsilon, running mean epsilon, heat capacity until current cycle and magnetic susceptibility until current cycle, for every MCMC-cycle done, and plots epsilon and mean epsilon for the four different files in the same plot.

### `distribution.py`  
  Plots histogram approximating probability density function of epsilon of the $20 \times 20$ Ising-lattice.

### `plot_values.py`  
  Reads files containing temperature, mean epsilon, mean m, heat capacity per spin, magnetic susceptibility per spin, epsilon squared and m squared for different temperatures, and plots one of the quantities against temperature. Also performs second-order fitting of the data, and plots the fit.


### `critical_point.py`  
  Estimates critical temperature at $L \rightarrow \infty$, and makes a plot of it.






