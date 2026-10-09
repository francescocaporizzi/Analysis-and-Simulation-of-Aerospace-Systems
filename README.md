# Analysis-and-Simulation-of-Aerospace-Systems
Reports of MATLAB &amp; Simulink implementations for aerospace systems modeling, dynamic analysis, and control: Liquid Sloshing (Pendulums), Inverted Pendulum stabilization (PD/LQR), and Aircraft Longitudinal Dynamics

### 1. Liquid Sloshing Modeling (`01-slosh-mass-pendulum`)
* **Objective:** Model the lateral fluid sloshing dynamics in a partially filled cylindrical tank using an equivalent mechanical multi-pendulum model (based on Dodge's formulation).
* **Key Topics & Methods:**
  * Derivation of nonlinear Equations of Motion (EOM) via the Lagrangian approach.
  * State-space formulation and modal reduction (analysis of up to 10 equivalent pendulums).
  * Model order reduction and convergence analysis (determining $n=5$ as the optimal trade-off).
  * System response to impulse and step accelerations (analytical solutions vs. `ode45` vs. MATLAB built-ins).
  * Frequency-response comparison against a frozen-mass rigid fluid model.
  * Implementation in Simulink using State-Space blocks.

---

### 2. Inverted Pendulum Dynamics & Control (`02-inverted-pendulum`)
* **Objective:** Dynamic modeling of a cart-pendulum system, followed by stabilization of the unstable upright inverted pendulum configuration.
* **Key Topics & Methods:**
  * Lagrangian derivation of the coupled nonlinear equations of motion.
  * Open-loop nonlinear vs. linearized responses under varying force impulses (1 N, 5 N, 25 N).
  * Transfer function derivation, pole-zero mapping, and Root Locus analysis.
  * **PD Controller Design:** Specification of damping ratio ($\zeta$) and natural frequency ($\omega_n$) to satisfy transient requirements (overshoot $< 20\%$, peak time $< 1\text{ s}$).
  * **Full-State Feedback (LQR):** Extension from partial-state feedback to optimal full-state feedback via Linear-Quadratic Regulator (LQR) and pole-placement (`place`), evaluating performance vs. control effort ($L_2$ norm).
  * Implementation in Simulink using both direct block-integrator architectures and interpreted MATLAB functions (`MATLAB Function` blocks).

---

### 3. Business Jet Longitudinal Flight Dynamics (`03-longitudinal-flight-dynamics`)
* **Objective:** Characterization of the longitudinal flight dynamics, trim analysis, and stability assessment of a business jet.
* **Key Topics & Methods:**
  * Numerical trim computation for straight-and-level flight at sea level ($V_{\text{trim}} = 120\text{ kts}$) using nonlinear optimization (`fsolve`).
  * Derivation of the linearized state-space system ($\Delta u, \Delta w, \Delta q, \Delta\theta, \Delta h$) from stability and control aerodynamic derivatives.
  * Eigenvalue analysis and identification of fundamental dynamic modes:
    * **Short-Period mode:** High frequency, well-damped ($\omega_n \approx 1.66\text{ rad/s}, \zeta \approx 0.43$).
    * **Phugoid mode:** Low frequency, lightly damped ($\omega_n \approx 0.19\text{ rad/s}, \zeta \approx 0.12$).
  * Frequency response analysis (Bode diagrams) from elevator deflection $\delta_e$ to longitudinal states.
  * Time-domain nonlinear vs. linear response to a $-1^\circ$ elevator pulse, comparing ode45 solvers with equivalent Simulink models.

---

## 🛠️ Software Requirements & Toolboxes

* **MATLAB** (tested on R2024a or newer)
* **Simulink**
* **Control System Toolbox** (for `ss`, `step`, `impulse`, `rlocus`, `bode`, `lqr`)
* **Optimization Toolbox** (for `fsolve`)
* **Aerospace Toolbox** (for `atmosisa`)

---
