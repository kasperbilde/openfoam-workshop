# Presentation
[**Click here**](https://kasperbilde.github.io/openfoam-workshop/) to start the presentation

This my presentation for the [17th OpenFOAM Workshok](https://openfoamworkshop.org/) at Cambridge University.

The topic of the presentation is on aggregation and breakage of solid particles through a turbulent 90° pipe bend.

The workshop presentation was held July 13th, 2022.

## About
The presentation is made using the [Marp](marp.app) Markdown Presentaiton Ecosystem.

## Source files
The presented 90° pipe bend are comitted to `OpenFOAM-dev` as a tutorial and can be found at
```
$FOAM_TUTORIALS/multiphase/multiphaseEulerFoam/RAS/pipeBend
```
The applied Saffman-Mei lift force, aggregation kernel and breakage kernels are also <a href="https://github.com/OpenFOAM/OpenFOAM-dev/commit/b4bcb29d6a8d8cc0b7576934ece1f0fafaddfccc" target="_blank">comitted</a> to `OpenFOAM-dev`.

Saffmann-Mei lift force:
```
$FOAM_SOLVERS/multiphase/multiphaseEulerFoam/interfacialModels/liftModels/SaffmanMei
```

Aggregation kernel:
```
$FOAM_SOLVERS/multiphase/multiphaseEulerFoam/phaseSystems/populationBalanceModel/coalescenceModels/AdachiStuartFokkink
```

Breakage kernel:
```
$FOAM_SOLVERS/multiphase/multiphaseEulerFoam/phaseSystems/populationBalanceModel/breakupModels/Kusters
```

## Socials
<a
    href="https://www.linkedin.com/in/kasper-gram-bilde/" target="_blank">
    <p>
        <img src="visuals/linkedin.svg" alt="LinkedIn" height="30"/>
    </p>
</a>
<a href="https://www.github.com/kasperbilde/" target="_blank"><img src="visuals/github_kasperbilde.svg" alt="LinkedIn" height="30"/></a>