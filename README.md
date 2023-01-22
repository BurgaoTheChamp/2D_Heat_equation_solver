# Heat Transfer Simulation
This is a simulation of the heat transfer in a 2D plane domain using the finite difference method.

This code simulates the heat transfer in a 2D plane with a heat source for a given number of timesteps, using the specified boundary conditions. The simulation is based on the heat equation, which describes how heat flows through a material. The heat equation is a partial differential equation, which in 2D can be written as:

$$\frac{\partial T}{\partial t} = \alpha * (\frac{\partial^2 T}{\partial x^2} + \frac{\partial^2 T}{\partial y^2})$$

where T is the temperature, t is time, α is the thermal diffusivity, and x and y are the spatial coordinates. The code uses the finite difference method to approximate the solution of the heat equation at discrete time and space steps.

## Usage
The function `simulate_plate()` has several arguments:
- `length`: length of the plate;
- `height`: height of the plate;
- `timesteps`: Number of timesteps to simulate;
- `alpha`: Thermal diffusivity of the plate;
- `T0`: Initial temperature distribution in the plate (Time, lenght, height);
- `heat_sources`: Heat sources distribution in the plate [((position_x, position_y), power, size)];
- `boundary_conditions`: Boundary conditions on the plate [left, bottom, right, top];
- `dx`: Spatial step;
- `plotfinal`: Plots the final timestep in png format;
- `savegif`: Save all timesteps in gif format.

The function starts by calculating the timestep `dt` based on the spatial step `dx` and the thermal diffusivity `α`. It then initializes the temperature grid `T` with the initial temperature distribution `T0`. The boundaries of the plate are then set with the specified boundary conditions.

The code then enters a time loop, where for each timestep, it iterates over each point in the plate and calculates the new temperature using the finite difference approximation of the heat equation. If a heat source is found at the current point, the temperature is set to the temperature of the heat source. Otherwise, the temperature is calculated using the finite difference formula.

Finally, the function has the option to plot the final temperature distribution using matplotlib, and save it to a png file, or even save all the timesteps in a gif format, this can be useful for visualization purposes.

Example usage:
```python
length = 100
height = 100
timesteps = 1000
alpha = 0.01
T0 = np.zeros((lenght, height))
heat_sources = [((50, 50), 100, 10)]
boundary_conditions = [0, 0, 0, 0]
simulate_plate(lenght, height, timesteps, alpha, T0, heat_sources, boundary_conditions, plotfinal=True, savegif=False)
```

This will simulate a 100x100 domain, for 1000 timesteps, with thermal diffusivity of 0.01, with one heat source at position (50,50) with power 100 wats and size 10, with all the boundaries set to 0, and the final temperature distribution will be plotted and saved to a png file.