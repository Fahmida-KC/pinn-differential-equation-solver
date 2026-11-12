# Physics-Informed Neural Network for Solving Differential Equations

## Project Overview

This project implements a Physics-Informed Neural Network (PINN) using DeepXDE and TensorFlow to solve a second-order ordinary differential equation (ODE).

The neural network incorporates the governing differential equation and Dirichlet boundary conditions into its training process. Its predicted solution is then compared with the analytical solution to evaluate accuracy.

## Governing Differential Equation

The project considers the following second-order differential equation:

```text
d²y/dx² + π² sin(πx) = 0
```

**Computational domain:**

```text
-1 ≤ x ≤ 1
```

**Boundary conditions:**

```text
y(-1) = 0
y(1) = 0
```

**Analytical solution:**

```text
y(x) = sin(πx)
```

## Methodology

### 1. Physics-Based Problem Formulation

- Defined the governing differential equation using DeepXDE's automatic differentiation functionality.
- Formulated Dirichlet boundary conditions at both ends of the computational domain.
- Defined the analytical solution to assess the accuracy of the PINN predictions.

### 2. Computational Domain and Training Data

- Established a one-dimensional interval from -1 to 1.
- Generated 16 domain training points.
- Specified 2 boundary training points.
- Used 100 test points for solution evaluation.

### 3. Neural Network Architecture

Implemented a fully connected feed-forward neural network with the following architecture:

| Parameter                | Configuration  |
| ------------------------ | -------------- |
| Input neurons            | 1              |
| Hidden layers            | 3              |
| Neurons per hidden layer | 50             |
| Output neurons           | 1              |
| Activation function      | Tanh           |
| Weight initializer       | Glorot Uniform |

### 4. Model Training

Trained the PINN using the Adam optimizer with the following configuration:

| Parameter           | Value                        |
| ------------------- | ---------------------------- |
| Framework           | DeepXDE                      |
| Backend             | TensorFlow 1.x compatibility |
| Optimizer           | Adam                         |
| Learning rate       | 0.001                        |
| Training iterations | 1,000                        |
| Evaluation metric   | Relative L2 error            |

The training objective included two loss components:

- Governing PDE residual loss
- Boundary condition loss

## Results

The trained PINN approximated the analytical solution with a low relative L2 error.

| Evaluation Metric |      Result |
| ----------------- | ----------: |
| Training loss     | 2.48 × 10⁻⁴ |
| Testing loss      | 2.38 × 10⁻⁴ |
| Relative L2 error | 3.31 × 10⁻⁴ |

The predicted solution was compared against the analytical solution through a visualization over the computational domain.

## Technologies Used

- Python
- DeepXDE
- TensorFlow
- NumPy
- Matplotlib

## Key Learning Outcomes

- Formulation of physics-informed neural networks for differential equation solving.
- Implementation of PDE residuals using automatic differentiation.
- Incorporation of boundary conditions into neural network training.
- Development and optimization of fully connected neural network architectures.
- Validation of numerical predictions against analytical solutions.

## Future Improvements

- Investigate the effects of network architecture and training parameters on solution accuracy.
- Explore different optimizers and adaptive training strategies.
- Extend the framework to more complex differential equations.
- Apply PINNs to physical problems such as heat transfer and fluid dynamics.
