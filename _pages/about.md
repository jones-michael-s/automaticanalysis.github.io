---
title: About
permalink: /about/
layout: splash
---

## What is aa, and why use it? ##
Automatic analysis (aa) is a pipeline specification tool for neuroimaging written in Matlab. It provides scriptable access to many popular imaging packages, as well as a variety of third party SPM toolboxes. The primary features include:

*Automatic*. Automatic detection of functional, structural, and fieldmap data. Automatic data transfer between processing stages.

*Flexible control*. Essential analysis settings taking sensible defaults to assist the new user. Experienced users can change a range of settings. Advanced users can modify almost any processing behaviour or add new capabilities.

*Restartable*. If aa halts processing for any reason, it will continue at the stage where it left off when restarted.

*Parallel processing*. If multiple cores or a computing cluster is available, aa jobs can easily be distributed across them.

*Analysis paper trail*. Unlike a click-through analysis, aa records all parameters used, and allows easy recreation of a dataset from the raw data at a later date.

*Multi-modal*. aa supports EEG & MEG as well as fMRI analysis.

*Tool Agnostic*. aa supports analysis tools equally. Use functionality implemented by SPM, FSL, Freesurfer, or any of the other supported software using the same scripting syntax. Operations from multiple packages can be combined in a single script.

*Extendable*. Matlab programmers can write new modules and incorporate them into the processing stream.

*Open source*. Code is maintained in a Github repository. Fixes and new features are easily added.


See the [aa wiki](https://github.com/automaticanalysis/automaticanalysis/wiki) for more information.

## How the story started... ##
automatic analysis software was originally developed by Dr Rhodri Cusack for supporting research at the MRC Cognition and Brain Science Unit. It is made available to the academic community in the hope that it may prove useful.

## References and citation ##
For any papers that report data analyzed with aa, please include the [GitHub repo URL](https://github.com/automaticanalysis/automaticanalysis) and cite the aa paper:

Cusack R, Vicente-Grabovetsky A, Mitchell DJ, Wild CJ, Auer T, Linke AC, Peelle JE (2015) Automatic analysis (aa): Efficient neuroimaging workflows and parallel processing using Matlab and XML. Frontiers in Neuroinformatics 8:90. DOI:[10.3389/fninf.2014.00090](http://doi.org/10.3389/fninf.2014.00090)
{:.reference}

