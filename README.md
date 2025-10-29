# Fermi–Pasta–Ulam–Tsingou (FPUT) Numerical Study — MATLAB  

This project implements and analyzes numerical methods for the **Fermi–Pasta–Ulam–Tsingou (FPUT)** chain, a nonlinear Hamiltonian lattice that exhibits non-ergodic dynamics and delayed thermalization.  
The goal is to evaluate numerical integrators that preserve the qualitative properties of the system: stability, energy conservation, and recurrence behaviour.

---

## Physical Background  

- The **FPUT chain** models a one-dimensional system of \( N \) particles connected by weakly nonlinear springs.  
- The model was first introduced by Fermi, Pasta, Ulam, and Tsingou (1953) to test whether nonlinearity induces thermalization, as expected from the ergodic hypothesis.  
- Contrary to expectations, energy initially placed in one normal mode periodically returned to its original configuration instead of spreading uniformly — a clear violation of ergodicity.  
- The discovery made the FPUT chain an **important toy model** for studying the limits of ergodicity, nonlinear resonances, and the transition from order to chaos in Hamiltonian systems.  
- It later became foundational in the development of **soliton theory** and the understanding of **near-integrable** dynamics.  
- In this work, we reproduce these phenomena numerically and study how the choice of integration scheme affects the conservation of energy and long-time stability.  
- A particular focus is given to **symplectic methods**, i.e. integrators that preserve the geometric structure of Hamiltonian systems and maintain nearly constant total energy over long simulations.

---

## Implemented Numerical Methods  

All integrators are implemented in MATLAB and tested on a fixed-length FPUT chain with fixed-end boundary conditions.

| Method | Type | Symplectic | Order | Notes |
|--------|------|-------------|--------|-------|
| Explicit Euler | Explicit | No | 1 | Unstable, accumulates energy error |
| Runge–Kutta 4 | Explicit | No | 4 | Accurate short-term, poor long-term stability |
| Leap-Frog | Explicit | Yes | 2 | Stable, bounded energy error |
| Ruth 3rd-Order | Partitioned RK | Yes | 3 | Good long-time energy conservation |
| Nystrom 3rd-Order | Symplectic | Yes | 3 | Most stable and accurate for long runs |

---

## Numerical Results  

- **Energy Conservation:** Symplectic schemes (Leap-Frog, Ruth, Nystrom) conserve energy over long integration times (\( T_{\max} = 10^4 \)), while non-symplectic methods show energy drift.  
- **Stability Threshold:** Stable integration requires \( \omega_{\max} \cdot h \lesssim 2 \).  
- **Empirical Convergence Order:**  
  - Euler ≈ 1  
  - Leap-Frog ≈ 2  
  - Ruth / Nystrom ≈ 3  
- **Recurrence and Equipartition:**
  - At low energy density \( \varepsilon < \varepsilon_c \), mode energy recurs quasi-periodically.  
  - Above \( \varepsilon_c \), energy equipartitions, matching the expected chaotic regime.

---

## Summary
This project provides a quantitative numerical study of the FPUT chain using explicit and symplectic integrators.
It verifies the classical recurrence phenomenon, examines stability and convergence, and evaluates energy conservation across methods.
The analysis highlights the importance of symplectic integration for reproducing physically consistent dynamics in Hamiltonian systems, where preserving energy and structure is essential to observe genuine long-term behaviour.  

