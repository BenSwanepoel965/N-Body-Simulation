# 🌌 N-Body Simulation

A physics-based **N-Body Simulation** written in Python.  
This project numerically integrates Newton’s law of gravitation for multiple interacting bodies and visualizes their motion in 2D space.  

It is designed to be:
- **Educational** – easy to read and understand, suitable for students and hobbyists.
- **Modular** – clean separation of physics, visualization, and configuration.
- **Extensible** – supports adding new forces, integrators, and visualizers.

---

## 🚀 Features

✅ Simulates gravitational interactions between any number of bodies (up to ~50 in Python).  
✅ Modular physics engine with interchangeable integrators (Euler, Verlet, RK4).  
✅ Configurable through `config.py` or `data/initial_conditions.json`.  
✅ Optional visualization using `matplotlib`.  
✅ Extensible architecture – add new forces, logging, or UI controls with minimal refactoring.

---

## 📂 Project Structure


---

## 🧠 Module Responsibilities

### **main.py**
- Serves as the **entry point** to the simulation.
- Loads configuration and initial conditions.
- Initializes bodies and passes them to the simulation engine.
- Optionally launches visualization.

### **config.py**
- Central location for simulation parameters:
  - `G`: gravitational constant.
  - `DT`: time step size.
  - `N_STEPS`: number of iterations.
- Prevents "magic numbers" from being scattered across the codebase.

### **simulation/**
- **body.py** – Defines the `Body` class, which encapsulates mass, position, velocity, and force vectors.
- **forces.py** – Responsible for force computation:
  - Pairwise gravitational force calculations.
  - Future extensions: drag, collisions, external fields.
- **integrator.py** – Implements numerical solvers:
  - Euler (simple, fast, low accuracy).
  - Verlet (better energy conservation, good for orbital problems).
  - RK4 (high precision, slower).
- **simulation.py** – The simulation loop:
  - Calls `forces.py` to update forces.
  - Calls `integrator.py` to advance positions and velocities.
  - Can optionally return data for logging or visualization.

### **visualization/**
- **renderer.py** – Handles the actual drawing:
  - Uses matplotlib (or another backend) to show the system evolving in time.
  - Can plot trajectories or animate the system.
- **ui.py** – Placeholder for interactivity:
  - Could allow pausing, resuming, or changing parameters on the fly.

### **utils/**
- **logger.py** – For tracking simulation diagnostics:
  - Kinetic energy, potential energy, total energy.
  - Exports CSV files for later analysis.

### **data/**
- **initial_conditions.json** – Defines initial body configuration:
  ```json
  [
    {"mass": 5e10, "position": [0, 0], "velocity": [0, 0]},
    {"mass": 5e10, "position": [100, 0], "velocity": [0, 5]}
  ]
