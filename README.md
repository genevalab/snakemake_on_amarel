# snakemake_on_amarel
Workshop on using Snakemake on Amarel

Wednesday, Oct 22 & Oct 29 12–2 PM

This hands-on workshop will introduce Snakemake, a workflow management system that enables reliable, scalable, and reproducible scientific workflows. We’ll work through a Software Carpentry tutorial to build a Snakemake workflow to perform a basic bioinformatics analysis. Later episodes will focus on workflow design, debugging, and configuration.

Upon completion of the workshop students will have:
1. Gained a familiarity with the use and benefits of workflow management systems generally and Snakemake specifically
2. Completed a worked example using Snakemake to manage and perform basic bioinformatics analyses
3. Learned about extensions and options in Snakemake that could apply to their coding/scripting
   
This workshop is suitable for STEM trainees who 1) have a familiarity working with Bash or other command line shell environments and 2) have an active Amarel account prior to the start of the workshop. No familiarity with python, R, or bioinformatics is needed to participate. In this workshop, we will collectively work through a Software Carpentry tutorial in which we will each build a Snakemake workflow to perform some basic bioinformatics analysis.

Details from the tutorial:
"Snakemake enables the writing of reliable, scalable and reproducible scientific workflows as a series of chained rules. Simple workflows to replace shell scripts can be written in a few lines of code, while for more complex cases there is support for conda integration, software containers, cluster execution, cloud execution, etc. You can also add Python and R code directly into your workflow.
This lesson introduces the core concepts of Snakemake in the context of a typical analysis task, aligning short cDNA reads to a reference transcriptome. Later episodes focus on practical questions of workflow design, debugging and configuration."

Aside from the initial setup modifications listed below, we will be following this tutorial from [Software Carpentries](https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/).


# Getting started
The tutorial was written assuming a linux workstation, therefore we have to make a few modifications in order to get started. This replaces the "Summary and Setup" instructions on the Carpentries tutorial. 

## First we need to connect to amarel and set up conda
Since everyone who signed up for this workshop already has an amarel account we only need to get connected via ssh. If you use a mac open terminal if on a PC use whichever tool you typically use to start an ssh session (putty, openssh, etc). Now connect using the command/address below, replacing [YOUR_NETID] with your actual netID.

```ssh [YOUR_NETID]@amarelc@hpc.rutgers.edu```

Once logged in, confirm you have an active conda install in your home directory by typing ```which conda``` if that command returns a path to a conda binary like ```/projects/community/anaconda/2023.10/bd387/base/bin/conda```, then you have conda installed. If you don't you will need to set up conda before proceeding.

I have laid out the steps to installing conda in your home directory [here](https://github.com/lizardroom/conda_on_amarel). Go to that page, follow all the steps and return to this page to continue.

## Now that we have conda set up, we need to create an environment for the workshop
I'm simply transposing the instructions from Software Carpentry here, for convenience. Feel free to switch over to the that page at any time.


