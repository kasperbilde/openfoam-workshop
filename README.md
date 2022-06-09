# Presentation
[Click here](https://kasperbilde.github.io/openfoam-workshop/) to start the presentation

This my presentation for the 17th OpenFOAM Workshop at Cambridge University.

The topic of the presentation is on aggregation and breakage of solid particles through a turbulent 90° pipe bend.

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