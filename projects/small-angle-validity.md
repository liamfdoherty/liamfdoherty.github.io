@def title = "Liam Doherty | Small Angle Approximation with UQ"

# Just How Valid _is_ the Small Angle Approximation? An Uncertainty Quantification Approach

\toc

## Introduction
A common joke among scientists is exaggerating the validity of the so-called "small angle approximation" used frequently in physics. The simplest example of an application of this concept is in approximating the differential equation of motion for a pendulum:
$$
\ddot{\theta} + \frac{g}{l}\sin(\theta) = 0.
$$
We are motivated to make an approximation to this equation because it is not solvable (in the sense that an analytical solution does not exist in terms of elementary functions). The approximation that people make is to approximate the $\sin(\theta)$ term. This is done through the commonly known Taylor expansion of $\sin(\theta)$:
$$
\sin(\theta) = \theta - \frac{\theta^{3}}{3!} + \frac{\theta^{5}}{5!} - \frac{\theta^{7}}{7!} + \dots.
$$
When the angle $\theta$ is sufficiently small, the high-order terms (i.e., terms involving high powers of $\theta$) are seen as negligible, and they can be dropped from the representation of $\sin(\theta)$ altogether with minimal impact to the dynamics. From the approximation $\sin(\theta) \approx \theta$, we obtain the simplification to our equation of motion:
$$
\ddot{\theta} + \frac{g}{l}\theta = 0,
$$
which may be recognized as the equation for simple harmonic motion, and has a nice analytical solution, a feature which the original equation of motion does not have.

The question we ask is in the validity of this approximation. Of course, we said when we used the Taylor series that the higher order terms are only negligible when $\theta$ is small, so we can imagine that when $\theta$  _isn't_ small, we will incur a noticeable error in our solution if we use this approximation. This article will investigate the question of validity through the lens of uncertainty quantification (UQ), obtaining bounds on the error of our models based on uncertainty in the initial displacement of the pendulum.

## Simulating Pendulums and Simple Harmonic Motion
Before we can begin to assess the validity of the approximation to the full differential equation, we must first be able to simulate both the full differential equation and its simplified version. We use the Julia programming language and its SciML ecosystem (specifically, the DifferentialEquations.jl package) to accomplish this task. First, we need to be able to simulate the complete dynamical system for the pendulum. This is easily done in Julia, with the following code:
```
 # Define dynamical system for full pendulum equation
function pendulum!(du, u, p, t)
    g, l = p
    θ, ω = u
    du[1] = ω
    du[2] = -(g/l)*sin(θ)
end

# Set up initial condition, integration time, and problem parameters
u₀ = [θ₀, ω₀]
tspan = (0., t_max)
p = [g, l]

# Solve the problem
prob = ODEProblem(pendulum!, u₀, tspan, p)
sol = solve(prob)
```
Here, we can give whatever parameters $\theta_{0}$, $\omega_{0}$, $g$ and $l$, as well as the integration time $t_{\text{max}}$ we wish. $\theta_{0}$ and $\omega_{0}$ are the initial conditions of the system; they represent the initial (angular) displacement and velocity respectively. On the other hand, $g$ and $l$ represent acceleration due to gravity and the length of the pendulum. We can use this to generate plots of the solution for given initial conditions and system parameters.

As an example, consider the conditions $\theta_{0} = 1$, $\omega_{0} = 0$, $g = 9.81$, and $l = 1$.

## Adding Randomness

## The UQ Framework

## Applying the Framework

## Conclusion