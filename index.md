---
marp: true
theme: default
_class: lead
title: 17th OpenFOAM Workshop
paginate: true
# backgroundImage: url('https://marp.app/assets/hero-background.svg')
math: katex
---

# Particle aggregation and breakage using `multiphaseEulerFoam`
A CFD-PBM approach
Kasper Bilde

---

# Introduction
![bg vertical right:33% 60%](visuals/AAU_UK_CIRCLE_blue_rgb.svg)
![bg 80%](visuals/alfa-laval-logo.svg)
Kasper Bilde
Industrial PhD Student
Aalborg University and Alfa Laval

**PhD Scope**: Agglomeration and breakage of micron-sized particles in turbulent flows for highly accelerated sedimentation

---
<!-- NOTE: NOT COMPLETE! -->
# Background
![bg right:66% 60%](visuals/mesh.svg)
Study the particle size distribution through pipe bends

---
# Governing equations
Euler-Euler approach using the population balance equations to track the particle size distribution

Mass- and momentum equations
$$
\frac{\partial}{\partial t} \left(\alpha_\varphi \rho_\varphi \right) +
\nabla \cdot \left( \alpha_\varphi \rho_\varphi \boldsymbol{u}_\varphi\right) =0
$$

$$
\frac{\partial}{\partial t}\left(\alpha_\varphi \rho_\varphi \boldsymbol{u}_\varphi\right)
+ \nabla \cdot \left( \alpha_\varphi \rho_\varphi \boldsymbol{u}_\varphi\boldsymbol{u}_\varphi\right)
-\nabla \tau_\varphi = -\alpha_\varphi \nabla p +  \alpha_\varphi\rho_\varphi\boldsymbol{g} + \boldsymbol{M}_\varphi + \boldsymbol{S}_\varphi
$$

where $\boldsymbol{M}_\varphi$ is the momentum exchange at the interfaces and $\boldsymbol{S}_\varphi$ is the source term.

---
# Governing equations
<!-- CONSIDER ADDING REFERENCES -->
Momentum exchange at the interfaces is the sum of external force
$$
\boldsymbol{M}_\varphi = \sum_{\varphi=0,\varphi\neq\psi}^{N}\left( \underbrace{F_{D,\varphi,\psi}}_{\text{Wen-Yu drag}^1}+\underbrace{F_{L,\varphi,\psi}}_{\text{Saffman-Mei lift}}+\underbrace{F_{TD\varphi,\psi}}_{\text{Turbulent dispersion}}+\underbrace{F_{VM,\varphi,\psi}}_{\text{Virtual mass}}\right)
$$

*Saffman-Mei lift force* [*committed*](https://github.com/OpenFOAM/OpenFOAM-dev/commit/b4bcb29d6a8d8cc0b7576934ece1f0fafaddfccc) *to `OpenFOAM-dev`*

---
# Population balance equation
Tracking the particle number density function using class method implementation of Lehnigk et al. (2021).

$$
\frac{\partial}{\partial t} n_v+\nabla\cdot\left(\boldsymbol{u}_\mathrm{p}n_v \right) = S_v
$$
where the source term, $S_v$ accounts for the discontinuous changes from aggregation and breakage.

---
# Aggregation kernel
The aggregation kernel for solid particles by Adachi et al. (1994) is [implemented](https://github.com/OpenFOAM/OpenFOAM-dev/commit/b4bcb29d6a8d8cc0b7576934ece1f0fafaddfccc) into `OpenFOAM-dev`.
$$
a_{d,d^\prime} = \frac{4}{3}\sqrt{\frac{3\pi}{10}}\sqrt{\frac{\varepsilon}{\nu}}\left(d+d^\prime\right)^3
$$

where $d$ and $d^\prime$ are the diameters of two colliding particles.

---
# Breakage kernel
The breakage kernel for solid particles by Kusters (1991) is [implemented](https://github.com/OpenFOAM/OpenFOAM-dev/commit/b4bcb29d6a8d8cc0b7576934ece1f0fafaddfccc) into `OpenFOAM-dev`.

$$
b_{v^\prime} = \sqrt{\frac{4}{15\pi}}\sqrt{\frac{\varepsilon}{\nu}}\exp\left(-\frac{\varepsilon_\mathrm{cr}}{\varepsilon}\right)
$$
Herein the critical energy dissipation rate required to cause a break up is given by
$$
\varepsilon_\mathrm{cr} =\frac{B}{r_\mathrm{c}}\,,
$$
where $r_\mathrm{c}$ is the collision radius of a particle.


---
# Case setup


---

# Source files
The presented material is available as a tutorial of the OpenFOAM Foundation.

Particle agglomeration, breakage and lift force for `multiphaseEulerFoam`
https://github.com/OpenFOAM/OpenFOAM-dev/commit/b4bcb29d6a8d8cc0b7576934ece1f0fafaddfccc

The tutorial of the pipe bend:
```
$FOAM_TUTORIALS/multiphase/multiphaseEulerFoam/RAS/pipeBend
```

---
# References
Adachi et al
Kusters
Lehnigk 2021