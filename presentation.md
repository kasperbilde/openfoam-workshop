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
# <! --fit--> Background
![bg right:66% 60%](visuals/mesh.svg)
Study the particle size distribution through pipe bends

---
# Governing equations
Euler-Euler approach using the population balance equations to track the particle size distribution

Mass- and momentum equations
$$\frac{\partial}{\partial t} \left(\alpha_\varphi \rho_\varphi \right) +
\nabla \cdot \left( \alpha_\varphi \rho_\varphi \boldsymbol{u}_\varphi\right) =0$$
$$\frac{\partial}{\partial t}\left(\alpha_\varphi \rho_\varphi \boldsymbol{u}_\varphi\right)
+ \nabla \cdot \left( \alpha_\varphi \rho_\varphi \boldsymbol{u}_\varphi\boldsymbol{u}_\varphi\right)
-\nabla \tau_\varphi = -\alpha_\varphi \nabla p +  \alpha_\varphi\rho_\varphi\boldsymbol{g} + \boldsymbol{M}_\varphi + \boldsymbol{S}_\varphi$$

where $\boldsymbol{M}_\varphi$ is the momentum exchange at the interfaces and $\boldsymbol{S}_\varphi$ is the source term.

---
# Governing equations
<!-- CONSIDER ADDING REFERENCES -->
Momentum exchange at the interfaces is the sum of external force
$$\boldsymbol{M}_\varphi = \sum_{\varphi=0,\varphi\neq\psi}^{N}\left( \underbrace{F_{D,\varphi,\psi}}_{\text{Wen-Yu drag}^1}+\underbrace{F_{L,\varphi,\psi}}_{\text{Saffman-Mei lift}}+\underbrace{F_{TD\varphi,\psi}}_{\text{Turbulent dispersion}}+\underbrace{F_{VM,\varphi,\psi}}_{\text{Virtual mass}}\right)$$

---
# Population balance equation
Tracking the particle number density function using class method of

---

# Source files
The presented material is available as a tutorial of the OpenFOAM Foundation.

Particle agglomeration, breakage and lift force for `multiphaseEulerFoam`
https://github.com/OpenFOAM/OpenFOAM-dev/commit/b4bcb29d6a8d8cc0b7576934ece1f0fafaddfccc

The tutorial of the pipe bend:
```
$FOAM_TUTORIALS/multiphase/multiphaseEulerFoam/RAS/pipeBend
```
