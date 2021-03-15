---
title: Getting started
permalink: /gettingstarted/
sidebar:
  title: Getting started
  nav: gettingstarted
---
This page is under construction. The [**old wiki**](https://github.com/automaticanalysis/automaticanalysis/wiki) is still available until further notice.

# Get ready #

## 1. Registration ##

{% raw %}
<iframe src="https://docs.google.com/forms/d/e/1FAIpQLScubzIQsKp472C2RsnKTZx76rTv0Y51_gAd63FUhfhWnDMczg/viewform?embedded=true" width="640" height="1600" frameborder="0" marginheight="0" marginwidth="0">Loading…</iframe>
{% endraw %}

## 2. Requirements ##

### Minimum requirements ###
Operating System: Linux or MacOX (Windows is not supported. Sorry!)

Softwares:
  - [MATLAB](https://uk.mathworks.com/products/matlab.html) - It has been tested with version r2013a and later
  - [SPM](https://www.fil.ion.ucl.ac.uk/spm) - It has been tested with versions SPM12 r7487 or later
Optional:
  - [GraphViz](http://www.graphviz.org) for visual representation of the pipeline

### Further supported software and toolboxes ###
  - [FMRIB Software Library](http://fsl.fmrib.ox.ac.uk/fsl/fslwiki)
  - [FreeSurfer](https://surfer.nmr.mgh.harvard.edu/fswiki)
  - [EEGLab](https://github.com/sccn/eeglab)
  - [FieldTrip](https://www.fieldtriptoolbox.org)
  - [Face Masking](https://nrg.wustl.edu/software/face-masking)
  - [Group ICA Of fMRI Toolbox](http://mialab.mrn.org/software/gift/index.html)
  - [BrainWavelet Toolbox](http://www.brainwavelet.org)
  - [Motion FingerPrint](https://www.medizin.uni-tuebingen.de/kinder/en/research/neuroimaging/software)
  - [CoSMoMVPA](http://www.cosmomvpa.org)
  - [The Decoding Toolbox](https://sites.google.com/site/tdtdecodingtoolbox)

## 3. Download and installation ##

There are two ways to install the aa scripts: One using Git, the other simply downloading the files.

If you are new to Git, there is a bit of a learning curve, but it is probably worth it. Using Git will make it easier to update code, especially small improvements and bug fixes. Because aa is still under active development these can happen a lot! There is some introductory help on github and also a git book, both of which are good resources.

Once you have installed Git, you can get aa by cloning the repository on your local drive:

`$ git clone https://github.com/automaticanalysis/automaticanalysis.git`

This will give you an automaticanalysis directory containing the aa code in the current folder.

As an alternative to git, you can simply download a [zip archive of the current code](https://github.com/automaticanalysis/automaticanalysis/archive/master.zip). Navigate to the main automatic analysis page (https://github.com/automaticanalysis/automaticanalysis) and click "download ZIP".

## 4. Parameterset ##

Automatic Analysis must to be configured before its first use. Rather than adding tools, such as EEGLAB or FieldTrip to the path, you must specify them in a parameterset, which serves as a description of the computational environment. You can see example parametersets in the [repository](https://github.com/automaticanalysis/automaticanalysis/blob/master/aa_parametersets) and locally in the `<aa path>/aa_parametersets` folder. The idea is that every site (or even user and project) can specify its own parameterset, which contains how the data and the software tools including the job scheduler are organised locally.

### 4.1 Inheritance ###

A parameterset can inherit the parameters using [XML Inclusion](http://www.w3.org/TR/xinclude) from another one while overriding a few of them. In this way, you do not have to (re)define every paremeters but only those which are different from those in the other paremeterset. For example, you can create a site/user/study-specific parameterset based on [aap_parameters_defaults.xml](https://github.com/automaticanalysis/automaticanalysis/blob/master/aa_parametersets/aap_parameters_defaults.xml), which is the root parameterset describing every paremeters.

The parameterset specific for the Univeristy of Surrey ([aap_parameters_defaults_UoS.xml](https://github.com/automaticanalysis/automaticanalysis/blob/master/aa_parametersets/aap_parameters_defaults_UoS.xml)) can be taken as an example:
```xml
<?xml version="1.0" encoding="utf-8"?>
<aap xmlns:xi="http://www.w3.org/2001/XInclude">
  <xi:include href="aap_parameters_defaults.xml" parse="xml"/>
  <local>
    <directory_conventions>
    …
    </directory_conventions>
    <options>
    …
    </options>
  </local>
</aap>
```  

Here, most of the settings are imported from aap_parameters_defaults.xml and the site-specific settings are redefined in the <local/> section.

It is also possible, of course, to generate a parameterset based on [aap_parameters_defaults_UoS.xml](https://github.com/automaticanalysis/automaticanalysis/blob/master/aa_parametersets/aap_parameters_defaults_UoS.xml) (or any other derived parameterset) if you want to keep customisations. For that, you only have to replace "aap_parameters_defaults.xml" with "aap_parameters_defaults_UoS.xml" in the `xi:include` tag. 

### 4.2 Configuration ###

#### 4.2.1 Mandatory ####

Here we provide a list of the most important settings to be configured:
```xml
    <directory_conventions>
      <rawdatadir> <!-- Colon-separated list of directories to find raw MRI data. You MUST have an entry ending with "aa_demo" for the examples -->
      <rawmeegdatadir> <!-- Colon-separated list of directories to find raw M/EEG data. You MUST have an entry ending with "aa_demo" for the examples -->
      <subjectoutputformat> <!-- `sprintf` formatting string to get subject directory as stored in rawdatadir -->
      <meegsubjectoutputformat> <!-- `sprintf` formatting string to get subject directory as stored in rawmeegdatadir -->
      <seriesoutputformat> <!-- `sprintf` formatting string to get series directory as stored in subject directory -->
      <protocol_structural> <!-- For automatic identification of structural/anatomical data, you must sepcify the name of the structural/anatomical protocol as stored in the DICOM header -->
      <dicomfilter> <!-- Directory listing filter to find DICOM files -->
      <toolbox> <!-- Settings for SPM. N.B.: You should not modify SPM version in your user script but rather in your parameterset. -->
        <name>spm</name> 
        <dir> <!-- path to SPM -->
      </toolbox>
```

#### 4.2.2 Optional ####

There are also other settings which may be required depending on your use case:
  - Distortion correction using fieldmaps
```xml
    <directory_conventions>
      <protocol_fieldmap> <!-- For automatic identification of fieldmap, you must sepcify the name of the fieldmap protocol as stored in the DICOM header -->
```
  - Multichannel segmentation using T2-weighted images
```xml
    <directory_conventions>
      <protocol_t2> <!-- For automatic identification of T2-weighted images, you must sepcify the name of the T2-weighted protocol as stored in the DICOM header -->
```
  - Further software
Some software are integrated using specific interface found in `<aa path>/aa_tools/toolboxes` folder.
```xml
    <directory_conventions>
      <toolbox> <!-- Settings for SPM. N.B.: You should not modify SPM version in your user script but rather in your parameterset. -->
        <name>eeglab</name> 
        <dir> <!-- path to EEGLAB -->
        <extraparameters>
          <requiredPlugins> <!-- colon-separated list of plugins to be used -->

      <toolbox> <!-- Settings for SPM. N.B.: You should not modify SPM version in your user script but rather in your parameterset. -->
        <name>fieldtrip</name> 
        <dir> <!-- path to FieldTrip -->

      <toolbox> <!-- Settings for SPM. N.B.: You should not modify SPM version in your user script but rather in your parameterset. -->
        <name>hcpwb</name> 
        <dir> <!-- path to Human Connectome Project Workbench (used by M/EEG source reconstruction based on cortical sheet) -->
        <extraparameters>
          <templateDir> <!-- Path to the folder created as spefcified in [FieldTrip path]/bin/ft_postfreesurferscript.sh -->

      <toolbox> <!-- Settings for SPM. N.B.: You should not modify SPM version in your user script but rather in your parameterset. -->
        <name>mvpalight</name> 
        <dir> <!-- path to SPM -->
```
