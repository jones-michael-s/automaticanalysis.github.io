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
<iframe src="https://docs.google.com/forms/d/e/1FAIpQLScubzIQsKp472C2RsnKTZx76rTv0Y51_gAd63FUhfhWnDMczg/viewform?embedded=true" width="640" height="1206" frameborder="0" marginheight="0" marginwidth="0">Loading…</iframe>
{% endraw %}

## 2. Download and installation ##

There are two ways to install the aa scripts: One using Git, the other simply downloading the files.

If you are new to Git, there is a bit of a learning curve, but it is probably worth it. Using Git will make it easier to update code, especially small improvements and bug fixes. Because aa is still under active development these can happen a lot! There is some introductory help on github and also a git book, both of which are good resources.

Once you have installed Git, you can get aa by cloning the repository on your local drive:

`$ git clone https://github.com/automaticanalysis/automaticanalysis.git`

This will give you an automaticanalysis directory containing the aa code in the current folder.

As an alternative to git, you can simply download a [zip archive of the current code](https://github.com/automaticanalysis/automaticanalysis/archive/master.zip). Navigate to the main automatic analysis page (https://github.com/automaticanalysis/automaticanalysis) and click "download ZIP".

## 3. Parameterset ##

Automatic Analysis MUST to be configured before its first use. Rather than adding tools, such as EEGLAB or FieldTrip to the path, you MUST specify them in a parameterset, which serves as a description of the computational environment. You can see example parametersets in the [repository](https://github.com/automaticanalysis/automaticanalysis/blob/master/aa_parametersets) and locally in the <aa path>/aa_parametersets folder. The idea is that every site (or even user and project) can specify its own parameterset, which contains how the data and the software tools including the job scheduler are organised locally.